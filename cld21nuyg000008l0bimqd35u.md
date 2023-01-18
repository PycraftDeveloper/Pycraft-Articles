# Pycraft Progress Report! 09/01/23

Hello there everyone! Its time for our weekly progress update, and this is for the week beginning the 9<sup>th</sup> of January 2023. In this article we look at the preparations we are making in Pycraft v9.5.6 as we get closer and closer to its release – and then look at what is coming in Pycraft v9.5.7!

We started the week with a significant amount of work on the documentation, something that we put less focus on during the middle of the week, but ramped up again towards the end of the week and going forward into the next. This is because the release of Pycraft v9.5.6 is just around the corner, and whilst Pycraft and its sister project the installer are both nearly complete for this deadline of around the 20<sup>th</sup> of January, the documentation is still dragging behind.

This week we made a big push to get the rest of the formatting guide finished, and having written most of that up this week, we are pleased at now finishing that. For those unfamiliar about this section of the documentation, the formatting guide is a set of guides that builds off the PEP-8 groundwork by adding in – not rules – but a guide to how we have formatted Pycraft’s source code, shaders and files, so that additional expansion can be done in this area whilst still being in keeping of the layout of Pycraft. Now, we are still far from having full PEP-8 compatibility and as such there is a section of the formatting guide that outlines the progress we are making to bring Pycraft in line with these standards of programming practice.

Now, aside from the formatting guide, we have also been busy transferring over other areas of the repository that are important, including the planned story line and the new difficulty comparison guide we have recently started working on in Pycraft’s GitHub repository. This is our way of keeping track of the changes in game mechanics between normal and hard mode – remember, we want to make hard mode challenging, but we don’t want to make it impossible or too frustrating. This therefore is a handy guide for you to see what the changes will be, and also gives you more of a sneak preview of future features we have in mind for the game. You can also see the changes that we have been implementing to Pycraft currently, although there are not too many as yet as the game engine isn’t very near completion yet.

There is one section that is a part of Pycraft’s repository that gives the user a preview of the different sounds and music we have been working on for different areas of Pycraft. This will be much harder to transfer over to the documentation given that it has embedded audio clips, so that will hopefully be coming, but wont be likely to arrive for a while yet as we find a solution to this.

Now, its time to talk about work outside the documentation, and there hasn’t been a lot of feature additions this week – mainly because we have added them all! However there have been yet more minor feature tweaks, including a slight adjustment to the animations in the save menu to make them match the excellent start-up screen we have! There have also been a significant amount of work done to the installer, however we have plans to talk more about that next week as that’s when the majority of that work is likely to take place.

We have also been working on testing Pycraft again, and unlike the testing we performed in Pycraft v9.5.5’s release, and the testing that we do at the end of every series of development updates we are only focusing on the features that we have changed or modified in this update – Pycraft v9.5.6, this way we can save on time by not testing every area of Pycraft, something that would likely take longer than the entire amount of time we have allocated for the entire development cycle of Pycraft v9.5.6! This also allows us to focus specifically on a small section of Pycraft and really make sure that we get it right, something that we really need to do, partly due to the file handling (moving, creating and removing) and also partly because of how important the saves functionality will be as we progress through development.

The saves mechanic is something that we don’t plan on changing now that we have added it in, as we are trying to make saves and configurations of Pycraft as backwards and forwards compatible as possible. Content not used in the save should remain untouched and not cause problems, and on the flip side, content that isn’t present in a save should be able to be repaired without needing to modify the other contents of the file, where there is enough data to rebuild the file from. Some functionality that is missing in a save could cause problems for other features, however as we are not yet at a stage where we need to worry about that, we are planning workarounds, but until we actually see this problem in practice we won’t know what to expect.

Now the reason it’s taken so long for us to get saves introduced to Pycraft is because of how much work has gone into making the save files as accessible to the end user and developers, and because we want to make sure that we can reliably recover and repair the contents of as file before we work on this, as we don’t want people to lose progress when updating their version of Pycraft. Pycraft’s configuration file is where we really start to see where this work took place, as this went through many iterations before we where happy with this concept.

Now, its time to share a highlight from this week of development, and we do have one, however this was taken from the documentation – rather than Pycraft its self as this was our main area of focus for this week of development!

![The new formatting guide for Pycraft](https://cdn.hashnode.com/res/hashnode/image/upload/v1674069274568/2818dc9d-fc6c-4bcc-825c-944e0aef4801.png align="center")