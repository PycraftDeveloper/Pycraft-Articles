# Pycraft progress report! 18/09/22

Hello there everyone!

Its time for our usual weekly summary of the progress we made on Pycraft, and it’s been a busy week!

We started the week by completely changing how versioning works for Pycraft. We had been working up to this over the past few weeks, but there have been major changes to how versioning works in Pycraft.

Previously Pycraft’s version was structured in the form:
vA.B.C.D-E

Where “A” relates to if Pycraft is in an alpha or beta state.
Where “B” relates to the last major update.
Where “C” relates to the minor update.
Where “D” relates to the current patch revision.
Where “E” relates to the developer build.

However, this has many flaws;
To start with, the part of the version code labelled “A” never changed, and realistically, what that related to was pretty unclear too, I mean, what does an “alpha state” mean? Does it change anything? The answer. Not even we knew, which is why we have removed what, in this example, relates to the letter “A”.

Then we looked at the part of the version code labelled “D”, which relates to the current patch revision for Pycraft. In 3 years, we have only ever released 1 patch for Pycraft, often because we prefer smaller, but quicker paced updates, over larger but more spaced-out updates, so often there was no need for this part of the version code. In fact, this is usually never included in the version code which only added to the confusion.

Finally, we looked at the part of the version code labelled “E”, which relates to the current developer build of Pycraft. This is the part of the version that sees the most change, and is arguably one of the most important values as a result! It was now that we decided to merge the patch and developer sections of the version code together, which is risky as it could generate confusion over whether the current version is a patch or a new developer version, but realistically; because we don’t usually release patches, we are considering deprecating that second use of the version code.

This therefore means that the current versioning system for Pycraft now only uses 3 values, in the structure:
vF.G.H

Where “F” is the same as “B” and relates to the last major update.
Where “G” is the same as “C” and relates to the last minor update.
Where “H” is new and relates to the current patch/developer version of Pycraft.

In addition to all these changes, we also dropped the minor update part down a value, so what was originally meant to be Pycraft v9.6.5 became Pycraft v9.5.5, this is because we wanted to make changes to Pycraft linear, further simplifying the way versioning in Pycraft works, as not making this change would have meant that instead of going in order, Pycraft versions would, in order of increasing progress, have looked a bit like this:
… v9.5.8, v9.5.9, v9.5.0, v9.6.1, v9.6.2 …
Which doesn’t make a lot of sense!

With that out the way, we where able to move onto some more exciting progress! I am of course talking about seasonal events and the new load screen.

We will start with the new load screen, as that was technically started before seasonal events was. The load screen has been an integral part of Pycraft since the very early versions of the game, acting as a transitional layer between the 2D and 3D windowing engines. Its function for the first year of Pycraft’s development was largely not used, as the game engine was too slow to be able to handle even basic 3D assets. However, in year 2 we started the second major restructuring of Pycraft, and switched from using the PyOpenGL library to ModernGL, both wrappers of OpenGL for Python. This meant there was massive changes to Pycraft as the entire game engine was re-worked. It was at this time that the load screen saw more use, as ModernGL allowed us to easily and more efficiently scale up the game engine’s complexity, including the use of more detailed and complex assets that took longer to initially process, it meant loading times increased and the load screen was an excellent way of showing how far through the loading process you where, and also that Pycraft was still running.

Now it's time for the third restructuring of Pycraft, this time not changing the wrapper for OpenGL, but instead how we use that wrapper, and this meant we had to remove the load screen and rework it so that it would work with Pycraft’s new structure. So, behind the scenes of Pycraft v9.5.5’s development we have been taking the load screen and completely reprogramming it, from the ground up. This process is now very nearly complete, the new loading screen has been added back into Pycraft, and looks very similar to how it did before.

So that was the second of three objectives for this week, adding back in the load screen, however we also this week reprogrammed how the geometric graphic on the home screen worked so that it was not dependant on set positions on the window, and instead dependant on a bounding box, meaning we could then use the same program to re-use the graphic in the center of the load screen, where for over a year it was previously empty space! In addition to that, we have also designed two different loading bars, which are in the process of being voted on to see which one gets added, they are both functionally the same, and have both been extensively tested and work perfectly, its just their design that is different. Next week we will be announcing which design won the vote and made it into Pycraft!

Finally, we can talk about the final objective for this week – feature improvements. Adding in the load screen for Pycraft was a big moment for us, as it marked the completion of the final major feature of Pycraft v9.5.5 – the third restructuring of Pycraft. This brings us good news as it means we can start something new very soon, however it is bad news as well as it means we won’t have as much to share visually. Although we will be making up for this where possible by sharing more content from features, we have been working on in Pycraft v9.5.5, as well as more comparisons between the current version of Pycraft and Pycraft v0.0.0, the original version of Pycraft. Many things have changed since then, but some of the same principles are still in use in Pycraft today, and there are even some lines in some modules that are over 3 years old, dating back to the very first few weeks of development! That means now we have finished adding in features to Pycraft its “feature tweaking” time – where we go through and make final changes to some features, perhaps improving how they perform, or how they look, or maybe behind the scenes improvements like reworking a complex function to make it more developer friendly.

Then from there, the final stage of any release of Pycraft can be deployed – Testing and bug fixes! And after any large change to Pycraft there is lots, we need to test, and this is no exception. Usually a developer update may see at most a few new features and changes to existing features, as well as a lot of bug fixes, therefore meaning we can focus testing on those functions that have been modified, speeding up the time we spend on this step. This time around everything has seen at least some form of change, so instead of testing maybe 500-1,000 lines of code, we are testing 19,000 lines or more! It’s a monumental task and we will work through it as quickly and efficiently as we can, but we want to make sure that everything is done effectively!

Attached below are some visual highlights from the last week of development!


![Pycraft's new loading screen, with the new splash text: "Open Source!" (Credit to: TrayMoment on Twitter)](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377336613/iteRthuql.png)


![Creating a custom theme!](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377338340/L0JMWoDn-.png)



