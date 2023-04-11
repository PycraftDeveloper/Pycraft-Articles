---
title: "Pycraft progress report! 11/04/2023"
datePublished: Tue Apr 11 2023 12:48:22 GMT+0000 (Coordinated Universal Time)
cuid: clgc9dgkb000l0al74wta5htv
slug: pycraft-progress-report-11042023
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681213150172/96c0c79e-6e45-4ed5-b6c7-8e097e5e13a4.png
tags: programming-blogs, python, opensource, gamedev, pycraft

---

Hello there everyone, It's time for our weekly Pycraft progress report! If you were wondering why there isn't one for the previous week, that is because we were on holiday, and we were planning to combine this week's progress update into next week, however in the last 4 days we have made a lot of progress, and we are super excited to share that today!

Over the last few days then we have been focusing on the installer for Pycraft, and more specifically on its install component, but before we focus on that, let's talk about the history behind the installer and what we have done with the installer in general.

Since we started working on the installer, there have been 3 major versions, and we have only recently added this into the installer, for reasons we will get onto later. We have listed the major versions below, and what differentiates them, but it's important to note that minor, patch and developer versions of that major install version may change its feature set.

* Firstly we have installer v1.x - This installer was never made public and was more of a proof of concept that we could have an installer for Pycraft. This installer worked for approximately 1 year and approximately 4 major updates to Pycraft.
    
* Then after a gap of 3 years, we have installer v2.x - This was our first installer to be made public, it was written to only support Windows, as that was the only operating system we actively tested Pycraft on at the time. This installer 'worked' for approximately 2 years, and 9 major releases of Pycraft - because of this, if you have ever used the installer for Pycraft before today, chances are it was this version.
    
* Then now we have installer v3.x - This is not as different in terms of code as the jump from v1.x and v2.x, however, this is the first installer to use GitHub as the main download site for Pycraft instead of PyPi (although PyPi is still used for Pycraft's dependencies). This installer has been reworked (but not rewritten) to include at fundamental level support for a range of operating systems but has official and hard-coded support for Windows and Linux users. This has worked for approximately 0.003 years and 0 major releases of Pycraft - it's currently been working for one day!
    

Now that we have discussed the different revisions of the installer, and in general, what sets them apart, let's talk about the changes we have made over the last few days to Pycraft's installer (v3.x).

Initially, we started by updating the fundamental structure of the installer to match the structure we have for Pycraft, making switching between the development of either system much easier. The biggest of the structural changes involved adding a registry to Pycraft's Installer - however, we later experimented with the idea of having one central registry and then dedicated registries for each major program that makes up the installer, where we felt it was necessary. This wasn't something we had experimented with before, and whilst we have no plans to roll out this structural change globally, it does open up some interesting possibilities in the future.

Following that we did a fair amount of cleaning up of both the code and the UI design. This improved the installer's use of PEP-8 and also involved the removal of a large number of global variables, which is an underlying job we have throughout Pycraft and its companion programs, and we are now at a point where the majority of the global variables we have are for communicating with code running in parallel and are not easily removed.

From this point onwards through this blog, all of the changes we make are to the main body of the installer, and the install section and its components.

The final thing we did in the cleaning-up process was to remove the strange off-white background to some widgets, something we had previously thought not possible. This was much harder than we were expecting, but makes the entire installer look a lot less haphazard and rushed.

Finally, this leaves us with two final tasks for the install section of the installer before we can move on to the other components - the uninstaller and the update processes:

* We needed to update the process of actually installing Pycraft so that it uses GitHub releases, and can navigate the new directory structure we have for Pycraft, which we don't plan on changing again. The process of installing Pycraft's dependencies relies on us being able to navigate Pycraft's directory structure to find the 'requirements.txt' file and then use PyPi to install the additional packages as required from there.
    
* Then we needed to improve Linux functionality - we had already improved general operating system compatibility through the use of Pathlib for file paths - So now we needed to add functions to add desktop and start menu shortcuts when using a Linux-based operating system. Unfortunately this isn't something we can do on a general level like we could use file paths, and as such only supported operating systems (Windows and Linux) can have desktop and start menu shortcuts made.
    

Now, with all those changes made, we can share the progress we have made, there are a few small things we have to change still, but the installer is functionally complete and working!

![Pycraft's initial install screen](https://cdn.hashnode.com/res/hashnode/image/upload/v1681216929783/0a201f35-6aa2-4a68-b9b1-461bc663b998.png align="center")

![Pycraft's secondary install screen](https://cdn.hashnode.com/res/hashnode/image/upload/v1681216920991/1b5c0841-1fcc-4292-afd5-734a6d7cfb3a.png align="center")

![Pycraft's 3rd install screen, you can choose the install path for Pycraft here](https://cdn.hashnode.com/res/hashnode/image/upload/v1681216912401/7c9915ac-66d4-4945-8c7d-5b46622941e8.png align="center")

![Here on install screen 4 we download and install Pycraft](https://cdn.hashnode.com/res/hashnode/image/upload/v1681216904447/5043ebd8-faf6-492b-9612-2f09e19a15a7.png align="center")

![Finally we have the options to create shortcuts and open release notes if the user wants to](https://cdn.hashnode.com/res/hashnode/image/upload/v1681216890824/fa9df3bf-f0d4-4476-9b4a-49be7325730f.png align="center")