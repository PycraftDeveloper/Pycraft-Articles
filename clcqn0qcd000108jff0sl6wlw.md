# How We are Making a Video Game in Python #9

Pycraft’s banner image

Pycraft; the 3D open-source, open-world video game being made in Python!

This series of articles, updated monthly, will document the latest additions and features to Pycraft that we are most proud of, and act as a brief guide to how we — and you too — can use these features and tricks in your own projects! Additionally, this series also gives additional insight into features coming up very soon in Pycraft’s development, and act as a guide to Pycraft’s future plans.

This article is written by Tom Jebbo, the lead developer and designer of the Pycraft team. We hope you enjoy both using our project and reading our series of articles!

* You can find the latest release of Pycraft (v9.5.0) here: [github.com/PycraftDeveloper/Pycraft](https://github.com/PycraftDeveloper/Pycraft)
    
* You can also find the latest release of Pycraft (v9.5.0) here: [https://sourceforge.net/projects/python-pycraft/](https://sourceforge.net/projects/python-pycraft/)
    
* You can also find the latest documentation for Pycraft here: [https://python-pycraft.readthedocs.io/en/pycraft-v9.5.4/index.html](https://python-pycraft.readthedocs.io/en/pycraft-v9.5.4/index.html)
    

### Contents

* Pycraft’s New Settings Menu
    
* \- Button Widget
    
* \- Slider Widget
    
* \- Dropdown Widget
    
* Pycraft’s Third Restructuring
    
* Pycraft’s Versioning Changes
    
* Future Changes Coming to Pycraft
    
* Dungeon Mechanics
    
* Final Words
    
* Links and Credits
    

### Pycraft’s New Settings Menu

There are many GUIs in Pycraft, but one of the oldest and least changed is the settings menu. In nearly 3 years there has been almost no change to improve the way it delivers functionality, either to developers — or to the end user. The GUI was dated and old, and lots of the widgets didn’t work great, and the settings menu was an absolute nightmare to work on as a developer — so adding new features did not happen often. The settings menu was designed to only ever work with a keyboard and mouse, never a controller, and even at that barely worked at all.

So, in Pycraft v9.5.3 and Pycraft v9.5.4 we started the huge job of completely redesigning the settings menu, both based on an improved front end design, and a much more modular backend design that made it easier to work on later. In Pycraft v9.5.3 we took the original features of the settings menu and transferred them over to the new system. Then in Pycraft v9.5.4 we built upon the new system adding in swathes of new options that where all much needed and helped to make debugging Pycraft much easier.

Originally the settings menu appeared as written, so in order to add an element to the screen you would have to physically go and change the settings menu’s code to add the new feature. Now the settings menu takes a much more modular approach — something that has inspired a similar design change to the credit’s menu and later the benchmarking engine.

In order to change (add or remove) an element from the new settings menu you need to simply adjust the (.json) file that it reads from, with details on how to do this coming in the new year with an improved documentation. Unfortunately, more complicated changes, like adding in a dropdown menu are still mostly done through code simply due to their complexity, although ways to change this are always being considered.

So, with structure out the way, what about the widgets themselves? Well originally every element in the settings menu had its own code, even if the same element was repeated, which meant that for how basic the settings menu originally was — it was huge! Something that certainly didn’t make adding in changes later easy. Now admittingly the new settings menu is also long; however, it takes a more modular approach so the number of lines repeated is significantly reduced, and the number of lines used shouldn’t increase significantly in future updates unless we add new elements.

So, we have talked a lot now about the theoretical design, now it’s time to look at the finished result for 3 of the redesigned widgets, from older classics that have been given a bit of a design refresh, to entirely new systems written and designed from the ground up, these 3 have been picked for how well they showcase some of the principles and design changes we had in mind when making the changes to the settings update. There are now many more different widgets in Pycraft than there were before, we look forward to introducing you to some of our favourites!

#### Button Widget

The button widget is the first or three widgets we are going to be looking into the design of in the redesigned settings menu. We have wanted to add in a button element to Pycraft for some considerable time, however this is the first opportunity we have had to add it, and of the three we are looking at here, this is by far the one we have spent the most time planning!

The button widget is one of the most versatile forms of widget in Pycraft, forming the fundamentals of a few other settings elements, which is why we haven’t included those as well in this list. We are of course talking here about the button, command, multi-button and chained button elements.

The button widget in its simplest form acts very similarly to a toggle switch element, with the ability to be clicked on and off to toggle its state and the feature it therefore represents. Because of this we don’t use the button widget in this form a great deal, as we want to create the variety and option for it to be there, however it acts more as a foundation to the other types.

The command widget, similarly to the button widget, is a single object onscreen, that has the same basic mechanics for hovering and design as the button, however when clicked this will not set the state of a variable that goes on to change something in Pycraft, it instead calls a subroutine to do a specific task, for example clearing Pycraft’s temporary files, and has the option to be disabled or enabled based on other settings or if it has been activated — for example; preventing you from clearing Pycraft’s cache multiple times too quickly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377929314/5Myd6ihzE.png align="left")

An example of the ‘command button’ application where when clicked, Pycraft’s temporary files will be cleared

The multi-button takes the principle of the button element and chains it together, in a way very similar to the chained button element, where you can have a series of buttons placed next to each other that relate to the same setting. The multi-button widget gives the user the option to select and deselect multiple different options relating to the same setting. This has many practical applications — for example; allowing you to choose if you want to log critical errors, warnings, both or nothing.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377930479/eA0uJvP_M.png align="left")

An example of the ‘multi-button’ application where the user can choose multiple different elements to enable/disable

On the flip side we have the chained button widget. This continued to use the principle we just looked at of placing multiple buttons beside each other, however this time instead of being able to select multiple different options, this allows you to select a category from a series of options. Where the slider widget can give a value on a continuous scale, this gives you discrete options. A good example of this would be themes, you can choose light or dark mode, but you can’t have both.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377931803/DnqF_U74y.png align="left")

An example of the ‘chained button’ application where the user can only choose one from a range of options.

#### Slider Widget

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673378114746/lBMTJjXZk.png align="left")

An example of the slider application, where the user can easily drag a slider to their preferred value.

The slider widget is the only widget that we are going to be writing about here that was also in the original settings menu, there is so much that has changed here, and also it gives a good comparison to how much things have changed since the original version design of the settings menu.

The slider widget is one of only two ways you can enter data on a continuous range in the new settings menu, with the other being the custom theme text input where you can enter a numerical value.

Of the 3 widgets that were present in the original settings menu the slider has seen the most extensive change, not only has its design completely changed, but its mechanics have also been completely rewritten to fix the numerous problems with mouse interactions and controller support.

#### Dropdown Widget

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673378116202/rf3VxNzYI.png align="left")

An example of the dropdown application where the user can easily choose from a range of options

The dropdown widget is the newest addition to the range of new additions to the settings menu, this widget is designed for applications where their multiple choices or options available, too much to be able to represent with a series of connected buttons (the chained button widget from earlier), or in situations where the number of available options may increase in future.

This currently has two applications in Pycraft, it allows the user to change the language of Pycraft, and also to adjust the (full screen) rendering resolution of the game engine

### Pycraft’s Third Restructuring

For nearly a year before we started work on Pycraft we spent a large amount of time planning and designing resources and where we want to go with Pycraft. This planning process has never stopped, even once development started. We quickly realised that some things where possible in code that we didn’t initially expect once we had started development and would make amendments to our plans as a result, unfortunately that process worked both ways and sometimes we would need to cut features that either later turned out to be unnecessary or deemed to be too tricky to implement for its purpose.

However, sometimes it’s not a 3rd party responsible for changes to plans in Pycraft. Because we are constantly revising our plans, we are always trying to prioritise some features other others, and when we change plans, we also need to make changes to Pycraft to reflect these changes. However, in some situations the way we implement the changes to Pycraft due to changes in plans may later affect future code that is still planned, or alternatively we write and plan code and go to extend that in future plans, long after the original plans were drawn up.

It is this that directly resulted in the sudden change of direction with the plan for Pycraft v9.5.5, as we have spent the last 2 months working on an update that was not at any stage predicted or planned, but instead was because we had reached a point in our planning where too many features had been pushed back due to unnecessary complexities surrounding Pycraft that we felt we had no choice but to go back and make significant changes to Pycraft.

This all reached problematic levels during the redesign of the settings menu. The settings menu was one of 3 UIs that had been planned and added to Pycraft around 4 years ago, these core UIs; the settings menu, the main menu and the game engine where the first to be added to Pycraft, and the settings menu-controlled functionality and behaviours of the other UIs. As we started to build off this foundation, we started to make changes to the game engine and main menu (also home screen) to the point where a large amount of the original code had been rewritten or changed to add new features or improve older ones.

However, the settings menu had remained somewhat isolated from these changes. It lacked any form of modular design — or for that matter much of a design focus at all. And was much too long for its purpose (indicating an inefficient use of code); the original settings menu was at its longest 2,293 lines long by the time work on it began. For reference that’s 2.3 times longer than the entire original code for Pycraft (v0.0.0).

It was at this point that we decided that we had to make some changes, because the other UIs where improving, and the settings menu was at risk of becoming a mess of problems if we left it much longer, and it was slowing down the development and customisability of other features. So, the process of reworking that began, which we documented in the previous chapter.

We broke development down into two stages:

* Stage 1: In this stage we completely removed all of the original settings menu code and started from scratch, adding in only the original functionality of the settings menu so we could perfect the design and implementation before building off that in stage 2.
    
* Stage 2: In this stage we take the concept we were satisfied with in stage 1 and expand upon that, adding in new options and elements that would add useful customisation to other UIs and also add in easier ways to test and edit Pycraft.
    

Fortunately stage 1 of development was amazingly successful, without removing any of the original functionality of the settings menu and considerably improving the look and functionality of the settings menu we managed to reduce those 2,293 lines down to just 894, that’s an improvement of 61% in terms of line efficiency. We achieved this by using a more modular design, as well as simplifying considerably upon the implementations of the original UI.

So, stage 1 of the settings menu’s development went perfectly, this was we believe in part because although the settings menu at this point went through some radical changes, none of the changes had much of an effect on the rest of Pycraft. The best way to understand that Pycraft calls the settings menu and expects a response, Pycraft does not care about the inner working of the settings menu, they could be completely changed and provided that the same result gets returned then the rest of Pycraft would remain relatively unaffected. This is very similar to how you may have multiple PCs at an office, but you can log into any one of them and complete the same task, even if the PCs themselves have different hardware.

This means that going into stage 2’s development was inherently going to cause problems. The settings menu as we have seen is a fundamental area of Pycraft and when changed could have significant consequences to other areas of Pycraft. In stage 1, to the rest of Pycraft, the settings menu still had the same inputs and outputs. However, when it was time to start work on adding in new settings this was inevitably going to start causing problems.

However, these problems where somewhat mitigated by the ease of development on the new settings menu, because everything is now so much more modular and not in fixed positions onscreen, it meant that adding a new setting went from being a multi-hour task to perhaps a 20-minute task (where the widget you are using is already implemented, for example the ones detailed in the previous chapter and more). This means that we were able to quickly start adding in settings that have long been requested and we have wanted to add.

We have briefly talked about how modular Pycraft’s new settings menu is, and the speed improvement in development this brings. However, there is one caveat to this; that only applies to widgets that are already implemented. There are a wide range of widgets and input options to choose from however where a new solution needs to be devised this is still a fairly complicated task and will take time, something that we have seen in the addition of the new dropdown menu, but part of that is also linking the new widget into the rest of Pycraft so that it behaves as expected. This additional time needed to create a new widget or UI element is quickly offset though by how comparably easy it should be to later re-use that code if it was needed later down the line. For example, let’s say we want to add a new widget to Pycraft and use this new widget 3 times in the settings menu.

In the old implementation it would take around 2.5 hours to initially set up the new element, then from there a further 1.5 hours every time we wanted to add in this element again (to allow for the initial design and implementation process), this leads to a total time taken of 5.5 hours to add the new widget and use it 3 times in the old settings menu.

In the new settings menu, it would take around 3 hours to initially set up a new element, from there it would take just 30 minutes to then use this widget again in a later setting, this means that the total time taken for this approach is 4 hours, a considerable amount less than the 5.5 hours needed for the old approach. And in addition to this time saving, the amount of code needed in this implementation would be significantly less than that of the older settings menu.

Please note that the values used here are estimates based on our experience with the two settings menu designs, it is possible for features to be added in more or less time for either approach, however the rule of re-using the element in the second (current) implementation being faster still applies.

As we can see, the actual code design changes to the settings menu work pretty much perfectly, so where did the need to change the direction of development in Pycraft v9.5.5 arise? Well, we have seen how integral the settings menu is to Pycraft, as it is one of the core UI’s. However, we had, at this stage of development innovated the settings menu to have features beyond its original capabilities, meaning that other areas of Pycraft needed changing to make sure that any changes to the options in the settings menu where properly reflected in the entirety of Pycraft.

We had hoped this would be a relatively simple process, however it was quickly drawn to our attention that we may have been wrong on that, and the problem lies — once more — with the game engine. In an earlier version of Pycraft we made the switch to ModernGL from PyOpenGL as our way of interacting with the OpenGL environment through Python. This increased the performance of the game engine by almost 18 times, going from an average of around 26 FPS in PyOpenGL to an average of 468 FPS in ModernGL (For the same hardware and scene) and whilst not all of that performance was made up by this switch, as we needed to completely redesign the underlying architecture for the game engine, we believe a large amount of it to have been.

This switch is where we first introduced the problem, at the worst possible time, we made a fundamental problem with the foundation of the game engine, that we then proceeded to build the rest of the game engine on. The problem was that in order to — at the time with our limited understanding of ModernGL — create a functional game engine, we needed to run the game engine isolated in a way from the rest of Pycraft. The game engine was run in what we can describe as almost a ‘bubble’ separated from the rest of Pycraft. This means that we could pass variables into the game engine environment once, when Pycraft first loads, but then after that we could not modify the behaviour of the game engine without a restart.

This bug also applied to the OpenGL benchmark environment, although there the problem is not nearly as noticeable as the main game engine as there it only needs to be set up once and then doesn’t have any attributes that change — by design — to make sure the test is as repeatable across different systems.

This problem is something that we had noticed, but only after we where well through the entire game engine redesign and as such didn’t change it — we didn’t really need to as the settings menu didn’t really affect the game engine at that stage as neither system as advanced enough at that stage for it to be a big problem. The game engine was by far one of the biggest forms of motivation for this change, although there were problems starting to show in lots of other places in Pycraft too at the time when making the changes to the settings menu, because it was such an integral part of the old design of Pycraft.

It was because of these problems that when we had to release the second part of the settings menu, lots of the new features where ‘software locked’ (where a feature is present in the source code, but calls to that feature have been disabled, making it inaccessible). So, we decided that instead of adding additional complexity to Pycraft at this point we would take a break from adding features to improve older ones. This also gave us a perfect opportunity to change some massive system-wide problems and improve and add additional minor features. And so, what was originally just meant to be an overhaul to the settings menu, quickly turned into a system-wide restructuring.

The design of Pycraft in general is also changing, initially there wasn’t much of a design focus, we were interested mainly in adding functionality. However, we are now also improving the design of Pycraft, something that initially started over a year ago when we unveiled some new icons and images used (for example in the caption) for Pycraft. The settings menu has really brought the design of Pycraft to our attention as not only has the settings menu for Pycraft been reprogrammed, but it has also been redesigned as we move away from using sharp shapes and solid blocks of colour, instead opting to use rounded corners and — later — a blur effect in some GUIs, here is the example of the recently showcased saves menu in the old style of Pycraft (top) and the newer style (bottom):

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673378117682/uz1ypszkE.png align="left")

Here is an example of the prototyped saves screen that will be added in Pycraft v9.5 based on the older design for Pycraft

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673378119813/KinYvUCUa.png align="left")

Here is an example of the prototyped saves screen that will be added in Pycraft v9.5 based on the newer design for Pycraft

### Pycraft’s Versioning Changes

Of the numerous changes that have been made to Pycraft in the course of Pycraft v9.5.5’s development, one of the most immediately noticeable changes came in late October when we migrated to a new method of versioning, we are trying to make versioning more concise now in Pycraft.

There are 3 major changes we made to versioning, and we are now going to cover how, and our reasoning, why we made each of the 3 major changes which takes Pycraft’s version from v0.9.6.0–5 to v9.5.5.

* The first thing we did is remove the ‘0’ at the start of ‘v0.9.6.0–5’ as it was originally intended to signify when Pycraft was in a public preview stage, however this was made redundant when we started sharing our progress on GitHub, instead of releasing updates internally. In fact, now Pycraft is publicly available it should actually be a ‘1’, so not only did it serve no function, it also represented out of date information. Because of this the first digit of the old versioning system was removed.
    
* Then we took the last two digits of the version code we had left, ‘v9.6.0–5’ and added them together as the first digit (in our example this is ‘0’) was used to represent any patches made to Pycraft since the last significant release, however we only ever used this feature once, when we needed to make a slight change to an update recently released. However, since then we have improved how we handle updates and now problems like that are fixed usually before release, if though a problem was still to occur then it would likely be patched in a few weeks when we release the next developer update to Pycraft. Because of this that number was often not included in most references to the version of Pycraft. On the subject, let’s talk about developer releases. We have released a few for Pycraft so far and this gets much more use than the number representing the patch revision. As a result, we made the decision to combine the two together. This does mean that it will be less clear when patches are released for Pycraft, however we have no expectation that we will be releasing patches to an update as we are usually only a short period of time away from another release.
    
* The final change that we have made is we dropped the 2nd number down a stage, so continuing from our example above, ‘v9.6.5’ now becomes ‘v9.5.5’. This is because as we were implementing the changes to versioning for Pycraft we realised that versions in Pycraft wouldn’t have been linear if we didn’t make this change; allow me to show by way of an example. This is a sequence of versions for Pycraft that have had the first two steps of the process applied to them, but not this last stage: ‘v9.4.8’, ‘v9.4.9’, ‘v9.4.0’, ‘v9.5.1’, ‘v9.5.2’. As you can see, this isn’t ideal, so we made this final adjustment so that the same sequence of versions would now go: ‘v9.3.8’, ‘v9.3.9’, ‘v9.4.0’, ‘v9.4.1’, ‘v9.4.2’.
    

Unfortunately, the old version system for Pycraft is still commonly used in historical work for Pycraft, we have made amendments to change some more recent work however its unfeasible for us to go back and change potentially thousands of references to the old versioning system. However, there is good news, you can easily identify a place where the old versioning system has been used as the version code will always start with a zero, whereas the new versioning system will never start with a zero. To convert the old version code to the new version code in summary:

1. Remove the first ‘0.’
    

2\. Add the last two digits together (in most cases however the first of the two digits won’t be shown. Its normally 0)

3\. Subtract 1 from the middle of the 3 numbers you have remaining, if this gives you a negative value then set the middle number to 0 and subtract one from the first digit.

We will be updating a lot of the written and visual resources for Pycraft so hopefully that process isn’t necessary. To convert the new version to the old version simply do the steps above in reverse!

### Future Changes Coming to Pycraft

It came as some surprise that it’s been over a year already since we last shared the full plan for the near future of Pycraft, and some things have changed. Before we begin talking about new features it’s important to note that the first digit in the version of Pycraft relates to the overarching goal of that period of development, and each sub-version to that is related to a goal that is being made as a part of that major update.

We last shared a timeline of development with you in October of 2021 and the focus of development has shifted slightly since then, nothing on that original list has been removed or is no longer coming, but some sections are coming sooner or later than others, and this is not a complete list, especially for versions sometime in the future as things may change.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673378121293/l56sVQi7-.png align="left")

You can find the content in this table in text form here: [https://docs.google.com/document/d/1rqCGwxIhjQCt5Ssjp\_p4wC3ENsPgmQgFyCMTurLVsjQ/edit?usp=sharing](https://docs.google.com/document/d/1rqCGwxIhjQCt5Ssjp_p4wC3ENsPgmQgFyCMTurLVsjQ/edit?usp=sharing)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673378122562/vIR4qN9TI.png align="left")

You can find the content in this table in text form here: [https://docs.google.com/document/d/1rqCGwxIhjQCt5Ssjp\_p4wC3ENsPgmQgFyCMTurLVsjQ/edit?usp=sharing](https://docs.google.com/document/d/1rqCGwxIhjQCt5Ssjp_p4wC3ENsPgmQgFyCMTurLVsjQ/edit?usp=sharing)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673378124393/N0fkBkRkcc.png align="left")

You can find the content in this table in text form here: [https://docs.google.com/document/d/1rqCGwxIhjQCt5Ssjp\_p4wC3ENsPgmQgFyCMTurLVsjQ/edit?usp=sharing](https://docs.google.com/document/d/1rqCGwxIhjQCt5Ssjp_p4wC3ENsPgmQgFyCMTurLVsjQ/edit?usp=sharing)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1673378125708/Lb3rhyHt9G.png align="left")

You can find the content in this table in text form here: [https://docs.google.com/document/d/1rqCGwxIhjQCt5Ssjp\_p4wC3ENsPgmQgFyCMTurLVsjQ/edit?usp=sharing](https://docs.google.com/document/d/1rqCGwxIhjQCt5Ssjp_p4wC3ENsPgmQgFyCMTurLVsjQ/edit?usp=sharing)

Looking from Pycraft v13 and onwards into the future there is still plenty to add, including the storyline, animations, cut-scenes, Pycraft specific game mechanics, bosses, items and more however these rely heavily on the future work for Pycraft and we can’t really plan or schedule that for some time yet. The plan here is going to be over the course of the next few years and is designed to be a structure to work on, and we will be adding in other elements and improvements where necessary through this time.

### Dungeon Mechanics

Pycraft’s story is going to entail you exploring the map and finding 8 special locations. We call these fountains, sounds easy right? Well getting to these fountains is trickier than it seems, they are all unlocked from the moment you step foot on the land at the start of the game, but will require the application of skills to unlock, for example the one in the middle of the Forest of Secrets is hidden in a dense foggy forest full of enemies — and also loot — however in the Forest of Secrets if you stop moving for too long (7 seconds in normal mode, or 3 in challenging mode) then you will be engulfed in the fog and moved to a random location in a ring of equal distance to the centre of the forest, and also rotated so you may not be facing the same direction. It’s up to you to try and figure out your way.

Fortunately, once you reach a fountain you can then warp to it if you need to go back. When you reach a fountain, it will be damaged and you will be tasked to find an item somewhere in the game that is needed to activate the fountain.

Upon doing this task you will be teleported into one of 8 dungeons. There is also an additional 9th dungeon that you get placed in by the antagonist created from your ‘weaknesses and fears’ at the end of the storyline. This will be harder than the other dungeons and will require the application of all your skills, in terms of ones unlocked in game and also parkour, combat, strategy and more based on game engine mechanics you will see in Pycraft.

Potion effects will not be applicable in dungeons and will be paused for the duration of time you are in them. Additionally for the 8 skill dungeons only the skill you are working on will be available. For all dungeons there is no expectation for you to have items, they are allowed in all but the final dungeon (which is engineered to take place as though in your head) so items can be found in dungeons to help you.

There are checkpoints in each dungeon as they are long. This will allow you to save your progress, if you die then you will be sent back to your last checkpoint. Additionally, you can leave a dungeon at any time, but your progress is only saved to your current checkpoint, so make sure that if you do leave a dungeon then you have recently reached a checkpoint.

Loot obtained in a dungeon can only be used in that dungeon and cannot be removed with the exception of when you complete the dungeon. Your health is reset at the start of the dungeon to full, although damage taken in each dungeon will be the same if you later decide to leave the dungeon.

When you reach a checkpoint, you are rewarded with loot that gets better the more challenging each stage gets.

In a dungeon there are going to be 10 stages (this may change although it’s unlikely) and they will get progressively harder towards the end. The final stage of the 8 skill dungeons is a boss battle. Damage dealt to each boss is reset if you leave the dungeon and in challenging mode bosses can regenerate health.

If you leave a dungeon before you have completed it then the in-game skill you are working towards is removed until you re-enter or complete the shrine.

### Final Words

Thank you for reading this article, I hope that you have liked this article and hopefully you have caught up will all things Pycraft. If you want to share this article that would be greatly appreciated!

Pycraft takes a lot of my time to develop, and a lot of work is but into Pycraft as a whole and writing these articles for you, as a result if you have any questions, suggestions or help; feel free to contact us at [https://github.com/PycraftDeveloper/Pycraft,](https://github.com/PycraftDeveloper/Pycraft,) or by contacting the lead developer here: [https://twitter.com/PycraftDev](https://twitter.com/PycraftDev) or by dropping a post on the discord server which you can find here: [https://discord.gg/83EBntQqpf](https://discord.gg/83EBntQqpf) (server invite).

### Links and Credits

You can find us on Dev at: [https://dev.to/pycraftdev](https://dev.to/pycraftdev)

You can find us on Discord at: (invite) [https://discord.gg/83EBntQqpf](https://discord.gg/83EBntQqpf)

You can find us on GitHub at: [https://github.com/PycraftDeveloper](https://github.com/PycraftDeveloper)

You can find us on Instagram at: [https://www.instagram.com/pycraftdev/](https://www.instagram.com/pycraftdev/)

You can find us on PyPi at: [https://pypi.org/user/PycraftDev/](https://pypi.org/user/PycraftDev/)

You can find us on Read-The-Docs at: [https://python-pycraft.readthedocs.io/en/pycraft-v9.5.0/](https://python-pycraft.readthedocs.io/en/pycraft-v9.5.0/)

You can find us on Revue at: [https://www.getrevue.co/profile/PycraftDev](https://www.getrevue.co/profile/PycraftDev)

You can find us on SourceForge at: [https://sourceforge.net/u/pycraftdev/profile/](https://sourceforge.net/u/pycraftdev/profile/)

You can find us on Twitter at: [https://twitter.com/PycraftDev](https://twitter.com/PycraftDev)

You can find us on YouTube at: [https://www.youtube.com/channel/UCsY70jt7ElA4e\_3YPlIkSnA](https://www.youtube.com/channel/UCsY70jt7ElA4e_3YPlIkSnA)

#### With thanks to:

Thomas Jebbo (PycraftDeveloper) @ [www.github.com/PycraftDeveloper](http://www.github.com/PycraftDeveloper)

Count of Freshness Traversal @ [www.twitter.com/DmitryChunikhin](http://www.twitter.com/DmitryChunikhin)

Henri Post (HenryFBP) @ [www.github.com/HenryFBP](http://www.github.com/HenryFBP)

PyPi @ [www.pypi.org](http://www.pypi.org)

PIL (Pillow or Python Imaging Library) @ [www.github.com/python-pillow/Pillow](http://www.github.com/python-pillow/Pillow)

Pygame @ [www.github.com/pygame/pygame](http://www.github.com/pygame/pygame)

Numpy @ [www.github.com/numpy/numpy](http://www.github.com/numpy/numpy)

PyAutoGUI @ [www.github.com/asweigart/pyautogui](http://www.github.com/asweigart/pyautogui)

Psutil @ [www.github.com/giampaolo/psutil](http://www.github.com/giampaolo/psutil)

PyWaveFront @ [www.github.com/pywavefront/PyWavefront](http://www.github.com/pywavefront/PyWavefront)

Py-CPUinfo @ [www.github.com/pytorch/cpuinfo](http://www.github.com/pytorch/cpuinfo)

GPUtil @ [www.github.com/anderskm/gputil](http://www.github.com/anderskm/gputil)

Tabulate @ [www.github.com/p-ranav/tabulate](http://www.github.com/p-ranav/tabulate)

Moderngl @ [www.github.com/moderngl/moderngl](http://www.github.com/moderngl/moderngl)

Moderngl\_window @ [www.github.com/moderngl/moderngl-window](http://www.github.com/moderngl/moderngl-window)

Matplotlib @ [www.github.com/matplotlib/matplotlib](http://www.github.com/matplotlib/matplotlib)

FreeSound: — Erokia’s “ambient wave compilation” @ [www.freesound.org/s/473545](http://www.freesound.org/s/473545)

FreeSound: — Soundholder’s “ambient meadow near forest” @ [www.freesound.org/s/425368](http://www.freesound.org/s/425368)

FreeSound: — monte32’s “Footsteps\_6\_Dirt\_shoe” @ [www.freesound.org/people/monte32/sounds/353799](http://www.freesound.org/people/monte32/sounds/353799)

Freesound: — Straget’s ‘Thunder’ @ [www.freesound.org/people/straget/sounds/527664/](http://www.freesound.org/people/straget/sounds/527664/)

Freesound: — FlatHill’s ‘Rain and Thunder 4’ @ [www.freesound.org/people/FlatHill/sounds/237729/](http://www.freesound.org/people/FlatHill/sounds/237729/)

Freesound: — BlueDelta’s ‘Heavy Thunder Strike — no Rain — QUADRO’ @ — [www.freesound.org/people/BlueDelta/sounds/446753/](http://www.freesound.org/people/BlueDelta/sounds/446753/)

Freesound: — Justkiddink’s ‘Thunder » Dry thunder1’ @ [www.freesound.org/people/juskiddink/sounds/101933/](http://www.freesound.org/people/juskiddink/sounds/101933/)

Freesound: — Netaj’s ‘Thunder’ @ [www.freesound.org/people/netaj/sounds/193170/](http://www.freesound.org/people/netaj/sounds/193170/)

Freesound: — Nimlos’ ‘Thunders » Rain Thunder’ @ [www.freesound.org/people/Nimlos/sounds/359151/](http://www.freesound.org/people/Nimlos/sounds/359151/)

Freesound: — Kangaroovindaloo’s ‘Thunder Clap’ @ [www.freesound.org/people/kangaroovindaloo/sounds/585077/](http://www.freesound.org/people/kangaroovindaloo/sounds/585077/)

Freesound: — Laribum’s ‘Thunder » thunder\_01’ @ [www.freesound.org/people/laribum/sounds/353025/](http://www.freesound.org/people/laribum/sounds/353025/)

Freesound: — Jmbphilmes’s ‘Rain » Rain light 2 (rural)’ @ [www.freesound.org/people/jmbphilmes/sounds/200273/](http://www.freesound.org/people/jmbphilmes/sounds/200273/)

Please note links under the “With thanks to” are not moderated by me, they are safe links at the time of writing however I do not control the content on them!