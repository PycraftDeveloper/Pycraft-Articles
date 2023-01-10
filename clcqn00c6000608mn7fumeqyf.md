# How We are Making a Video Game in Python #8

Pycraft’s banner image

*Pycraft, the 3D open-source open-world video game made in Python!*

*This article, released roughly once a month will document what changes have been made to the project, what challenges we faced and how we overcame them and provides a more detailed look at future features planned for Pycraft.*

*These articles are also shared to our Dev (*dev.to/pycraftdev*) profile and accompany the regular updates we post on our Twitter (*twitter.com/PycraftDev*) account. This article is written by Tom Jebbo, the lead developer and graphics designer and I hope you enjoy both using the project and reading this article!*

*   You can find the latest release of Pycraft (v0.9.5) here: [https://github.com/PycraftDeveloper/Pycraft](https://github.com/PycraftDeveloper/Pycraft)
*   You can also find the latest documentation for Pycraft here: [https://python-pycraft.readthedocs.io/en/latest/](https://python-pycraft.readthedocs.io/en/latest/)
*   You can also find Pycraft on SourceForge: [https://sourceforge.net/projects/python-pycraft/](https://sourceforge.net/projects/python-pycraft/)

### Contents

*   An Introduction to Cloud Design
*   Generating The Right Structure
*   Time For a Guide
*   Time For Some Colour
*   Let’s Look at What Challenges We Faced
*   Enough Of the Negatives, Future Changes coming to Pycraft
*   Final Words
*   Links and Credits

### An Introduction to Cloud Design

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377899821/DJeg7AP3u.jpeg)

A photograph taken looking straight up at the sky

If I were to show you the image above, most people would be able to confidently tell you that it is a photograph of some clouds, if you were feeling more technically inclined you might also be able to identify it as a ‘fair weather’ cumulus or *cumulus humilis*. Regardless of how well you can identify them, we can all identify them with confidence as clouds, but did you ever stop to consider, what defines a cloud? With that question in your head, if I were to show you the two images below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377901023/wFRD9KZAZ.jpeg)

2/3 images of clouds, you can see that this is very different to the one we showed above

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377902158/q3rRaYNQ-.jpeg)

3/3 images of clouds, higher cloud in the sky made up of ice crystals instead of rain drops

Chances are you will be able to tell me that they are also clouds, but they have very different colours, transparencies, depth, height, structure and patterns. The point I am trying to bring across here is that we all know a cloud when we see one, but how many of us have stopped to try and understand what tells us that?

If you hadn’t guessed already this article for Pycraft is all about clouds and how we go about making them in Pycraft, it’s one of the most recent features added into Pycraft and makes a big difference.

### Generating The Right Structure

To start with, before we look at any fancy texturing or colouring to the clouds themselves, we need to consider especially for the first image we showed here, how to generate that style of pattern and save it as a heightmap (an image that is used in Pycraft or any other rendering engine to alter the heights of different positions on an object). To do this we will be generating noise. Noise is a computer-generated pattern that can follow lots of different rules/styles. By far the most common form of noise is random noise which you may have already heard of, it looks a bit like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377904280/8Eykh4zFA.png)

This is an example of random white noise, it’s called white noise as in audio it is a combination of lots of different frequencies of sound which is similar to how white light is a combination of all the other visible wavelengths of light (red, orange, yellow, ext.)

But this is clearly not going to work in Pycraft for clouds, there is simply no pattern, clouds would be a jumbled mess. In order to this we need to change the way we generate images.

For this example, we made a program in Python that would scan from top-left to bottom-right and fill each pixel with a random monochromatic colour (any greyscale colour), but to generate noise with any form of pattern we would need to consider adjacent pixels to calculate the colour of each pixel, this is comparatively easy on the same row, but gets much more difficult and computationally expensive when considering pixels on diagonals and above or below.

Instead, and this is the approach we took in Pycraft, we compared the pattern we see in clouds to the pattern we see in different styles of noise, as shown in this table:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377906063/vAUk5kNOy.png)

Different examples of noise

Gradient noise is similar to Perlin noise, in fact they are both closely linked, but the pattern made by gradient noise is too rough for use as a heightmap for clouds in Pycraft.

Perlin noise is perfect, but in the same way so is value noise, both making a clear pattern that is both natural looking and not too harsh like gradient noise, the only reason we picked Perlin noise to use is that it was easier to implement into Pycraft, although as we will see this could potentially change.

Simplex noise is very different to the other types of noise we have seen so far, this would not look good in Pycraft for clouds, but may be better than Perlin noise for use in adding a bit of height to water.

Worley noise is again not suitable for clouds in Pycraft, its pattern is very different to what we are trying to achieve but, like simplex noise, may have other uses, for example in adding a rain drop pattern to the ground in Pycraft or for texturing rocks!

There are lots more different types of noise than we have seen here, and we looked at lots of different types, but Perlin noise was the easiest to add and looked the most natural, so we started to see if we could generate this in Python and add it to Pycraft. The end result can be seen below, this has been taken out of Pycraft having been generated when the game launches (on some installs of Python).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377908247/s3-SrISlI.png)

A much larger example of Perlin noise, which is used in Pycraft

### Time For a Guide

The image above is generated by Pycraft and is used in the generation of clouds. This gives us the distribution of clouds similar to what we have seen in the first image we showed in this article. For most games we can now colour this more like what you would expect clouds to look like and simply use the image its self to represent clouds.

However, Pycraft isn’t just about following the trends of other games (or for that matter sticking to an easy solution), and we wanted to make the design both 3D and as realistic as possible. Another point of Pycraft is to try out features and experiment, to hopefully understand better why game developers often leave it as a 2D image instead of doing what we did in Pycraft, and we will get onto the limitations in a bit, but for now let’s see what we did.

To start with we used the ‘noise’ module, which you can find here: [pypi.org/project/noise/](https://medium.com/p/d21ab19b00a0/pypi.org/project/noise/), this generates an array of values that represent Perlin noise (represented by the variable ‘array’ in the example below), this we can then convert to an image through the use of Matplotlib, Numpy and PIL with this line of code:

from PIL import Image  
import numpy  
from matplotlib import cm

image = Image.fromarray(numpy.uint8(cm.gist\_earth(array)\*255))

From there we can save the image file with this line of code:

image.save(PATH)

All this code does so far is convert an array of generated Perlin noise into an image file that can then be saved. From there we need to load the newly created file in ModernGL as a heightmap. To do this we simply use the line of code:

self.cloud\_texture = self.load\_texture\_2d(PATH)

Then from there we enter ‘self.cloud\_texture’ as a heightmap to our GLSL program called ‘clouds.glsl’.

This is great, we have an image file we can use to displace vertexes to create our cloud style, but we don’t have any surface to displace yet, so nothing will happen.

To do this we use the function ‘ComputeCloudModel’ in Pycraft, which generates the vertexes and indexes for a flat plane (vertexes are the points in 3D space and indexes tells the rendering engine how they connect together). This plane is square and is scaled so that it has a slightly larger size than the skysphere, which we initially used to crop the clouds as shown below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377910276/uU_AT9dul.png)

A diagram showing the skysphere (the circle), the plane with clouds on it (the square) and the area they intersect each other (in red)

In later revisions we added transparency to the clouds and we could no-longer use the skysphere to crop out the clouds, instead we fade clouds out as they get further away towards the edge of the skysphere, along with all other objects that appear in the 3D scene, significantly improving the look and effectively adding fog to the game.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377911581/Vw4pHxfNH.png)

This mock up in blender shows what clouds look like without any shading, similar to what we had in Pycraft and similar to what you would have so far if you followed this guide!

Below is a revised look at the diagram above, this time showing fog in Pycraft, the red areas are not visible and the white areas in the circle are, the gradient shows the fade out between what is and isn’t visible, different weather types in Pycraft have different fade distances, some will start/end closer to the player to change the dynamic, as well as adjusting the area that fades out:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377913001/biCUMJBoJU.png)

The different levels of fog in Pycraft, you can see that the image on the left (<) has a much shorter fade distance to the one on the right (>).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377914258/DFJ2AdBVr.png)

This is an example of fog in Pycraft on a clear day

### Time For Some Colour

So, we have now looked at how to structure the clouds, how to add depth to the clouds and how to fade them in and out, but there are a few problems still, firstly the clouds could do with a bit of colour, then they could also do with a bit of transparency themselves, and finally we need to get rid of the rest of the plain that appears flat where there is no noise.

To start with we colour the clouds based on depth, the lower the cloud reaches the darker the cloud gets coloured, creating a gradient style effect, the lowest point is determined by the lowest value generated in the array when we made the Perlin noise. The top colour gets a bit more complex, to start with it was purely white, but that means that at night the sky is covered in clouds that seem to think it is the middle of the day, this won’t do, so to fix this we make a fundamental change to the entire game.

In any 3D scene there is the foreground and background, the background to any game is masked by the skybox or skysphere, but behind that its typically just a black void (as shown below). In Pycraft we decided that to correct the colouring to the top of the cloud we would change the colour of that dark void depending on the time of day and weather, this alone has no effect, but we can add that colour as an input into the GLSL programme that we use to position and shade the clouds, ‘clouds.glsl’, and this makes the clouds base colour change according to the time of day and weather. The main reason however that we change the colouring of the ‘void’ is so that we can add transparency to the skysphere later on.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377915625/jJn-ttra8.png)

The ‘blackness’ you see here is simply void or empty space were nothing is rendered

At this moment in time, we now have a plane that has colour and depth, but is still fundamentally a solid white square when seen from below, so to change this, and to improve on efficiency, any areas of cloud that are at the ‘base’ level (which are therefore the areas in the heightmap rendered black) we discard them. This immediately changes the solid plane into having patches of cloud.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377916896/Bjsd1oRlP.png)

In this render from Blender, you can see how much of a difference it makes to discard some of the plane, this is the same random noise as was shown in the blender example earlier (albeit a bit closer up) and with some areas removed based on height

Additionally, the higher the vertex is in the cloud the more transparent it is, this means that we can better blend between the areas we can see and the bits we simply cut out, also the alpha transparency of the clouds changes significantly based on what type of weather it is, with clouds on a sunny day getting transparency and most other times they have no transparency as the clouds are thicker to present the idea that there may be rain coming.

Now that we have cut out the areas of cloud that we don’t want we can see the skysphere behind it, this is excellent and on a clear day this effect remains virtually unchanged, however when it is rainy it still looks like a cloudy day, only the clouds look more ominous and there is rain. To fix this we must use an earlier feature, remember how we change the colour of the void behind the skysphere in Pycraft? Well now we apply transparency to the whole skysphere when the weather isn’t sunny and we can start to differentiate different weather events by darkening the entire sky.

Suddenly this creates the intended effect and we get to finally show you a review of what clouds look like in Pycraft:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377918446/7c4DBuMZC.png)

This is the finished product, this is considered light rain so the sky doesn’t get too much darker

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377920110/tOppubueN.png)

This is considered heavier rain in Pycraft, but this is still not the worst weather in Pycraft

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377921709/PU-aW8JLn.png)

This is a thunderstorm in Pycraft, to see a thunderstorm at night in Pycraft check this out: [www.youtube.com/watch?v=-cg6bbL2AFg](http://www.youtube.com/watch?v=-cg6bbL2AFg)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377923646/SK6wkG13B.png)

This is considered a sunny day in Pycraft with only a little bit of cloud

### Let’s Look at What Challenges We Faced

One of the biggest challenges we faced when working on clouds in Pycraft was how to generate Perlin noise. There aren’t many options and after settling on the noise module we quickly began to regret our decision. To start with it can be tricky to install, requiring other 3rd party software, that means that it wouldn’t be compatible with the installer and not very user friendly. This is one of the key reasons we switched away from PyOpenGL to ModernGL, because it was much easier to install. Additionally, it was last updated in 2015 and there looks to be no future updates to the library, this is particularly disappointing as we want to make sure that we use modules that are seeking active development where possible to support new features and hardware. And finally, because the module has seen no recent updates it is buggy, for example it works on 43.5% of all computers we have tested on (remember we do not collect any data inside of Pycraft that is later sent anywhere so this is based on our testing of 30 machines from a variety of ages) so we have coded a work around into Pycraft to use cached data if the module doesn’t work, but this is only a temporary solution for now.

Additionally cloud generation isn’t infinite, it’s not something we thought was easily achievable (considering we have to convert the data into an image file this means it would potentially take up a lot of space and was also computationally more expensive to achieve) although we are going to review that in a later update. This means that the clouds are, like the skysphere, fixed to the location of the player. To provide a bit of movement we move the cloud plane in a large circle very slowly around the players position on the x and z axis, but this is again something that we would hope to later fix by making the cloud generation infinite.

Finally, adding clouds into Pycraft meant other features in the game engine now also need to be tweaked, mainly shadow mapping. Currently shadow mapping is easy to implement on objects we load from a file, for example trees, terrain and entities. However, the clouds in Pycraft are created not through a file but through a plane generated as the game starts up. This may not seem like a problem, but the way these are ‘seen’ by ModernGL is very different, which means the same program won’t work for both, so a different solution is required there to get clouds to both cast shadows on themselves (like the terrain does) and also on the terrain and things below.

One final problem is the lack of detail, the clouds in Pycraft aren't really 3D, if anything they are closer to ‘2.5D’, they have ‘x’ and ‘y’ values based on their position on the plane, but their depth value is that value in the heightmap texture we just looked at generating. This means that when viewing the clouds from below or above they look fine, and also at an angle they don’t look terrible, but they have no detail on one axis. The best way to demonstrate this is to elongate a 2D shape to make a prism, it has no detail on one axis. If I take a circle to be my 2D shape and I stretched it out on a 3rd axis (to make a 3D object), you get a cylinder with no extra detail on that 3rd axis than was present in the 2 axes, to make this example properly 3D you would end up with a sphere. This means that the sides of the clouds lack any 3D detail. The reason for this is we are generating 2D Perlin noise, a 2D heightmap and a 2D object to apply the heightmap to. To make the clouds go from ‘2.5D’ to 3D we would need to change all those previous objects to 3D and we have seen that already Perlin noise is difficult enough to generate and adding in another dimension would make it more computationally expensive and lead to larger files and load times.

### Enough Of the Negatives, Future Changes coming to Pycraft

So, as you can see the current design of clouds in Pycraft isn’t flawless, it’s certainly a good start, but at this moment in time we need to change our approach to generating Perlin noise before we can act on those changes. Perlin noise generation will therefore be changes in Pycraft v0.9.6–0 if a suitable module can be found. If so, or even if there isn’t, there are already safeguards in place to make sure that even with the bad module Pycraft should work alright. As with every feature in Pycraft it goes through cycles of development. For example, the home screen for Pycraft has been revised 3 times in the last 3 years and seen many changes to both the design and improvement. The credits menu has also seen similar changes, but we have perfected the structure of that now and it won’t see any major changes other than regular updates to keep the credits up-to-date.

This nicely links into the goals of Pycraft v0.9.6, which have been overshadowed somewhat by the settings redesign. So let’s start there; settings in Pycraft is about to change in a big way. No longer will we have to manually add in complex hit boxes, text and other items to the menu, or search through the unordered mess, soon there will be a categorised settings menu that will, like the credit’s menu, be arranged based on a pre-determined order that will make it much easier to tweak settings and add in future ones.

The details of the settings menu will be looked at closely in the article for August so I won’t give any spoilers, but it’s not the only change coming. The best way to showcase this is to create a timeline:

Pycraft v0.9.6–0: This update will make improvements based on our experience releasing Pycraft v0.9.5 and fixes and improves how resources are checked. This update also will see better bug fixes for bugs that were identified during the release of Pycraft v0.9.5 and quickly patched and part of that will be to hopefully switch to a better way of generating Perlin noise.

Pycraft v0.9.6–1: This update will tweak how the program starts up, rearranging some sections so that it makes more sense. This update will also see changes to how files are saved and loaded with a better mechanism for fixing corrupted saves. This update will also add a standard for structuring variable names and fix some of the more commonly used ones. This update will see a fundamental change to how the jump animation works.

Pycraft v0.9.6–2: This is one of the more significant changes to Pycraft v0.9.6, the redesign of the settings menu, improving performance, ease of use, ease of update and general design.

Pycraft v0.9.6–2.5: This is a smaller update that focuses on the settings menu, this will add in lots of new settings to fill out the new categories and to provide greater customisation. This has the potential to take a while and/or introduce bugs which is why its split into 2 parts.

Pycraft v0.9.6–3: This will be a smaller update, potentially fixing bugs from previous bug fixes, tweaking some behaviours and potentially fixing the issues with music that are evident in Pycraft at the moment.

Pycraft v0.9.6–4: This will completely change the structure of the benchmarking process, allowing users to better customise what they want to test, between a short CPU or GPU stress test, a longer more gaming focused benchmark to give closer to real-world values and hardware information and compatibility.

Pycraft v0.9.6–4.5: This will see significant changes to how the benchmark section of Pycraft displays results, seeking to simplify the process, bring in benchmark saving and also methods to export your data.

Pycraft v0.9.6–5: This will likely be again a smaller bug-fix focused update.

Pycraft v0.9.6–6: This will introduce the idea of save files and different profiles into Pycraft, you will get 2 saves and 3 auto saves per profile. You have 2 profiles, so you can run different instances of the game. For now, this will be to allow for testing in an up-and-coming testing focused environment as well as in the scene we have now to test changes to the game engine. Later on, these will be split into a ‘normal’ and ‘harder’ mode so you can choose between different difficulty levels (or potentially this might be something you can change in settings for each profile, it’s too early to tell at the moment)

Pycraft v0.9.6–7: This is the final stretch towards the end of Pycraft v0.9.6’s development at the current plans , this isn’t set in stone and we should be approaching this target as we get close to December and the end of the year.

### Final Words

Thank you for reading this article, I hope that you have liked this article and hopefully you have caught up will all things Pycraft. If you want to share this article that would be greatly appreciated!

Pycraft takes a lot of my time to develop, and a lot of work is but into Pycraft as a whole and writing these articles for you, as a result if you have any questions, suggestions or help; feel free to contact us at [https://github.com/PycraftDeveloper/Pycraft,](https://github.com/PycraftDeveloper/Pycraft,) or by contacting the lead developer here: [https://twitter.com/PycraftDev](https://twitter.com/PycraftDev) or by dropping a post on the discord server which you can find here: [https://discord.gg/h4jpcjJh](https://discord.gg/h4jpcjJh) (server invite).

### Links and Credits

*   My Twitter Page: [https://twitter.com/PycraftDev](https://twitter.com/PycraftDev)
*   My GitHub page: [https://github.com/PycraftDeveloper](https://github.com/PycraftDeveloper)
*   My Dev.to page: [https://dev.to/pycraftdev](https://dev.to/pycraftdev)
*   Pycraft can be found here: [https://github.com/PycraftDeveloper/Pycraft](https://github.com/PycraftDeveloper/Pycraft)
*   Pycraft can also be found here: [https://pypi.org/project/Python-Pycraft/](https://pypi.org/project/Python-Pycraft/)
*   Pycraft’s documentation can be found here: [https://python-pycraft.readthedocs.io/en/latest/](https://python-pycraft.readthedocs.io/en/latest/)

#### With thanks to:

*   Thomas Jebbo (PycraftDeveloper) @ [www.github.com/PycraftDeveloper](http://www.github.com/PycraftDeveloper)
*   Count of Freshness Traversal @ [www.twitter.com/DmitryChunikhin](http://www.twitter.com/DmitryChunikhin)
*   Dogukan Demir (demirdogukan) @ [www.github.com/demirdogukan](http://www.github.com/demirdogukan)
*   Henri Post (HenryFBP) @ [www.github.com/HenryFBP](http://www.github.com/HenryFBP)
*   PyPi @ [www.pypi.org](http://www.pypi.org)
*   PIL (Pillow or Python Imaging Library) @ [www.github.com/python-pillow/Pillow](http://www.github.com/python-pillow/Pillow)
*   Pygame @ [www.github.com/pygame/pygame](http://www.github.com/pygame/pygame)
*   Numpy @ [www.github.com/numpy/numpy](http://www.github.com/numpy/numpy)
*   PyAutoGUI @ [www.github.com/asweigart/pyautogui](http://www.github.com/asweigart/pyautogui)
*   Psutil @ [www.github.com/giampaolo/psutil](http://www.github.com/giampaolo/psutil)
*   PyWaveFront @ [www.github.com/pywavefront/PyWavefront](http://www.github.com/pywavefront/PyWavefront)
*   Py-CPUinfo @ [www.github.com/pytorch/cpuinfo](http://www.github.com/pytorch/cpuinfo)
*   GPUtil @ [www.github.com/anderskm/gputil](http://www.github.com/anderskm/gputil)
*   Tabulate @ [www.github.com/p-ranav/tabulate](http://www.github.com/p-ranav/tabulate)
*   Moderngl @ [www.github.com/moderngl/moderngl](http://www.github.com/moderngl/moderngl)
*   Moderngl\_window @ [www.github.com/moderngl/moderngl-window](http://www.github.com/moderngl/moderngl-window)
*   PyJoystick @ [www.github.com/justengel/pyjoystick](http://www.github.com/justengel/pyjoystick)
*   Noise @ [www.github.com/caseman/noise](http://www.github.com/caseman/noise)
*   Matplotlib @ [www.github.com/matplotlib/matplotlib](http://www.github.com/matplotlib/matplotlib)
*   FreeSound: — Erokia’s “ambient wave compilation” @ [www.freesound.org/s/473545](http://www.freesound.org/s/473545)
*   FreeSound: — Soundholder’s “ambient meadow near forest” @ [www.freesound.org/s/425368](http://www.freesound.org/s/425368)
*   FreeSound: — monte32’s “Footsteps\_6\_Dirt\_shoe” @ [www.freesound.org/people/monte32/sounds/353799](http://www.freesound.org/people/monte32/sounds/353799)
*   Freesound: — Straget’s ‘Thunder’ @ [www.freesound.org/people/straget/sounds/527664/](http://www.freesound.org/people/straget/sounds/527664/)
*   Freesound: — FlatHill’s ‘Rain and Thunder 4’ @ [www.freesound.org/people/FlatHill/sounds/237729/](http://www.freesound.org/people/FlatHill/sounds/237729/)
*   Freesound: — BlueDelta’s ‘Heavy Thunder Strike — no Rain — QUADRO’ @ — [www.freesound.org/people/BlueDelta/sounds/446753/](http://www.freesound.org/people/BlueDelta/sounds/446753/)
*   Freesound: — Justkiddink’s ‘Thunder » Dry thunder1’ @ [www.freesound.org/people/juskiddink/sounds/101933/](http://www.freesound.org/people/juskiddink/sounds/101933/)
*   Freesound: — Netaj’s ‘Thunder’ @ [www.freesound.org/people/netaj/sounds/193170/](http://www.freesound.org/people/netaj/sounds/193170/)
*   Freesound: — Nimlos’ ‘Thunders » Rain Thunder’ @ [www.freesound.org/people/Nimlos/sounds/359151/](http://www.freesound.org/people/Nimlos/sounds/359151/)
*   Freesound: — Kangaroovindaloo’s ‘Thunder Clap’ @ [www.freesound.org/people/kangaroovindaloo/sounds/585077/](http://www.freesound.org/people/kangaroovindaloo/sounds/585077/)
*   Freesound: — Laribum’s ‘Thunder » thunder\_01’ @ [www.freesound.org/people/laribum/sounds/353025/](http://www.freesound.org/people/laribum/sounds/353025/)
*   Freesound: — Jmbphilmes’s ‘Rain » Rain light 2 (rural)’ @ [www.freesound.org/people/jmbphilmes/sounds/200273/](http://www.freesound.org/people/jmbphilmes/sounds/200273/)

Please note links under the “With thanks to” are not moderated by me, they are safe links at the time of writing however I do not control the content on them!