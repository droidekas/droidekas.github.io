---
title: Adding that floating button
categories: ["Building this site"]
tags: ["UI"]
published: True
layout: post
---

Being an android developer,I am heavily influenced by the Android design philosophy.This design is quite inline with [material][3] design.And considering us *Android-<small><small>develop</small></small>ers* cannot get our hands Android 5.0 devices that easily.We have be content with emulators(*eeurgh*).I decided to try a few components on website interface.So I hope no UI/UX designer sees this.

>a very interesting discussion is [here][4].

That tiny blue button took me about 3 hours to add.
<small><small><small>Yes i know that makes me look stupid.</small></small></small>

But I digress(as usual) thank you [nobitagit][1] for the fantastic [floating action bar][2] component.

This has the most detailed css documentation that I have come accross.Not only is it extremely  easy to use,but also looks supremely complicated().

I had decided to have this component in all pages.But this button by design is supposed to be contextual.Jekyll's [templates][5] and `_include` provide a brilliant solution.

So just add an the relevant html code as file to `_include`.

*<strong style="color:green;">action_button.html</strong>*

{% highlight html %}
<ul class="mfb-component--tr mfb-slidein">
	<li class="mfb-component__wrap">
		<a href="#" data-mfb-label="A long long label" class="mfb-component__button--main">
			<i class="mfb-component__main-icon--resting ion-plus-round"></i>
			<i class="mfb-component__main-icon--active ion-edit"></i>
		</a>
		<ul class="mfb-component__list">
			{% for action in page.actions %}
				<li>
					<a href="#" data-mfb-label="{{action.title}}" data-mfb-label="label with long long title" class="mfb-component__button--child">
						<i class="mfb-component__child-icon {{action.icon_class}}"></i>
					</a>
				</li>
			{% endfor %}
		</ul>
	</li>
</ul>
{% endhighlight %}







[1]:https://github.com/nobitagit
[2]:https://github.com/nobitagit/material-floating-button
[3]:https://www.polymer-project.org/docs/elements/material.html
[4]:http://ux.stackexchange.com/questions/67419/do-material-designs-floating-action-buttons-provide-a-bad-ux




