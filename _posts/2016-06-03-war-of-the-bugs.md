---
layout: post
title: "War of the bugs"
---


#TrueStory

In android ,there are 2(well 3,but 2 are sort of similar bugs).

   1. An on open app crash(you might laugh but it happens)
      - unsupported architecture
      - rooted device at times
      - a conflicting xposed module
      - developer stupidity
   2. An unresponsive ui
      - A button does not respond
      - A dialog which cannot be dismissed because of the lack of an exit condition

I realised a type 2 issue.A crash in the app atleast provides you some information(Crashlytics,ACRA etc etc).But this.You have no way of knowing whats going except a large reduction in installs and an equal increase in uninstalls.

So you can image my pulse when i found this in my source code.And then lo and behold pop ups another bug.I was trying to setup 2 activites for a `onActivityResult()` scenario.However instead of calling on `startActivityForResult()` ,I had used `startActivity()`. While this prevented a certain (minor) functionality from working,it prevented the *major* bug.

Lessons Learnt:

 1.Bugs are helpful at times too.
 2.**Never ever ever**  deploy untested code,no matter how big the  sword dangling on your head.


PS: This should not be observed as my lack of competency :P._Shit happens_ at times.Especially when you are expected to deploy last minute untested code.
#LifeOfStartupDevs.
