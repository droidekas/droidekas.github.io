---
title: Effective Recycling with a recycler view
layout: post
section-type: post
category: android
tags: [ 'android','recycler-view','performance' ]
---
The recycler view is one hell of an API(do pardon the language).The entire RecyclerView and its components belong to one class.While this seems quite anti-thesis of the decoupled nature of the recycler view. This is by far one of the most exposed APIS with such widespread use[^1]. 

This post will just cover performance tracing and logical improvement methods.I'll try covering the API intricacies in another post.

#Using timers
It would not make any sense doing performace improvements if you were unable to gauge it quantitatively.The time taken to render a screen (in this case the time take to bind/create ViewHolders) is a good enough measure.I would also like to explain why does this matter.


Assuming you want to achieve a frame rate of 30 fps.This means that every frame needs to be rendered in 16 ms.When you consider flings,the duration reduces exponentially.The bind methods runs for all items, and not only the destination items.When you are dealing with heterogenous lists,on-the-fly toggling of UI elements along with `findViewById()` being a *really* *really* 
*really* [expensive process][1]. You would really be better off timing your methods



#Remove unnecessary things
The `bindViewHolder(ViewHolder vh,int position)` method is called on every scroll/fling.It does not make sense to use `findViewById()` in a bind method. Similary,you should avoid toggling View visibilities too,especially toggling from visible to gone.
While making views invisible causes a redraw of that particular view,by making a view gone,you would be forcing a redraw of all the views in that viewgroup and up(or down or whatever) the viewtree too.

Avoid setting  anonymous click listeners, i.e. 
    
    button.setOnClickListener(v -> performClick());

Java is GCed language,the use and throw click listeners serve no other purpose other than ensuring frequent Garbage Collection which in turn slows the ui.
Instead use singleton click listeners ,or ideally set up the click listeners in  `onCreateViewHolder()`. You can always pass the click context(this does not mean View context,but click context).

Instead of toggling view visibilities, you should use multiple ViewTypes instead.If you are insistent on using the same item layouts,you would see noticeable performance improvements even when you treat both the types of views as 2 different viewtypes.


#Reuse as much as possible
Say you have multiple recyclerviews which use the same viewtypes.You can have multiple recyclerviews share the same RecycledViewPool for scrap views (beat that list view!) by `setRecycledViewPool(RecyclerView.RecycledViewPool pool)`.
Sharing the same RecyclerViewPool would reduce object creations. This in turn reduces the number of times GC runs...well, you should get the picture by now.


`setHasFixedSize(boolean b)`
This tells the recycler view that recalculation of layouts are not necessary.Layout passes to calculate view positions although heavilit optimized,can be quite process heavy.I really do not need to explain the fight between optimized view hierachies.

 
#pre calculate things.
If you process text before displaying,do those in the object in itself. Often display html text like `Html.fromHtml()` ,instead of performing this function in the bind,try doing it in the POJO in-itself. I normally maintain nullable variables in the pojo.

These alone helped me shave off precious time(10 ms) from each pass.RAM usage was reduced by 10 mb too.










[^1]:If you dig through AOSP,you will realize that a lot of the classes follow a brilliant structure.
[1]:http://daniel-codes.blogspot.in/2013/11/is-findviewbyid-slow.html
[2]:https://github.com/JakeWharton/salvage