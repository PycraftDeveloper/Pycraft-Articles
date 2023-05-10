---
title: "Pycraft Progress report! 10/05/2023"
datePublished: Wed May 10 2023 20:04:22 GMT+0000 (Coordinated Universal Time)
cuid: clhi4pvga000109jn90457pyd
slug: pycraft-progress-report-10052023
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682538475667/36cbf14a-8b42-4c6d-b354-bd83e2569d01.png
tags: programming-blogs, python, game-development, pycraft

---

Hello there everyone, it's time for our weekly progress update, and over the last week, we have made the finishing touches to numerous features that have been adjusted and improved in Pycraft, and have made major changes to the widgets system for Pycraft!

Let's start with some of the features that have been changed and improved over the last few weeks, and the one that immediately comes to mind is the new performance monitoring window for Pycraft. The one we have replaced it with takes advantage of the new metrics system (more on that in a bit) and is considerably shorter and more efficient, taking up just 53 lines compared to the 125 lines it took before. And that is a good way of looking at the progress we have been working on and aiming to achieve as we work on Pycraft currently; doing more in fewer lines.

Now, let's discuss the new metrics system for Pycraft. Whilst this is different to the performance monitoring/graphs, they were added in the same update, and for a significant period - close to 5 years - their only purpose was to collect information to display in the graphs. Whilst the way we do this has remained the same in that time, where we do that has changed significantly. In addition to this, the desire to collect information that is relevant to the performance impact of Pycraft on your system instead of the performance impact on your system from Pycraft.

This means we have now made a new utility module that handles all of the metrics collection. We have also removed the relationship between the collection metrics and the performance graph, so instead of only collecting metrics on demand, it runs passively in the background. This is in preparation for future scenarios where we add performance logging or better error reports but that's very much something we are looking into in future.

Note though that the metrics system is disabled automatically in-game if Pycraft determines it to be causing poor in-game performance. Also, this is something we are very strong on, any performance metrics are only ever stored in memory on your system, and are never stored locally or on a network location. Additionally, the ability to disable performance monitoring is available in the settings menu under the "developer options" tab.

Now, let's discuss widgets in Pycraft. Over the last few weeks, we have been going through every widget in Pycraft and have been converting them to an object-oriented programming paradigm, instead of a procedural programming paradigm. There are two main reasons for this. Firstly by doing this, we can make the widgets much easier to deploy outside of the settings menu, which was where they were first introduced. Secondly, this allows us to adapt the new widgets in such a way that we can optimise their rendering and computing functions.

The reason behind decoupling the rendering and computing of the widgets for Pycraft is that we are working on a new - better optimised - 2D rendering pipeline that should significantly improve the performance of Pycraft. This will work by using two dedicated clocks, one that runs at the specified frame rate, and the other that runs at intervals (this will be adjustable in settings under "video"). So this means if I set my game to run at 60 Hz (or 60 frames per second) the computer will run to target that frame rate. if I then set an interval of 0, then for every compute cycle the graphics will update. This is going to be identical in performance to what we are currently doing in Pycraft. However, if I set the interval to 4, then for every 4 compute cycles, the graphics will update, leading to a compute frame rate of 60 Hz, and a graphics frame rate of 15 Hz.

Naturally, it will be very noticeable if every frame's graphics were only updated for example 15 times per second, therefore the game will automatically "force" a frame at most with a delay of 1/(the current frame rate of the compute stage).

I hope you have enjoyed this weekly progress summary, here is a photo of the new performance monitoring/graphs, complete with the new metrics system running behind the scenes!

![Pycraft's home screen with a graph showing Pycraft's CPU and memory usage, as well as the current in game frame rate](https://cdn.hashnode.com/res/hashnode/image/upload/v1683748948340/19a87d05-0021-458d-b02c-8b974d20ea2a.png align="center")