---
title: Adding that floating button
categories: ["SiteBlocks"]
tags: ["UI"]
published: True
layout: post
---


Being an android developer, I am heavily influenced by the Android design philosophy.This design is quite inline with [material design][1] . Considering us *Android-(develop)-ers* cannot get our hands Android 5.0 devices that easily, we have be content with emulators( *eeurgh* ). I decided to try a few components on website interface. That tiny plus button took me about 3 hours to add.<small><small><small>Yes, I know that makes me look stupid.</small></small></small>

<!--end-excerpt-->
>On a more holistic level ,a very interesting discussion is [here][4].



But I digress(as usual) thank you [@nobitagit][2] for the fantastic [floating action bar][3] component.

This has the most detailed css documentation that I have come across. Not only is it extremely  easy to use, but also looks supremely complicated.

I had decided to have this component in all pages. But this button by design is supposed to be contextual. Jekyll's  `_include` provide a brilliant solution.

So just add the relevant html code as file to `_include`.





*<span class="filename">action_button.html</span>*

{% highlight html%}

<ul class="mfb-component--tr mfb-slidein">

  <li class="mfb-component__wrap">

    <a href="#" data-mfb-label="main label" class="mfb-component__button--main">
      <i class="mfb-component__main-icon--restingion-plus-circled"></i>
      <i class="mfb-component__main-icon--activeion-information"></i>
    </a>
    {% raw %}
    <ul class="mfb-component__list">
      {% for action in page.actions %}
        <li>

        <a href="{{action.link}}" data-mfb-label="{{action.title}}"
          class="mfb-component__button--child">
          <i class="mfb-component__child-icon {{action.icon_class}}"></i>
        </a>
        
        </li>
      {% endfor %}
    {% endraw %}
  </ul>
</li>
</ul>
{% endhighlight %}

This include then snugly sits in your layouts like:

<span class="filename">default.html</span>

{% highlight html %}

{% raw %}

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en-us">

  {% include head.html %}

  <body class="theme-base-0f ">

    {% include sidebar.html %}
    {% include action_button.html %}

    <!-- Wrap is the content to shift when toggling the sidebar. We wrap
     the
         content to avoid any CSS collisions with our real content. -->
    <div class="wrap">
      <div class="masthead">
        <div class="container">
          <h3 class="masthead-title">
            <a href="/" title="Home">{{ site.title }}</a>
            <small>{{ site.tagline }}</small>
          </h3>
        </div>
      </div>

      <div class="container content">
        {{ content }}
      </div>
      <div class="comments">
        {% include comments.html %}
      </div>
       
    </div>

    <label for="sidebar-checkbox" class="sidebar-toggle"></label>

  </body>
</html>
{% endraw %}

{% endhighlight %}

Now that I was done with the setup, I could concentrate on the button itself. I would have 3 categories(depends entirely on you) of contexts. Those I added in the `_config.yml` as defaults. These can be overridden in each post. But bearing in mind [that box][5] in the Jekyll website, I decided to **DRY**.



So my addendum to <span class="filename">_config.yml</span>

{% highlight YAML%}

defaults:
  -
    scope:
      path: ""
      type: "posts"
    values:
      actions: 
        - label: "option1"
          icon: "ion-edit"
          link: "#"
        - label: "option2"
          icon: "ion-arrow-down-c"
          link: "#"
        - label: "option3"
          icon: "ion-social-github"
          link: "#"

  -
    scope:
      path: ""
      type: "pages"
    values:
      actions: 
        - label: "option1"
          icon: "ion-edit"
          link: "#"
        - label: "option2"
          icon: "ion-arrow-down-c"
          link: "#"
        - label: "option3"
          icon: "ion-social-github"
          link: "#"

{% endhighlight %}

I initially had a problem with figuring out YAML syntax. Heck, I still have a problem. So I would recommend this *bad boy*, a [JSON to YAML][6] converter to prevent you from breaking your head.

Now that the plugging of that beautiful widget is done, I could try figuring out a use case for it. In the mean time, shall try tinkering with the Sass files too. That I guess should cover one more post.


[1]:https://www.polymer-project.org/docs/elements/material.html
[2]:https://github.com/nobitagit
[3]:https://github.com/nobitagit/material-floating-button
[4]:http://ux.stackexchange.com/questions/67419/do-material-designs-floating-action-buttons-provide-a-bad-ux
[5]:http://jekyllrb.com/docs/configuration/#front-matter-defaults
[6]:http://jsontoyaml.com/







