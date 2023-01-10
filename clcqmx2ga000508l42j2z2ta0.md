# How We are Making a Video Game in Python #5

Pycraft’s banner image

*Pycraft, a 3D open-source open-world video game made in python with Tkinter, PIL, Pygame, Numpy, ModernGL, ModernGL\_window, PyAutoGUI, Psutil, Py-CPUinfo, GPUtil, PyJoyStick and Pyrr*

*This article, released roughly once a month will document what changes have been made to the project, what challenges we faced and how we overcame them and how and where you can install this project from. For anyone wondering, this is to accompany the regular updates on my Twitter page (@PycraftDev on twitter: www.twitter.com/PycraftDev) which are now also shared to my Dev profile here:* [https://dev.to/pycraftdev](https://dev.to/pycraftdev)[*.*](http://www.twitter.com/PycraftDev%29.) *This article is written by Tom Jebbo, the lead developer and graphics designer and I hope you enjoy both playing the game and reading this article!*

*   You can find the latest release of Pycraft (v0.9.3) here: [https://github.com/PycraftDeveloper/Pycraft](https://github.com/PycraftDeveloper/Pycraft)
*   You can find the latest developer preview of Pycraft (v0.9.4–4) here: [https://github.com/PycraftDeveloper/Pycraft/tree/Pycraft-v0.9.4-4](https://github.com/PycraftDeveloper/Pycraft/tree/Pycraft-v0.9.4-4)
*   You can find the latest feature preview for Pycraft (v0.9.5–0) here: [https://github.com/PycraftDeveloper/Pycraft/tree/Pycraft-v0.9.5-0](https://github.com/PycraftDeveloper/Pycraft/tree/Pycraft-v0.9.5-0)
*   You can also find the latest documentation for Pycraft here: [https://python-pycraft.readthedocs.io/en/pycraft-v0.9.3/](https://python-pycraft.readthedocs.io/en/latest/)

### Contents

*   PyOpenGL vs. ModernGL, *the change in game-engine wrappers*
*   Pycraft’s New Installer
*   News about Pycraft
*   Pycraft’s Ongoing Redesign
*   Final Words
*   Links and Credits

### PyOpenGL vs. ModernGL

*the change in game-engine wrappers*

Recently we made the move to start transitioning away from PyOpenGL in favour of ModernGL, in this section we explore why these changes were made.

I'd like to start by saying; we are still using the OpenGL API for the 3D graphics in Pycraft. Both PyOpenGL and ModernGL link a Python project to the C based API, allowing us to use OpenGL, we have looked into this at more depth in our previous article which you can find here for more information: [https://medium.com/@PycraftDev/how-we-are-making-a-video-game-in-python-4-9ec13e333944](https://medium.com/@PycraftDev/how-we-are-making-a-video-game-in-python-4-9ec13e333944)

Then you may be left wondering, why change from PyOpenGL to ModernGL if they do the same thing? Well PyOpenGL, what we used originally, was a very basic wrapper for OpenGL, allowing us to interact with the C API, but other than that everything else we as programmers behind Pycraft have to add in, and this is time consuming and also not very friendly to anyone starting out with 3D game development, we aim to make this project as detailed as we can but we are not a large team of developers that can spend large amounts of time on complex programs to create our game, it’d also make the program difficult to understand and modify for anyone not familiar with OpenGL and the documentation for OpenGL and the wrapper PyOpenGL is not very detailed or easy to find, the best site for OpenGL documentation we found was [https://learnopengl.com](https://learnopengl.com)/. This written in C and not Python so you would need to have a good understanding of both to be able to really understand the project we are making on.

In contrast ModernGL takes the same functions as PyOpenGL and simplifies most of it and makes it much more ‘Pythonic’ (essentially meaning it is in a similar form to the rest of the Python programming language) but ModernGL also has another stand out feature, lots of the complex OpenGL programming is already done for us, so instead of spending weeks tuning a Vertex Buffer Object in PyOpenGL, we can load an object (or ‘scene’ as it's referred to in ModernGL) on just a few lines! This heavily reduces the time spent programming and makes the project much more user friendly, even to new developers. You can find the project’s documentation here: [https://moderngl.readthedocs.io/en/latest/](https://moderngl.readthedocs.io/en/latest/) although it's important to note here the project is split into 2 libraries, both link closely but the second module (ModernGL-window) allows us to create a window which is optimised for OpenGL rendering, you can find that here: [https://moderngl-window.readthedocs.io/en/latest/index.html](https://moderngl-window.readthedocs.io/en/latest/index.html)

ModernGL also has another selling-point, its developers are working on the project actively and are open to feedback and improvements and you will likely get a response if you post a question there. ModernGL also comes with example programs too which work perfectly in our experience without any tweaks, although PyOpenGL has one improvement here, PyOpenGL is older and there is a lot more questions on Stack Overflow if you need help. Both libraries have their pros and cons, which I have briefly summarized in the image below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377488642/2EqKHl_U5.png)

Moderngl and PyOpenGL feature comparison

### Pycraft’s New Installer

The latest update to Pycraft, v0.9.4 is focused entirely to the new installer, we wanted to make downloading the project -and all its additional modules- easier, this is part of making the project more user-friendly. There was an installer planned for Pycraft right back to the first few months of development but this was never shared because it was a quick prototype and we wanted to spend more time working on getting the installer looking better and more professional as well as running lots of tests to make sure the new installer is functional on a range of hardware. Currently the installer has only been tested on Windows based Operating Systems and as a precaution the installer will not work on Linux, Apple or other Operating Systems because we don’t want to risk damage.

The installer is comprised of 4 sections;

*   The Installer Utility, this is complete (as of Pycraft v0.9.4–2 and above) and when run downloads the rest of Pycraft and its additional files and moves then to the user’s specified file location, during this process a number of checks are performed to make sure that everything is installed properly, this will change in future versions as more validation is done.
*   The Uninstaller Utility, is also complete (as of Pycraft v0.9.4–4), this allows you to customise the files the installer has added to your device, here you are given 3 options, remove everything that was downloaded and all saved data, remove only Pycraft (keeping the additional files which might be necessary for a developer to have) and remove everything downloaded but keep saved data, this will be called upon in the next section as part of the updating process which is the focus of the not yet completed Pycraft v0.9.4–5. The uninstaller is very basic currently removing everything in the ‘site-packages’ and ‘pycraft’ folders on your PC (It detects where your additional files where downloaded, they are stored under a file ‘site-packages’ in the Python folder), this is set to change leaving some files required by Python for example in the next update to Pycraft (v0.9.4–5)
*   The Update Utility has not yet been completed although extensively planned it uses the core fundamentals of both the uninstaller (to remove the previous install but keep save data) and the installer (which will automatically download the next version of Pycraft) to keep file sizes down.
*   Finally there is the Repair Utility, this will not be completed as part of the rest of the installer (in Pycraft v0.9.4) but will appear in a later version as we want to move development along and the repair section is the most complex and will likely take the most time, for now you can contact the Pycraft team by leaving a comment at the repository here: [https://github.com/PycraftDeveloper/Pycraft](https://github.com/PycraftDeveloper/Pycraft), or by contacting the lead developer here: [https://twitter.com/PycraftDev](https://twitter.com/PycraftDev) or by dropping a post on the discord server which you can find here: [https://discord.gg/h4jpcjJh](https://discord.gg/h4jpcjJh) (server invite)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377490418/beDOcJuvt.png)

This is the view of the installer after an install, prompting you with 3 options to customise your install

This will not replace any of the usual methods of downloading the project, from GitHub, SourceForge, Read-The-Docs or PyPi, but will be attached as part of each download should you want any help setting up. The PyPi command ‘pip install python-pycraft’ will still be functional (and is actually used by the installer), but to download the installer only a separate link/download code and advice will be given on the ReadME although that will only occur after the finalization of the entire Installer.

It is also important to note this does not affect (.exe) users of Pycraft as they cannot be installed through the installer unfortunately but are much easier to set-up.

### News about Pycraft

Aside from work on the installer there has also been a lot of work in a few other aspects of the project. Initially we used the ‘Inputs’ module to get a controller input for the project, this worked alright but had a few flaws, it would indefinitely listen for events and would not be controlled by the project as planned, it also was very resource heavy, even when it was not enabled in settings, the code for the controller detection mechanism would constantly make the project use in excess of 80% of its available CPU power meaning the rest of the project would be heavily restricted in performance. The Inputs module for Python is also getting old (so it's unlikely it would support new controllers) and has a few security issues; for example, it would be very easy for someone to take the project and make a keylogger. As a result, we have switched over to ‘PyJoyStick’ which is the exact opposite of all the things I mentioned above, its quicker, more secure (it cannot be used as a keylogger), much more controllable and customisable, much better at performance (at roughly 0.1 to 1% CPU usage) and is more modern.

Also, we have made a large tweak to the way music is loaded and played in Pycraft, the plan was always to have a different implementation for ‘music’ and ‘sound’ in Pycraft. Sound is intended to be ambient noise like birds tweeting or short sounds like a footstep, in the current solution they are loaded entirely into memory before being played, this is fine because they are small and often don’t have large file sizes. In contrast music is a lot larger in file size and would be difficult to load entirely into memory when we want to use it, also this would make the project very memory intensive so instead we stream the music from a file, this works much better and only needs minor changes to the implementation, this change was made a few developer updates ago and is relatively minor but does make the project again more performant. There are still bugs here and they are being dealt with as soon as we can!

Here I think it is important to note that the project is currently in testing on a lot of different operating systems, the code is written in -and largely intended for use on- Windows based devices, but the project has always been written so that it should be compatible with other operating systems. Currently active testing is done on Windows, this is where most people will use the project and where most bugs are identified and fixed quickly, but also on a variety of Linux distributions. It is important to note here though that the install utility is only available on Windows for the time being, but that will change to support Linux at a later date. Apple devices unfortunately will not be actively tested and get support for Pycraft because it is not an OS, I have easy access to, although this may change if the number of issues and bugs identified on Apple increase.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377491882/0ifqP6Ndp.png)

Comparing performance with music on and off for different implementations of the music section.

### Pycraft’s Ongoing Redesign

Pycraft has been slowly undergoing a design change recently, making small changes through both the project its self and through its web-pages, the game has its self recently been updated slightly to change of the differences between light and dark mode so they are slightly different, the subheading of the GUI in light mode is slightly different to the normal font colour but we cannot do this in dark mode because we want to make the contrast high enough to be accessible to most users. Additionally, the project has had changes to improve compatibility with the new rounded corners of Windows 11 and the way font is rendered now in both the Credits and Benchmark GUIs is different, this allows us to improve them, like adding in extra information easily without having to completely re-do all of the lines below.

There have also been changes to some of the graphics for Pycraft, the project’s icon has now changed and so has the logo on the GitHub page, which has also seen a new contents page with links that take you to areas of the project at a glance. Importantly we have also changed the logo of the project from PNG to SVG so it scales now on devices better and also isn’t affected by the user’s theme. You can see these changes in the images attached below.

There are a lot more features that are also planned for the project, aimed mainly at the settings menu which will be completely re-designed using the same font rendering technique as other GUIs.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377493160/i4XhH1_CO.png)

The new icon for Pycraft (left) in comparison to the old icon for Pycraft (right)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377494348/cBih2OHBF.png)

The new logo for Pycraft (top) compared to the old logobelow, you can clearly see here the issues with the old logo…

### Final Words

Thank you for reading this article, I hope that you have liked this article and hopefully you have learned a few Pygame tricks and caught up will all things Pycraft. If you want to share this article that would be greatly appreciated!

Pycraft takes a lot of my time to develop, and a lot of work is but into Pycraft as a whole and writing these articles for you, as a result if you have any questions, suggestions or help feel free to contact us at [https://github.com/PycraftDeveloper/Pycraft,](https://github.com/PycraftDeveloper/Pycraft,) or by contacting the lead developer here: [https://twitter.com/PycraftDev](https://twitter.com/PycraftDev) or by dropping a post on the discord server which you can find here: [https://discord.gg/h4jpcjJh](https://discord.gg/h4jpcjJh) (server invite).

### Links and Credits

My Twitter Page: [https://twitter.com/PycraftDev](https://twitter.com/PycraftDev)

My GitHub page: [https://github.com/PycraftDeveloper](https://github.com/PycraftDeveloper)

My Dev.to page: [https://dev.to/pycraftdev](https://dev.to/pycraftdev)

Pycraft can be found here: [https://github.com/PycraftDeveloper/Pycraft](https://github.com/PycraftDeveloper/Pycraft)

Pycraft can be also found here: [https://pypi.org/project/Python-Pycraft/](https://pypi.org/project/Python-Pycraft/)

Pycraft’s documentation can be found here: [https://python-pycraft.readthedocs.io/en/latest/](https://python-pycraft.readthedocs.io/en/latest/)

#### With thanks to:

*   Thomas Jebbo (PycraftDeveloper) @ [www.github.com/PycraftDeveloper](http://www.github.com/PycraftDeveloper)
*   Count of Freshness Traversal @ [https://twitter.com/DmitryChunikhinn](https://twitter.com/DmitryChunikhinn)
*   Dogukan Demir (demirdogukan) @ [https://github.com/demirdogukan](https://github.com/demirdogukan)
*   Henri Post (HenryFBP) @ [https://github.com/HenryFBP](https://github.com/HenryFBP)
*   PyPi @ [www.pypi.org](http://www.pypi.org/)
*   PIL (Pillow or Python Imaging Library) @ [www.github.com/python-pillow/Pillow](http://www.github.com/python-pillow/Pillow)
*   Pygame @ [www.github.com/pygame/pygame](http://www.github.com/pygame/pygame)
*   Numpy @ [www.github.com/numpy/numpy](http://www.github.com/numpy/numpy)
*   PyAutoGUI @ [www.github.com/asweigart/pyautogui](http://www.github.com/asweigart/pyautogui)
*   Psutil @ [www.github.com/giampaolo/psutil](http://www.github.com/giampaolo/psutil)
*   PyWaveFront @ [www.github.com/pywavefront/PyWavefront](http://www.github.com/pywavefront/PyWavefront)
*   Py-CPUinfo @ [www.github.com/pytorch/cpuinfo](http://www.github.com/pytorch/cpuinfo)
*   GPUtil @ [www.github.com/anderskm/gputil](http://www.github.com/anderskm/gputil)
*   Moderngl @ [https://github.com/moderngl/moderngl](https://github.com/moderngl/moderngl)
*   Moderngl\_window @ [https://github.com/moderngl/moderngl-window](https://github.com/moderngl/moderngl-window)
*   PyJoystick @ [https://github.com/justengel/pyjoystick](https://github.com/justengel/pyjoystick)
*   Visual Studio Code @ code.visualstudio.com
*   And Twitter, Medium and Dev.to followers and community!

> This edition, and future editions of this series will not be including images of code, although this can look nicer and syntax highlighting can be helpful, having code written out here makes it friendly for those in the development community who have sight issues (like myself), or if you want to have this article read to you!

Please note links under the “With thanks to” are not moderated by me, they are safe links at the time of writing however I do not control the content on them.