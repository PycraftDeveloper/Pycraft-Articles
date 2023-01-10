# How We are Making a Video Game in Python #4

*Pycraft, a 3D open-source open-world video game made in python with Pygame, Numpy, PyOpenGL, ModernGL, PyAutoGUI, Py-CPUtil, GPUtil, PIL, PyWaveFront and Psutil!*

*This article, released at the start of every month will document what changes have been made to the project, what challenges we faced and how we overcame them and how and where you can install this project from. For anyone wondering, this is to accompany the regular updates on my twitter page (@PycraftDev on twitter: www.twitter.com/PycraftDev). Tom Jebbo, the lead developer and graphics designer and I hope you enjoy both playing the game and reading this article!*

*You can download Pycraft from my GitHub page (here: www.github.com/PycraftDeveloper/Pycraft) if you’re interested!*

### Contents

*   What is OpenGL?
*   What are we using in Pycraft?
*   The history of Pycraft
*   \- The past
*   \- The present
*   \- The Future
*   What is happening to Pycraft?
*   More news about Pycraft
*   Final Words
*   Links and Credits

### What is OpenGL?

OpenGL is a cross-platform graphics API (An API is a set of programs that can be used in lots of programs to add additional features) that allows for the creation and manipulation of 2D and 3D graphics. OpenGL allows for greater control over the GPU often bypassing the CPU on some instructions (For example ‘buffers’ which store data like faces and vertices in the GPU’s memory, these are used primarily to create VBOs, or Vertex Buffer Objects that can render large and complex shapes incredibly fast).

OpenGL was originally a project by Silicon Graphics, Inc. in 1991 however was released around a year later. Since 2006 it has been managed by a consortium called Khronos Group, that have pushed a series of updates to the API, extending its functionality and performance. Khronos Group also manage a lot of other popular APIs, both in and out of 3D graphics; these include: Vulkan, WebGL, OpenCL, and OpenGL ES.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377455336/SJc5NWb9q.png)

The full list, there are a few; how many do you know?

As a result of both its age and -at the time especially- cutting edge functionality it has been widely adopted for some time by the programming world, this is why I chose to use OpenGL in my project Pycraft.

### What are we using in Pycraft?

In Pycraft we are creating our game in Python, as such OpenGL will not work natively (to my knowledge), so we have to use a secondary module to be able to efficiently call the API, this is where ModernGL and PyOpenGL come into things, they are bindings that allow us to use OpenGL in python.

Initially we started off with PyOpenGL which is a very basic binding that didn’t add any additional features of its own (by that look at the example of Pygame, which I’ve talked about before; its a binding for the SDL API (we talked about this in this article: [https://medium.com/@PycraftDev/how-we-are-making-a-video-game-in-python-3-80ae07760168](https://medium.com/@PycraftDev/how-we-are-making-a-video-game-in-python-3-80ae07760168)) but in addition to this it also adds additional functionality that the SDL doesn’t have natively.)

This has some advantages and disadvantages, the main advantage is that to use the program we use the exact same syntax as we would in C, which is OpenGL’s native language, unfortunately this poses a few disadvantages, the structure of OpenGL in this way isn’t very pythonic (that is, follows the methods and style of coding often used in Python) and as such can cause some strange behaviour. In addition to this, the developer has only provided a basic documentation and a lot of the examples didn’t work (at least for me), and the programming community has really moved on from OpenGL now, the questions I'm looking at on Stack Overflow are a few years old at least, and almost all were written in C, so that was a language I had to learn too.

Enter ModernGL, this is another Python module that like PyOpenGL provides access to the OpenGL API, but this module has provided a middle layer between the raw OpenGL and Python, allowing it to simplify calls and handle the OpenGL environment much better. This has the advantage of being a fair bit faster and efficient, and much more Pythonic. It also has the advantage of being a relatively new module, so the developer is still active and able to help out (if we ask nicely!). Unfortunately, this means that most of my previous knowledge of OpenGL cannot be applied here and I am effectively starting again, but progress is really quick because of the better design, and as such I don’t think that changing modules like this will delay the project too much.

### The history of Pycraft

I think it’s time to share a bit about my back-story and the history of Pycraft

#### The past

Back at the start of October of 2016 I had just finished working on another large project, this was a video editor made entirely in python, with a large number of features that I myself found really useful including high quality video exports, audio manipulation, thumbnail makers, effects and timeline trimming, in-fact it’s what I’ve used to edit all the videos I’ve created on Pycraft. Anyway, since then I took a month off from programming, to rest and research what to do next, one day I came across PyOpenGL, and about a month later, on the 1st of November 2016 I began work on a game.

It started off as a simple 3D cube, within a few days I had rotations and translations so I could move easily around the object. Then I decided to start adding multiple cubes and eventually has a one cube thick layer of a randomly generated terrain like Minecraft, they were all wire meshes at the time (so just the outline of the cube, they were not filled). Then I decided to name the project Pycraft (‘Py’ from Python, and ‘craft’ from Minecraft).

However, I was unhappy about not being original and effectively attempting to copy Minecraft, so instead in November of 2018, I decided to take what I knew about cubes, OpenGL and textures and instead start loading (.obj) files, eventually deciding on a rudimentary terrain, using my knowledge of cubes to create a skybox and pin it to the player (a feature that broke for some considerable time).

From there, well things started going wrong, I have already got knowledge with OpenGL and I could not get some of the advanced features, like Vertex Buffer Objects to work, so I delayed the OpenGL side of game design, instead focusing my attempts on GUI design, this was the state of affairs right up to Pycraft v0.9, where I began to really focus on the OpenGL side of the game. My main issue with the OpenGL side of things was really a lack of power in Python.

Python is an interpreted language, unlike C which is compiled before running, meaning Python is considerably slower in some situations, and I could not get VBO’s to work, because I knew they would free up a lot of performance. Finally, around September of 2021, with help from a twitter follower, we cracked VBO’s in PyOpenGL and that was the only real issue at the time with the game engine, now things where much faster and everything was going well, we could really speed up development.

#### The Present

So, this is where we arrive at the issue that made me want to try ModernGL instead. I was really excited and happy at the large amount of progress that was being made on Pycraft, I decided to start trying to fix texture loading for both the map (so giving it a grassy texture instead of the green one you can see here:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377457523/8gZ3wn9yC.png)

The skybox can be seen in the background, and the map coloured green in front.

In addition to this change, I also attempted to start work on a HUD (or Heads Up Display), however once I had created a method of updating and loading a texture, assigning the texture to the plane we were using as causing issues. Either the texture would show as a solid colour, or it’d show as it’s meant to, but be really slow and not include the transparency effects properly.

So I decided to do a quick google on the subject to see if I could find a solution. I found lots of Stack Overflow articles on the subject, and Itried their fixes on my own program, but with no luck. So, then I decided to check out the tutorial I was using for the bulk of my knowledge, here: [https://learnopengl.com/](https://learnopengl.com/), but I could not find a tutorial there that would fix my issue, and googling other tutorials always gave either overcomplicated examples, or contrasting information.

A while ago I was looking into ModernGL, and found it really interesting, I had tried to use it and things had gone really well, and the plan was to eventually use it as a part of Pycraft. So that's what's happening now, we are migrating the entire Game Engine and graphics engine over to ModernGL. Implementing the same features in ModernGL is so much easier than PyOpenGL, and I have in about 6 hours of work, managed to create a skybox, get a window loaded with events, get a game loop working, created rotations around inside the skybox, and a fair bit more as well.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377460124/3-HWTHquL.png)

This is the new skybox in ModernGL, the images are rendered much clearer, however images aren't rendered in the right order yet, so excuse the strange edges!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377463292/ZPU66n3y7.png)

This is the old skybox implementation, you can see there is some work to do with transferring captions over to the new Engine, but the quality of the skybox looks much better on the new one above!

### The Future

So, naturally as a result of changing our OpenGL implementation, it will slow the release of Pycraft v0.9.3 somewhat, however all being well I don’t think that we will see a large delay in the bigger picture.

In order to get each update ready and released, so much time is spent testing and debugging strange OpenGL syntax, so if we can reduce this somewhat with the new system then that will improve the speed, I can release some updates.

Pycraft v0.9.3 was originally going to feature the implementation of a new weather system and day and night cycles, and that will still happen, but the new plan is to delay everything by 0.0.1 of an update (so the original Pycraft v0.9.3 update becomes v0.9.4 ext.) Aside from that I’ll be trying to stick to implementing the features of the update as mentioned on the timeline found both on a previous medium article here: [https://medium.com/@PycraftDev/how-we-are-making-a-video-game-in-python-2-547b504bbd67](https://medium.com/@PycraftDev/how-we-are-making-a-video-game-in-python-2-547b504bbd67) or on my GitHub page here: [https://github.com/PycraftDeveloper/Pycraft](https://github.com/PycraftDeveloper/Pycraft). Apologies about the confusion over the change in updates!

### More news about Pycraft

As you now know, there have been a lot of changes lately to Pycraft, however outside of the main change, I’d like to mention a few small tweaks to both Pycraft that will be coming in v0.9.3, as well as some tweaks to the structure of my content!

So, the skybox in Pycraft v0.9.3 no longer has the borders that have been seen in older versions, which you can see below, it's a small change, but one that really adds to the immersiveness of the game.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377466400/emG1UI8Vx.png)

This is the older version of Pycraft v0.9.3, before the tweak, see the big line going down the centre of the screen?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377469463/FYJR12Uu5.png)

No more lines! (This is the newer version, so new in-fact the skybox hasn’t been arranged properly, this is an easy fix that will be made!)

In addition to this, there have been more minor in game tweaks and bug fixes, a notable one will be issues around the new load-screen. (There was more progress to announce, however the redesign of the game engine meant we are rolling back a few at present, but they will be added before the update goes live!)

The issues with PyPi and the strange character rendering has also now been fixed!

I’d also announce the completion of the reprogramming of the loading part of the game engine, now this process is as parallelised as possible to improve both load times and performance, as the previous system would tell the game to update after a percentage of the files has been loaded and processed, and this is very fast meaning we would often easily exceed the user’s set FPS, this new feature also means we don’t wait around for the display to refresh, so load times have been significantly reduced:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377471167/cQDlN34F_.png)

A bar chart comparing the old load times to the new system, much faster!

Finally, I’d like to add that these medium articles will be shared with the my dev.to profile here: [https://dev.to/pycraftdev](https://dev.to/pycraftdev) weekly, in addition to either two or three updates during the week on the progress of Pycraft (once during the working week, then one for each day of the weekend which have off if I get lots done!)

### Final Words

Thank you for reading this article, I hope that you have liked this article and hopefully you have learned a few Pygame tricks and caught up will all things Pycraft. If you want to share this article that would be greatly appreciated!

Pycraft takes a lot of my time to develop, and a lot of work is but into Pycraft as a whole and writing these articles for you, as a result if you have any questions feel free to message me here on twitter ([https://twitter.com/PycraftDev](https://twitter.com/PycraftDev)) or drop me an email at ([ThomasJebbo@gmail.com](mailto:ThomasJebbo@gmail.com)).

I’m regularly on Twitter so feel free to message me with any questions you may have on the project, for feel free to let me know of any typos and mistakes!

Thank you for reading this article, that’s really appreciated. And remember; anyone can learn to code. And games like my own, which I’m still working on, from a programming point of view are possible for everyone!

### Links and Credits

My Twitter Page: [https://twitter.com/PycraftDev](https://twitter.com/PycraftDev)  
My GitHub page: [https://github.com/PycraftDeveloper](https://github.com/PycraftDeveloper)  
My Dev.to page: [https://dev.to/pycraftdev](https://dev.to/pycraftdev)  
Pycraft can be found here: [https://github.com/PycraftDeveloper/Pycraft](https://github.com/PycraftDeveloper/Pycraft)  
Pycraft can be also found here: [https://pypi.org/project/Python-Pycraft](https://pypi.org/project/Python-Pycraft/)/

I would like to also mention that my website is getting some attention and will be coming soon!

#### With thanks to:

*   Pygame ([www.pygame.org](http://www.pygame.org))
*   Numpy (numpy.org)
*   Pillow (PIL) (python-pillow.org)
*   Python ([www.python.org](http://www.python.org))
*   Tkinter
*   PyAutoGUI (pyautogui.readthedocs.io/en/latest)
*   Psutil (psutil.readthedocs.io/en/latest)
*   GitHub (github.com)
*   PyOpenGL (PyOpenGL — The Python OpenGL Binding (sourceforge.net))
*   ModernGL ([https://github.com/moderngl/moderngl](https://github.com/moderngl/moderngl))
*   *GPUtil (*https://github.com/anderskm/gputil)
*   *PyWaveFront (*https://github.com/pywavefront/PyWavefront)
*   OpenGL ([www.opengl.org](http://www.opengl.org))
*   YouTube
*   Windows
*   Visual Studio Code (code.visualstudio.com),
*   Microsoft
*   And My amazing Twitter, Medium and Dev.to followers and community!

> This edition, and future editions of this series will not be including images of code, although this can look nicer and syntax highlighting can be helpful, having code written out here makes it friendly for those in the development community who have sight issues (like myself), or if you want to have this article read to you!

*Please note links under the “With thanks to” are not moderated by me, they are safe links at the time of writing however I do not control the content on them.*

*This article was written 8 days in advance, so there may be some out-of-date information here, although I try my best to keep this as accurate as I can to the day of release!*