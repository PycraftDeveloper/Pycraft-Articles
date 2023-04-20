---
title: "Pycraft progress report! 19/04/2023"
datePublished: Thu Apr 20 2023 18:08:19 GMT+0000 (Coordinated Universal Time)
cuid: clgpfrlcj000509l7585e5rbw
slug: pycraft-progress-report-19042023
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681928168741/2d582b03-d9a7-45fe-8f4a-35473a621109.png
tags: programming-blogs, opensource, game-development, pycraft

---

Hello there everyone, it's time for our weekly progress summary for Pycraft, and I think that we have just had one of the most productive weeks in the entire 5 years or so we have been working on Pycraft! Needless to say, there is plenty to talk about today - starting with the announcement that Pycraft's installer is now "finished"!

Although unfortunately by "finished" I mean that every individual component of the installer that we have been working on over the last few weeks is now finished, there are a few final 'housekeeping' jobs to do before we can announce that the installer is finished.

But this time last week we were not able to discuss the installer even as being in this "finished" state, so what have we been working on over the last 7 days?

Well, there are 3 main areas to Pycraft's installer, there is the installer, which we had already finished working on last week, there is the uninstaller and the updater, and it is those last two components that we have been working on and have finished this week.

Let's start with the uninstaller. Of any area in Pycraft's installer, the install component was probably the worst written, and the uninstaller was the least optimised, close to 40% of the uninstaller was repeated code, so naturally the first task of this week was to fix this, as we quickly realised we didn't need 3 different methods of removing the same file, so decided that the "action stage" where we would go through and uninstall Pycraft should be completely re-written.

Completely re-writing an entire section like this was something we had hoped to avoid, due to how much additional time that would take, however it wasn't something we would avoid doing if necessary, and in the uninstaller, we decided to go ahead with it as we are rewriting a whole section, but the rewritten section is comfortably 75% smaller than the original. By doing this we were able to optimise the file removal process as much as possible, and significantly reduce the complexity of Pycraft's uninstaller.

From there, now that the uninstaller was a lot more concise, we were able to conclude that the rest of the uninstaller was functionally fine, so decided to tidy up the whole program and move on to the update component, well ahead of schedule.

Right, let's talk about the update component of Pycraft's installer - by first talking about the installer and uninstaller. In Pycraft's installer, you can consider the installer and uninstaller to be fundamental components, and the updater as a composite combination of the two fundamental components of Pycraft's installer. Additionally, a lot of the components of the updater had been migrated into the main installer, for example before you could click on "update" and check for updates and only then if there were any available would you be able to continue, now only if there are any updates available will you be able to access the update program.

What that means is that the updater has been significantly simplified and as such only took around 2 days to work on and finish. Additionally, whilst the actual code itself is simpler, so is the user experience, as we have significantly improved the UI and taken on user feedback to improve its overall user-friendliness.

Now, with all the major components of Pycraft finished (and the repair component coming in a not-too-far-away update) this means that we are nearly finished with Pycraft's installer - with only a bit of code cleaning left to do. Fortunately, this is not the end of work on Pycraft v9.5.0dev8 as we still have numerous improvements to make in Pycraft itself, like for example improving controller compatibility.

We hope you enjoyed this week's progress update!

![The last page of Pycraft's update component is shared with the installer](https://cdn.hashnode.com/res/hashnode/image/upload/v1682013635693/a83eddf2-3673-4d7a-88ea-280a3c9a0dd0.png align="center")