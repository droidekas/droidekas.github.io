---
layout: 
title: Why do we need an onAttach()
categories: []
tags: []
published: True

---

_**TL;DR**_:

In order to **not break** the design consistency amongst different UI components in android,the `onCreate()` method will have similar functionality across all of them.

When linking Containers to Contents  like Window to Activity and Activity to Fragment a preliminary check needs to be done to determine the state of container.
And that explains the use and position of `onAttach()` in the fragment lifecycle.



_**Too short;Need longer **_

The answer is in the archetype code itself,


    @Override
        public void onAttach(Activity activity) {
            super.onAttach(activity);
            try {
                mListener = (OnFragmentInteractionListener) activity;
            } catch (ClassCastException e) {
                throw new ClassCastException(activity.toString()
                        + " must implement OnFragmentInteractionListener");
            }
        }

Another example would be in Jake Wharton's [ActionBarSherlock][4] library.

Why would you want to use a method like `onCreate()` which is has the same purpose in an [activity][2] ,[service][3].

The `onCreate()` is meant to handle issues with respect to that particular context creation.It does not make sense if `onCreate()` is used to check the state of its container.

The second reason that I can come determine is that a fragment is designed to be activity independent.The `onAttach()` provides an interface to determine the state/type/(other detail that matters to the fragment) of the containing activity w.r.t the fragment before you initialize a fragment.

**EDIT**:

An activity exists independently and therefore has a self sustaining lifecycle.

for a fragment :

1. The independent lifecycle components(same as any other components):
    - onCreate()
    - onStart()
    - onResume()
    - onPause()
    - onStop()
    - onDestroy()

2. The interaction based components:
    - onAttach()
    - onCreateView()
    - onActivityCreated()
    - onDestroyView()
    - onDetach()

from the [documentation][1]:

> The flow of a fragment's lifecycle, as it is affected by its host
> activity, (...) each successive state of the activity determines which 
> callback methods a fragment may receive. For example, when the
> activity has received its onCreate() callback, a fragment in the
> activity receives no more than the onActivityCreated() callback.
> 
> Once the activity reaches the resumed state, you can freely add and
> remove fragments to the activity. Thus, only while the activity is in
> the resumed state can the lifecycle of a fragment change
> independently.
> 
> However, when the activity leaves the resumed state, the fragment
> again is pushed through its lifecycle by the activity.

answering another question which came up in the comments:

> _**Caution**_: If you need a Context object within your Fragment, you can call getActivity(). However, be careful to call getActivity() only when the fragment is attached to an activity. When the fragment is not yet attached, or was detached during the end of its lifecycle, getActivity() will return null.


The design philosophy states that a Fragment is designed for reuse. A fragment (by design) could(and should) be used across multiple activities.

The `onCreate` by definition is responsible  to create a fragment.
Consider the case of orientation,your fragment could be:
- using different layouts in different orientations.
- applicable only in portrait orientation and not landscape
- To be used only on tables and mobile phones.

All these situations would require a check before the fragment is initialized from the android perspective(`onCreate()`) and the view inflated(`onCreateView()`). 

Also consider the situation of a [headless fragment][5].The `onAttach()` provides you the interface required for preliminary checks.




[1]: http://developer.android.com/guide/components/fragments.html#Lifecycle
[2]:http://developer.android.com/reference/android/app/Activity.html#onCreate%28android.os.Bundle%29
[3]:http://developer.android.com/reference/android/app/Service.html#onCreate%28%29
[4]:https://github.com/JakeWharton/ActionBarSherlock/blob/fe0125aedd889f6f5d9bd8ca09e1e79d9ffc0c58/actionbarsherlock/src/com/actionbarsherlock/app/SherlockFragment.java#L22
[5]:http://luboganev.github.io/blog/headless-fragments/



