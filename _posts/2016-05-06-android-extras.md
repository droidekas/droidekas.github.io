---
layout: post
section: post
category: tech
title: "android-extras"
date: "2016-05-06 20:35:42 +0530"
tags: ["android","groovy","cli","github"]
---

This project started out of just the lack of desire to repeat monotonous
tasks which dont really take more than a second.Its a simple wrapper
around adb with few long commands give much shorter forms. There is a groovy
dependency right now which i hope to remove some day[^1].Its really not anything
too new.All you have to do is setup your groovy path and add the following to
you config files:


(% highlight sh %}

   devtools(){
         groovy /path/to/repo $*
   }
   
{%endhighlight%}


##Toggle Charging:
**Requires Root**

Toggle charging mode for my Device(One Plus One)
       - Tweak the settings based on your particular device or phone.
       - xda should be able to give you the location of the charging_enabled file on your device.

What you can do right now?

 - Clear cache and data for any app  `devtools clear <app-package-name>`
 - Launch any app `devtools launch <app-package-name>`
 - Provide the deeplink intent to an app `devtools deeplink <deeplink>`
   - This needs extra configuration where you need to add your app 
     `app_name=<app-package-name>`


Trying to figure out auto wifi adb connect in the process.



[^1]:Bash scripting is on the agenda
