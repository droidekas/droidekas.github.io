---
title: My Tryst with emacs
layout: post
section-type: post
category : tech
tags : ['emacs','dot-file']
---

I’ve always been fascinated with emacs as an editor. I have always been a keyboard person. The first I would do on any system is set up as many keyboard shortcuts as possible. The general tendency while saving a file is

 -  <kbd>Cmd</kbd> +<kbd>Alt</kbd> +<kbd>L</kbd> (A couple of times)
 -  <kbd>Cmd</kbd> +<kbd>S</kbd>
 -  <kbd>Cmd</kbd> +<kbd>Alt</kbd> +<kbd>L</kbd> 

But that is everyone's tendency.I assume that the Mouse and a Laptop
have a very unequal love story.But the _Magic Trackpad_<sup>TM</sup>
is something I could get used to.


Emacs _apparently_ comes in several flavours.Apparently being the
keyword here.[This StackOverflow thread][1] covers that topic
adequately.Being the procrastinator and inqusitive kind I
tried several of them(Aquamacs,Spacemacs,Emacs,CarbonEmacs).
But I stuck to Emacs.I can say the single most influencing
factor was this chart from the same SO thread.

![TextEditorChart](/img/posts/text_editor_charts.jpg)

I always try to learn things which have a spiral learning curve.
It makes the learning experience so frustrating and diverse and fun
that you end up learning a lot more ways of not doing things than doing them.

I uses Gnu Emacs from [emacsformacosx][2].Vanilla projects are so much more fun
 than heavily moded versions.For those vim to emacs converts there also is the
 [Emacs Evil mode][3] which provides vi shortcuts.

I went for the usual pilgrimage; Download emacs -> Google "Basic emacs tutorials
and beginner plugins".Google informs me that my best friend is <kbd>C-h</kbd>.It
indeed was.Emacs has a brilliant guide with appropriate links that makes it easy
to learn commands too.

It did take a while to setup a good interface so what I would suggest is to take
up a good starting point.It is much easier to tinker emacs configurations
instead of creating one by yourself.Since I started using emacs to learn
Clojure[^1],I used the setup from the [emacs-for-clojure][4][^2].It setup all the
package sources,basic editing functionalities and also takes care of a few edge
cases when you try using ageless software like emacs for the  gui-dependent
techies of today(I still belong to that group btw).So while the clojure learning
spree did not stick,emacs did.

You see ,you cannot possibly perceive the advantages of a terminal editor till
you start working on remote systems.That started when took up the task of
setting up CI servers and fiddling around with a Raspberry Pi.You can setup a
git repo with your dot-files (.emacs.d) in this case which makes setting up your
environment a breeze. Consider this like the trusty backpack of a frequent
traveller.Nothing makes you feel at home in a new System like a personalised
 set of dot-files.[Mine][5] currents consists only of emacs because I am trying
 to figure out a way to automate package installs with the same.
 
 Another fascination that I have with emacs is how all text editors now days are
 basically reinventing features of vi,emacs etc.Built in
 REPLs,VCS,distraction-free-mode ,multi cursor support ; all are features which
 are immensely customizable in these timeless editors.The next project was
 setting up mail in emacs which well,was a pain and I did not stick to it.But
 the setup process was amazingly cool.


[1]:http://stackoverflow.com/questions/1430164/differences-between-emacs-and-vim
[2]:https://emacsformacosx.com/
[3]:https://www.emacswiki.org/emacs/Evil
[4]:https://github.com/flyingmachine/emacs-for-clojure
[5]:https://github.com/droidekas/dot-files
[6]:https://github.com/xiaohanyu/oh-my-emacs
[7]:https://github.com/eschulte/emacs24-starter-kit
[8]:https://github.com/bbatsov/prelude

[^1]:I actually had installed emacs to learn Lisp,and then moved on to Clojure which I swear to the gods that I shall complete.
[^2]:There are several other options for this:[oh-my-emacs][6],[emacs24-starter-kit][7],[prelude][8]
