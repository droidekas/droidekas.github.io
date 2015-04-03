---
layout: post
title: Adding Travis CI
categories: []
tags: []
published: True

---

So I've been trying to Travis builds to my workflow for the past 2 days.And after 32 + 14 builds I have finally ironed out all issues.All that is left is a slight amount of clean up.
Its quite direct and simple.
<!--end-excerpt-->

1. Go to the [travis][1] website.
2. Login with github credentials
3. From your list of repositories,select all repos you would want to use CI for.In this case it would be `<username>.github.io`.

That ends the work on the travis website.No back to your project.I have made my project to have 2 branches,viz.
-master:
	This contains the the output of `jekyll build`.This static site is served by github.
-development
	This contains my entire building environment with node,jekyll gems,gulp etc etc.

cd into your directory and use

{% highlight shell %}
	gem install travis
{% endhighlight %}

Now you let it do its thing.And now you need to get an API token for travis to use.There are 2 ways to do this.

The GUI way:
1. Open the [user settings][2] and the applications sub-menu
2. Click on generate new token in the Personal access tokens.
3. The only permission that is needed is the public_repo permission.
4. Go ahead and generate the token,and make sure you keep it somewhere safe for the time being.
5. Now go back to your,









[1]:http://travis-ci.org
[2]:https://github.com/settings/applications