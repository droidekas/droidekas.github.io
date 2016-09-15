---
title: Code Predictability
layout: post
section-type: post
category: tech
tags: ["tech","writing","code","java"]
---
When I write code,I like to go through tiny iterations.Each class that I end
up writing gets rewritten approximately twice or thrice during the first initial
writing phase in itself.I realise this could be odd for few people but to me its
natural.

Code is elegant,you want to convey the message as easily as possible.But you
should also keep in mind the black box nature of functions/code snippets.
The most atomic place where you can excercise SRP is at the functions.This
removes the 'magic' from code(atleast for the developer it does).If I see
myself copying a segment of code to add it somewhere else I end up making
it a function.[^1]It might be used in only 2 places,but what I've learned
from working in a fast paced release focused environment is changes are
expected to made quickly and with maximum predictability.

Contradictory to this,I choose to specify as less arguments as  possible.
Try to derive arguments from parameters that already exist
Ex.


{% highlight java %}

public boolean iNeedViewAndContext(View v,Context c){
  //Do stuff
}

{% endhighlight %}


can be written as

{% highlight java %}

public boolean iNeedViewAndContext(View v){
    Context c = v.getContext();
    //Do stuff
}

{% endhighlight %}

Infact a much better way would be.

{% highlight java %}

public boolean iNeedViewAndContext(View v,Context c){
  //Do stuff
}

public boolean iNeedOnlyView(View v){
    return iNeedViewAndContext(v,v.getContext)
}

{% endhighlight %}

While these seem quite trivial changes.They can have a cascading effect.
Another important change I made to my code-writing techniques , you need to stop
worrying about names.The amount of type spent in naming
variables/functions/classes is really not justified.This increases exponentially
while making Constants/libraries. Nevertheless well named parameters can often
replace a lot of documentation. So instead of figuring out the shortest smart
name for things,figure out the name which describes its functionality. I really
dont think there is anything wrong in naming a function.

{% highlight java %}

convertScreenCartesianCoordinatesToImageBoundaryCoordinates(float x,float y)

{% endhighlight %}

You end up thanking the past you when you get back to this code after a few
months. It makes debugging a whole lot easier.

Code abstraction is hard,but the benifits outweigh any form of time spent on it.



[^1]:IDEs also give you that right click on code and refactor into a function to make it easier for those lazy folks
