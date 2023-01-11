# Pycraft Progress Report! 28/10/22

Hello there everyone! It’s time for our usual weekly progress update, however for this time only things are a bit unusual as we summarise the progress from the last two weeks as we had to rearrange our schedule to allow for the release of the next article for Pycraft. This article takes a more in depth look into the changes to the settings menu (although admittingly, due to size constraints we where not able to discuss this in as much detail as we would have liked) as well as why we needed to change so much in the jump from Pycraft v9.5.4 to Pycraft v9.5.6 (which work begins on in January of 2023) and in addition to all this we also gave a sneak preview of the dungeon mechanics and a more in depth look into what we have planned for the next few years of Pycraft’s development. You can find this article on Dev, Medium and Revue at their following respective links: https://dev.to/pycraftdev/how-we-are-making-a-video-game-in-python-2fl7 https://medium.com/@PycraftDev/how-we-are-making-a-video-game-in-python-8-dec592752e1b https://www.getrevue.co/profile/PycraftDev/issues/how-we-are-making-a-video-game-in-python-8-1490492

With that out of the way, we will be starting this article with the progress for the week beginning the 28th of November, and will be writing our weekly progress update chronologically.

We started off with a continuation of testing the installer with our successful pass style approach, although by this time we where a large amount of the way through this process, having already tested the installer and uninstaller using the same technique and finding it to be very successful. For more information on how we tested the installer and how it was different to testing the rest of Pycraft feel free to check out the previous iteration of this series!

From there a large part of the past few weeks has been allocated to adding in docstrings to Pycraft, and although we touched upon this previously, to recap:

Every function/procedure/class will have (and will always have) a corresponding docstring providing information on what that area of code does, as well as the code’s relevant inputs, outputs and keyword arguments which will all have descriptions documenting their use and expected data types.

This is a feature that we are adding after the testing process for Pycraft versions with either a major or minor version change, for example going from Pycraft v9 to Pycraft v10, or from Pycraft v9.6 to Pycraft v9.7. (Pycraft v9.5.5 is the base documentation and is slightly out of character for this trend, this is just as we get things all set-up). We do this process after the testing process as it does not make any changes to the actual source code for Pycraft, and will be written or updated when the source code for that section is in its most finished form, so therefore will be as reliable and accurate as possible.

In Pycraft, EVERY class, function and procedure will have an attached docstring. The same is true for all public sister projects to Pycraft (for example the installer). In Pycraft v9.5.5 there is approximately a total of 384 individual areas of code like this that need docstrings, and as you can imagine this process takes some time. Even at the time of writing, two weeks on, we are still not finished on this task, although we are close to being finished.

As such, towards the end of the two weeks we have started work on the new documentation for Pycraft. For those unfamiliar, there is already a documentation for *some* of Pycraft, but it is old, poorly maintained and in no way user friendly. We therefore aim to take what we have learnt when making that documentation and completely start from scratch, however it will be some time before our work is made public as we manage writing docstrings for Pycraft, adding them into the new online documentation and also writing additional content there. We are not yet making our work public as it will overwrite all of the original documentation and it will not be recoverable – although at this point in time, why you would actually even try to use that… mess… is unclear. We will however be making a backup just in case that documentation (even in its unfinished form) is needed by someone later down the line.

On the subject, at the present time due to restrictions in how we are making our documentation on ReadTheDocs and GitHub Wiki’s we will not be able to show previous versions of the documentation. The supported branches of Pycraft (i.e the ones with documentation) will be the ones that show in the ‘branches’ section of our GitHub repo (which you can find here: https://github.com/PycraftDeveloper/Pycraft), we are looking for a suitable solution to this, however if one cannot be found then the documentation will be made available either vie a Google Docs link, or by email if requested in the meantime. All new documentation will be made available when a solution to this problem has been found.

So then, given all this progress, what stage are we at now? Well currently Pycraft v9.5.5 is finished, and we finished it about 2 weeks earlier than planned, so we are currently trying to break up the release of the last article and the release of Pycraft v9.5.5, if not by the full two weeks, then by at least some time, regardless this update will be made public before the 25th of December 2022. Because Pycraft v9.5.5 is finished doesn’t mean that we are not working on other things surrounding Pycraft though.

Regardless of when we finished Pycraft v9.5.5 we were going to be changing our focus to work on the documentation (that we aim to finish by part-way through January) for the time being, and our work on the docstrings for Pycraft has accelerated this process, as a large amount of the documentation is now finished!

Therefore, we are pleased to showcase two photos of the latest status on the documentation for Pycraft! (The bottom one is newer, although taken before we noticed a small problem – easily fixed though)

![The start of work on the be documentation for Pycraft, there isn't much to see, but we have completely changed the style of the documentation to suit a darker theme (there is also still light theme if you prefer!](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377322788/rANigdwFJ.png align="left")

![The continuation of work on the be documentation for Pycraft, there isn't much to see, but we have completely changed the style of the documentation to suit a darker theme (there is also still light theme if you prefer! We have also now added in the contents of the GitHub repo as well](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377324645/R19vrfJTd.png align="left")