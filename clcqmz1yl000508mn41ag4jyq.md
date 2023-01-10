# How We are Making a Video Game in Python #7

Pycraft’s banner image

*Pycraft, a 3D open-source open-world video game made in Python!*

*This article, released roughly once a month will document what changes have been made to the project, what challenges we faced and how we overcame them and how and where you can install this project from.*

*For anyone wondering, this is to accompany the regular updates on my Twitter page (@PycraftDev on twitter:* [*www.twitter.com/PycraftDev)*](http://www.twitter.com/PycraftDev%29) *which are now also shared to my Dev profile here:* [https://dev.to/pycraftdev](https://dev.to/pycraftdev)[*.*](http://www.twitter.com/PycraftDev%29.) *This article is written by Tom Jebbo, the lead developer and graphics designer and I hope you enjoy both using the project and reading this article!*

· You can find the latest release of Pycraft (v0.9.4) here: [https://github.com/PycraftDeveloper/Pycraft](https://github.com/PycraftDeveloper/Pycraft)

· You can find the latest developer preview of Pycraft (v0.9.5–2) here: [https://github.com/PycraftDeveloper/Pycraft/tree/Pycraft-v0.9.5-2](https://github.com/PycraftDeveloper/Pycraft/tree/Pycraft-v0.9.5-2)

· You can also find the latest documentation for Pycraft here: [https://python-pycraft.readthedocs.io/en/latest/](https://python-pycraft.readthedocs.io/en/latest/)

### Contents

· An Introduction to GLSL

· Shaders in Pycraft

· Shadow Mapping in Pycraft

· Future Game Engine Improvements to Pycraft

· Final Words

· Links and Credits

### An Introduction to GLSL

OpenGL is a graphics specification that combines languages like C# and Java and now Python with OpenGL’s own language, called GLSL (openGL Shading Language) that runs on your GPU and performs computations over large data sets — like for example a 3D model.

GLSL is a compiled language and we must use some special syntax that isn’t seen in Python, the language Pycraft is commonly programmed in. GLSL code is run only when we start rendering objects to the display.

In ModernGL, the module we are using in Python for manipulating an OpenGL environment, we use the `.render()`syntax to tell the GPU to render something to the screen, for example we could load an object from a file, let’s say a bike, then saying `$bike.render()` will render that object to the OpenGL environment. However, we can specify a GLSL programme to use when we render for example let’s say we had a GLSL programme to colour the bike red, and this is called `red_shader` and would call this GLSL programme when we render like this: `$bike.render(red_shader)`.

The `in`syntax in GLSL is what we can use to interact with the GLSL code from our language. This is how we send and update parameters in our GLSL object that change the result. For example, this could be changing the red colour of a vertex by specifying a variable in GLSL like `in float color`which you could then go on-to assign to each vertex you are currently rendering, for example taking our `red_shader`from earlier, we could then specify the colour value for red, remember it would need to be between 0 and 1 instead of the usual 0 to 255 for the rest of Pycraft.

This is a very simple demonstration, and we will continue to reference back to this as we go, and then look at some GLSL code so we have a good understanding of GLSL, which is applicable to any application that uses OpenGL and GLSL, not just Pycraft, although any code we place a ‘$’ symbol before is syntax specific to Python and ModernGL.

The `uniform` syntax in GLSL is very similar to the `in`syntax, but this data cannot be modified or changed when the GLSL programme is rendering. This is very similar to a constant variable that we never change once it is set when the programme is running. However, in GLSL, when the programme is not running and waiting for the next render call, we can, and must specify what data we should store in a uniform variable. Continuing with our example from earlier we could also give the GLSL programme the series of points that make up our bike model, this does not change when we render the object, but could potentially change when we are not rendering.

To do this in ModernGL, we use the `$write()` syntax after the name of the programme with the name of the variable you are writing to defined in square brackets, similar to a dictionary in Python, with our example from earlier, this would look like: `$red_shader["color"].write(1)`

This code takes what we learned with the `in`syntax in GLSL and shows how we could update or set the data stored in that variable as our Python programme runs. This is the exact same for the `uniform`syntax too, although be aware that GLSL is compiled and therefore we must specify the data type it is expecting and then use that data type when we specify values, so if we tell GLSL the value for colour should be a `float`, and we enter a matrix or Boolean, this will cause the programme to crash.

So now we have looked at how to enter data into a GLSL programme, now let’s look at how to get the result back out again, although we cannot return the data back to the Python programme, we are running the GLSL programme from, instead the `out` syntax tells GLSL that this is the result it is working towards and this is used to render the object with a specific property. If we do not specify an output for the programme then when the GLSL code compiles it will not run any of the programme because it knows the data it is processing isn’t used to save on resources.

So, we have now looked at the ins and outs of GLSL, and we should now take a small diversion to talk about GLSL’s structure. GLSL is split into two sections, a vertex shader and a fragment shader. The vertex shader is used to manipulate the object its self, for example moving it around, as the name suggests it works with the object’s vertices. The fragment shader works on colouring or texturing materials properly, these details are called fragments and refer to the result we can see onscreen. Often these programmes are linked together, but sometimes we many only specify a fragment or vertex shader depending on its purpose.

Lining this back to our example from earlier, the model of the bike would be part of the vertex shader, whilst the colour input would be part of the fragment shader.

Now lets quickly go over the main ‘compute’ section of GLSL, there is one main structure we need to look into the `main()` syntax. This is where most of the GLSL compute happens, there is one for both the vertex and fragment shader, they take the values and constants and, much like in Python it performs calculations with them to get a desired result. However, unlike Python we can make a sub-programme to calculate the result of a calculation and store it in a variable, currently Pycraft only uses this in the `shadowmap.glsl`programme (more on this later) but its very similar to a function in Python. In the `main`section of GLSL is where we see the main difference between the `in` and `uniform` syntaxes in GLSL, we can update and set the values for variables defined using the `in` syntax, but the `uniform`syntaxes are for constants and these do not change during the main compute section of the shaders.

This is all we really need to know about GLSL for now, as a basic overview. The contents of the compute section of GLSL for Pycraft is mainly some complex calculations involving matrixes and vectors, with little other specialist syntax like the loops and complex structures we see in Python and other programming languages.

### **Shaders in Pycraft**

Now we have looked into the code structure for GLSL, we now need to go into detail about how these will look for most of the rest of this article (with the exception of the shadow mapping section later on). We will show GLSL files as function machine style objects, with the inputs on the left, the section of GLSL code and the resulting outputs on the right, to help keep things simple.

In Pycraft we have two purposes for shaders, we use them for computing depth in our 3D scene, and also for computing textures and the data for each object, we will start of with going over the function of each GLSL programme in Pycraft, there are only 5 we use for now, but this is set to expand in the future.

Starting with the most basic, the `raw_depth.glsl`programme, this takes in only two variables, `in_position`which is used to calculate the depth of a scene from a set position, and `u_mvp` which is used a matrix which the `in_position`variable scales, this may seem complex, but what this is doing is calculating what can an object ‘see’ from its current position, and anything that it can see will not be in shadow. This programme is solely for compute, and as a result it has no fragment shader component. This shader can be modelled below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377875751/0Xk8B346K.png)

In this diagram, the arrows pointing towards the objects are inputs, so for example `u_mvp`, and arrows pointing away, which there are not here, are the resulting outputs. The output for this shader is later accessed by another GLSL programme. Because there is no fragment shader component it is still shown here, but because it is redundant it has no connection to the other section and this is shown with the dotted line.

Now the next simplest GLSL programme in Pycraft is the `cube_simple.glsl`this is going to however be renamed as it currently is used to render the sun and moon in the Pycraft sky. This GLSL programme is used to calculate the position of the sun and moon in the sky, this is done by entering the position we want the sun/moon to be at with the `in_position`, then we also need to enter a lot of information about the current scene, the next shader also needs this information, but Ill go into more detail here, it needs the model to render, which it receives using the `m_model` variable, it also needs the position of the camera which it gets with the `m_camera`variable, and finally it needs the current scene projection, which is entered to the `m_proj` variable, the current and next shaders need this because it renders the sun/moon or scene relative to the camera (which is our perspective).

This information is then processed (its mainly a bunch of mathematical process that would need a medium article in of themselves to explain, but this tutorial which is not in any way linked to me so I do not moderate any content shared there helps to provide a much more in depth look into OpenGL: [Learn OpenGL, extensive tutorial resource for learning Modern OpenGL](https://learnopengl.com/)).

Then, after the position of the object is set properly onscreen, we then colour the object with the fragment shader, this takes the output from the vertex shader and also a `color` value and then colours the object with this. This GLSL shader is similar in design to the example with the red bike we used earlier. This GLSL programme can be modelled below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377876929/zwOmLOK6m.png)

Next up we have the `cubemap.glsl` programme, this shader is used to texture and transition the skybox between day and night, it has a very similar vertex shader to the previous GLSL programme, but then the output of the vertex shader in used, along with three more inputs: `texture0`which is the texture (in this case a GIF file) which we will be using to texture the sky, the `um_layers` which refers to the number of layers in our texture, then finally we have to enter a `time` value so that the texture can be adjusted depending on the in-game time. Together this will blend the current and next frame together gradually to give a smooth transition between day and night in Pycraft. This shader looks like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377878211/p_Fbdn7yU.png)

There is one final GLSL programme, the `shadowmap.glsl` programme, but we will go into more detail about that in the next section.

### Shadow Mapping in Pycraft

So, there is one final shader that we haven’t looked at yet, and this is the shadow mapping shader, but it’s a lot more complex than just a GLSL programme (which is ironically far more complex than the other GLSL programmes we have seen so far) and it could have been done in two different ways, we could either render the same object twice, one with and one without shadows, but we felt that the performance impact here would have been too significant, so instead we chose to go with a different method.

We use the depth calculation from earlier to calculate which areas would and would not be in shadow, then from there we use the more complex shadow mapping programme to compute the areas that would and would not be in shadow. Both areas of the shadow mapping GLSL programme are lengthy here because although it may only appear a visual effect so therefore rely on the fragment shader, but we use the vertex shader here to compute which areas should and shouldn’t be in shadow using the pre-calculated depth, below is what a simple scene would look like based only on depth:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377879550/Idz_6J-Ve.png)

This is what the shadow mapping programme gets as an input for the depth, and the darker areas are rendered lighter because the light areas are in shadow (because they are further away). This was actually how Pycraft used to render shadows, based on this technique, however this didn’t support any textures or colouring the 3D objects, meaning that Pycraft’s map would be entirely black and white — not what we want!

So, then we switched to a more complex technique that included adding a texture to our scene, and this is where we made our first breakthrough:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377880834/SujvsxR1h.png)

Now this was a very early on preview of shadows in Pycraft, this doesn’t show it well, but we did manage to texture this surface, and then with a bit of tweaking we ended up with this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377882421/0IOG8IFUN.png)

Now this is far from perfect, the shadows where pixelated terribly and there were numerous visual issues, but after 46 days of improvements, we ended up with what we have today:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377884597/kDEb6Ci7y.png)

You can see that there is now a much better texture, and that the shadows are much more detailed and smoother, there are still issues, but for 46 days of work we managed to get something that looked really clean! Below is the GLSL shader for the shadow mapping programme, its much more complex than the others, but relies on the principles we have already looked into before:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377886062/FTKg6Jc7c.png)

This takes in a lot of inputs to get one final result, it takes in the same values as earlier `in_position`, `in_normal` and `in_texcord_0`, then also takes in a `u_mvp` value which is a scale to how deep the scene is, we can use this to adjust the depth of our scene. Then we also enter the `u_depth_bias`, which is the depth of the scene relative to the light source. This then spits out a bunch of values which we use in the next section of the programme, the fragment shader, here we also need to enter, in addition to the results of the vertex shader the position and perspective of the light source `u_light`, then the colour of the light `u_color`, and finally the light level `light_level` which is crucial for changing how stark the shadows are between day and night. The final output is a colour value which is assigned to the scene at a position to create an in-depth shadow effect.

### **Future game Engine Improvements to Pycraft**

So now we have looked at the current features of Pycraft, with the exception of one final change, we initially planned to use a cube based skybox for Pycraft, but in later revisions, due to the large file size of all those images (at least one for each side) and then complications around trying to render a dynamic skybox (so a skybox that changes as the game runs) with the rotation of some of the sides, and the lack of control over the individual images for each side we decided to switch to a sphere based sky, or as I will be calling it from now on a skysphere, this unfortunately means we don’t take advantage of any hardware accelerations for cube maps (a net of 6 images that are wrapped around a cube in a video game) but this makes the file size smaller and the project a bit simpler, and we see almost no change in performance as a result.

We can also see the project scaling slightly to try and get the most performance out of our setup, when we first start the project — this is most noticeable in ‘unlimited FPS mode’ — we see a frame rate of around 400 FPS, then after about 2 minutes we see it increase and stay at a much higher 450–480 FPS, about a 20% performance improvement, this is partially due to changes withing Pycraft to optimise performance, but there are also other — currently unknown factors at play here.

Now, looking at the plan for Pycraft n the near future, we plan to add texture to the terrain based on its steepness (so flatter land could be rendered as grass whilst steep slopes could be rendered as rocky) and also the basics of a weather system will also be added into Pycraft, this will be over the course of 3 updates, one with the textured terrain change, one with basic weather then a final update featuring much more detailed weather.

The first of the two weather updates aims to focus on getting the skybox to change, as well as better atmospheric noise and texture changes, then the second update will see clouds, rain particles, slow particles and more depending on how it all works out!

### Final Words

Thank you for reading this article, I hope that you have liked this article and hopefully you have caught up will all things Pycraft. If you want to share this article that would be greatly appreciated!

Pycraft takes a lot of my time to develop, and a lot of work is but into Pycraft as a whole and writing these articles for you, as a result if you have any questions, suggestions or help; feel free to contact us at [https://github.com/PycraftDeveloper/Pycraft,](https://github.com/PycraftDeveloper/Pycraft,) or by contacting the lead developer here: [https://twitter.com/PycraftDev](https://twitter.com/PycraftDev) or by dropping a post on the discord server which you can find here: [https://discord.gg/h4jpcjJh](https://discord.gg/h4jpcjJh) (server invite).

### Links and Credits

My Twitter Page: [https://twitter.com/PycraftDev](https://twitter.com/PycraftDev)

My GitHub page: [https://github.com/PycraftDeveloper](https://github.com/PycraftDeveloper)

My Dev.to page: [https://dev.to/pycraftdev](https://dev.to/pycraftdev)

Pycraft can be found here: [https://github.com/PycraftDeveloper/Pycraft](https://github.com/PycraftDeveloper/Pycraft)

Pycraft can be also found here: [https://pypi.org/project/Python-Pycraft/](https://pypi.org/project/Python-Pycraft/)

Pycraft’s documentation can be found here: [https://python-pycraft.readthedocs.io/en/latest/](https://python-pycraft.readthedocs.io/en/latest/)

#### With thanks to:

· Thomas Jebbo (PycraftDeveloper) @ [www.github.com/PycraftDevelope](http://www.github.com/PycraftDeveloper)r

· Count of Freshness Traversal @ [https://twitter.com/DmitryChunikhinn](https://twitter.com/DmitryChunikhinn)

· Dogukan Demir (demirdogukan) @ [https://github.com/demirdogukan](https://github.com/demirdogukan)

· Henri Post (HenryFBP) @ [https://github.com/HenryFBP](https://github.com/HenryFBP)

· PyPi @ [www.pypi.org](http://www.pypi.org)

· PIL (Pillow or Python Imaging Library) @ [www.github.com/python-pillow/Pillow](http://www.github.com/python-pillow/Pillow)

· Pygame @ [www.github.com/pygame/pygame](http://www.github.com/pygame/pygame)

· Numpy @ [www.github.com/numpy/numpy](http://www.github.com/numpy/numpy)

· PyOpenGL (and its counterpart PyOpenGL-accelerate) @ [www.github.com/mcfletch/pyopengl](http://www.github.com/mcfletch/pyopengl)

· PyAutoGUI @ [www.github.com/asweigart/pyautogui](http://www.github.com/asweigart/pyautogui)

· Psutil @ [www.github.com/giampaolo/psutil](http://www.github.com/giampaolo/psutil)

· PyWaveFront @ [www.github.com/pywavefront/PyWavefront](http://www.github.com/pywavefront/PyWavefront)

· Py-CPUinfo @ [www.github.com/pytorch/cpuinfo](http://www.github.com/pytorch/cpuinfo)

· GPUtil @ [www.github.com/anderskm/gputil](http://www.github.com/anderskm/gputil)

· Tabulate @ [www.github.com/p-ranav/tabulate](http://www.github.com/p-ranav/tabulate)

· Moderngl @ [https://github.com/moderngl/moderngl](https://github.com/moderngl/moderngl)

· Moderngl\_window @ [https://github.com/moderngl/moderngl-window](https://github.com/moderngl/moderngl-window)

· PyJoystick @ [https://github.com/justengel/pyjoystick](https://github.com/justengel/pyjoystick)

· FreeSound: — Erokia’s “ambient wave compilation” @ [www.freesound.org/s/473545](http://www.freesound.org/s/473545)

· FreeSound: — Soundholder’s “ambient meadow near forest” @ [www.freesound.org/s/425368](http://www.freesound.org/s/425368)

· FreeSound: — monte32’s “Footsteps\_6\_Dirt\_shoe” @ [www.freesound.org/people/monte32/sounds/353799](http://www.freesound.org/people/monte32/sounds/353799)

Please note links under the “With thanks to” are not moderated by me, they are safe links at the time of writing however I do not control the content on them!