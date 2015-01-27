---
layout: post
title: Why Jekyll+gh-pages+jekyllized-generator.
categories: ["siteBlocks"]
tags: []
published: True

---

So as i mentioned before,the plan was to use a system which provided an ease of blogging(writing).The main reason being that I have the habit of digressing.If I were to manually develop this platform.I'd spend so much time developing it,that I would not be able to(read: *lose the interest to*) write about it.

<!--end-excerpt-->

Before I start,you should know this.

<a name="dontknowlist"></a>

| What I do know | What i pretend to know | What I ***do not*** know |
|:---------------|:----------------------:|-------------------------:|
| Java   		 | Git   				  | Ruby   				     |
| Android Programming| Javascript   	  | Jekyll   				 |
|**Googling**|Nodejs|YAML|
|Amateur web development|Sass,Less,Css|Markdown|
||Other cool stuff|PHP|

Now that you know where I stand,back to the main point.

>So why this **"Framework"** (can i call it that?) ?

+ It's (*majorly*) open source.

	This gives you the ability to not give up on it.Put another way,this means that you cannot blame someone else for something not working and sit with your head in your hand and say that solving this is 
	<img src="../assets/images/impossibru.jpg" width="200" height="100" />

+ Github Pages
	
	Its all on the cloud.You do not need to keep a copy in a safe place.Neither do you need to keep a copy on you when you want to work on it from someplace else.
	Yes you could use your own private space for the same.But isn't this so much more easier?
	And I have noticed that these websites load quite fast.You really dont need worry about optimizations as long as you really dont plan on loading a video for the background or something.(I plan to try that someday).
	Another feature which i like is the version control.It lets me treat the posts like I want without having to keep 

+ Organized and logical


	I have worked with pure HTML.It's a disaster.Initially all the projects that I worked on were HTML + CSS + JS. Javascript was still easier to debug.Cross browser compatibilities totally messed up HTML and CSS.Those presumptuous browsers would render pages as deemed fit by them.
	How do you work without Sass or Less these days?
	I used to debug/write/code/modify stylesheets from the browser thanks to [Chrome's capability to work as an IDE now][1].
	Sublime has  a brilliant [less2css][2] plugin which takes care of converting your Less files to css so that your project structure(which you cannot fiddle with) does not change.
	Sass, IMHO,for an amateur isnt that different from Less.It gives you the ability of classes and inheritance and a lot of performance tweaks.But Less is a tad bit easier to install for us non ruby Windows<sup>&trade;</sup>-speaking *cannot-afford-a-mac* people.


+ SSG

  Static Site generators might have their flaws.But they are apt for blogging.You do not need to worry about a database or other frontend,middleware,backend components of your site.You concentrate on the content and trust me,thats the hardest part
  ***points at self***

   {% highlight java %}
	self=this.site
   {% endhighlight %}

   Yes I just personified this whole site.

+ Jekyll
	
    It redefines easy.Even its [directory structure][3] underlines how a blog should work.the `_drafts` folder functions like your staging area where you could,well..**Do anything**.Draft till kingdom-come and then move it to the `_posts`,and it gets published.Yes that is pretty much like copy paste thing.But bear in mind this is your mobile workspace.Your drafts and posts are under svn.You do not have to bother about different versions of the draft in different folders(Its really not that hard to lose something on your computer).

    It also provides you the unique quirk of `_includes`.Where you could add HTML or your personal non-content additions in an organized manner. Its like those Bootstrap,Backbone,Jquery combinations where you reload only the data div while verything remains constant.

    This quirk is what convinced me to move to the dark side.Because I love coding and I am a programmer.I could not blog using a CMS like wordpress because while it makes bloggin easy,it makes modifications harder(remember [I do not know](#dontknowlist) PHP).

+ Jekyllized Generator:

	For those of you in javascript development who ahve not heard of [Yeoman][4],please acquaint yourself to it.Its a thing of beauty w.r.t to scaffolding and other generating boiler palte code.
	Now comes out the gem (or for those Ruby people a bunch of gems)
	[generator-jekyllized][5] by [@sondr3][6] is a beauty.Although the page states it is still unfinished,It is amazingly stable and very debuggable.By the magic of Gulp and yo,it automates all your process flow and you are left concentrating only on the content and not the scaffolding,plumbing and all the other euphemisms with absolutely no relation to what you have to do(pull the hair off your head).


There you go.Thats my **"stack"**.Its not much,heck its nothing apart from a bloggin platform.But I hope to do more.Lesse :).












[1]:https://developer.chrome.com/devtools/docs/workspaces
[2]:https://github.com/timdouglas/sublime-less2css
[3]:http://jekyllrb.com/docs/structure/
[4]:http://yeoman.io/
[5]:https://www.npmjs.com/package/generator-jekyllized
[6]:https://github.com/sondr3/