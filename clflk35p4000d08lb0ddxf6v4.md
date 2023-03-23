---
title: "Pycraft progress report! 23/03/2023"
datePublished: Thu Mar 23 2023 20:18:30 GMT+0000 (Coordinated Universal Time)
cuid: clflk35p4000d08lb0ddxf6v4
slug: pycraft-progress-report-23032023
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1679595386229/2fdc1942-6f3f-44d1-96d7-72e733b86be7.png
tags: programming-blogs, python, opensource, gamedev, pycraft

---

Hello there everyone, its been a bit of a busy two weeks since we last spoke, and whilst there is plenty *now* to talk about, we didn't feel that in the first week, we had much to talk about, so, in addition to the focus on getting Pycraft v9.5.7 (or Pycraft v9.5.0dev7) released on GitHub, we decided to combine the two.

So, to start: within the first week, we were predominantly finishing up with work on Pycraft, as we were nearly done changing the way data gets transferred through Pycraft, and making some pretty significant under-the-hood changes to Pycraft. This change was designed to improve readability, expandability and flexibility within Pycraft's source code, which we have already talked about a fair bit.

During this first week, we also made a series of plans on what we wanted to do, not on the source code for Pycraft as such, but around Pycraft to make things much simpler and hopefully more accessible. Therefore before we continue into the rest of this progress update, we must make these two big announcements.

* We are changing the way versions work in Pycraft, non-developer releases are backwards compatible and unaffected by this change. For developer versions of Pycraft, the developer code we would assign each release of Pycraft has moved to allow for the re-introduction of patches as a release option. Developer updates now include the phrase 'dev' after the main version code and a number to represent the iteration in the cycle towards the release of the next version of Pycraft. The first and last digits of the main version code are cumulative, and as such, they should never decrease as we release future versions of Pycraft. All this means that Pycraft v9.5.0 remains the same before and after the change, and developer versions like Pycraft v9.5.7 now become Pycraft v9.5.0dev7. This change has already taken effect at the time of writing on GitHub and we will use the two version codes when referencing new versions of Pycraft for this article only.
    
* In addition to all this, the structure of the GitHub repository has changed. Originally we had branches for every currently in-development version of Pycraft, and for the most recent stable release of Pycraft. This has changed slightly now, the most recent stable release of Pycraft is now known as the 'master' branch, and the most recent developer release is known as 'main', in order of decreasing priority. From there the 'dev' branch is where the currently in-development version of Pycraft lives. When the code in the 'dev' branch gets completed, it gets its own (pre) release on GitHub, and replaces the code in 'main'. The code is now what changes in the repository, rather than the branches. Changes to the documentation and to adding content around Pycraft and the installer are affected by this change.
    

These two major changes around Pycraft are the main reason we have decided to release Pycraft v9.5.0dev7, as by splitting what was already going to be a pretty large developer update into two do make these changes benefits us and you, as it allows us to start development with Pycraft v9.5.0dev8 (Pycraft v9.5.8) with the changes applied, and benefits you as this is a much more standard and clearer way of development.

As we progressed into week two, which is ironically when those changes we just discussed take effect, our focus moved away from making progress on Pycraft, and more towards getting Pycraft ready for release. This was a very abrupt change of plan, and didn't allow us a lot of time to make the changes we wanted to, which makes us say that Pycraft v9.5.0dev7 *works*, and runs at a low level, but lots of the features we added more recently and changes we are currently working on have yet to be re-added. This includes things like the new built in pop-up mechanism, the new saves mechanic (which we plan on revising the backend for) and in general things like fullscreening the window or controller support have yet to be added.

All this makes us say that Pycraft v9.5.0dev7 is very much a 'two-parter' as the code is in an *operational* but not nessasarily *finished* state as yet.

We hope you enjoyed this two week progress update, we plan to get back to our normal schedule again for next time, and have also got plenty to share from the *operational* version of Pycraft, we hope you enjoy:

![Pycraft's game engine early morning](https://cdn.hashnode.com/res/hashnode/image/upload/v1679602459109/df1ee0bc-8660-433f-9859-f439309af2f4.png align="center")

![Pycraft's game engine afternoon](https://cdn.hashnode.com/res/hashnode/image/upload/v1679602414078/201fa1de-5fcf-41a0-bd71-fa037e1885cf.png align="center")

![Pycraft's game engine night](https://cdn.hashnode.com/res/hashnode/image/upload/v1679602428648/9b77b517-f1e4-443a-9861-b7a97f5432bc.png align="center")

![Pycraft's game engine night and stormy](https://cdn.hashnode.com/res/hashnode/image/upload/v1679602439398/a3a1d884-b7b0-41c4-a4dd-c0b5c165036b.png align="center")