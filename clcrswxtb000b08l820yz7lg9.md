# Pycraft Progress Report! 26/12/22

Hello there everyone, it's Pycraft progress update time, and this is for the week beginning the 26th of December!

Last week we where discussing the work on Pycraft v9.5.6's saves functionality, even though Pycraft v9.5.5 hadn't been released yet, so everything was a bit confusing.

However since then Pycraft v9.5.5 has been released, along with its corresponding 'under construction' documentation and we realise that, although we try to cover as much of the highlights from this week of development, sometimes we may miss more minor changes to our plans; and we need to start this article off with a slight change to the way we will be sharing the documentation for Pycraft.

So, from now on, every release of Pycraft will have a corresponding documentation, including all major, minor and development releases of Pycraft. The documentation for a specific version of Pycraft will be made available for as long as that version is listed in the branches section of the GitHub repository for Pycraft; which you can find here: https://github.com/PycraftDeveloper/Pycraft

The rules for accessing documentation once that version of Pycraft is no longer in the branches section of our repository are also slightly different, the major, minor and development releases to Pycraft's corresponding documentation will always be saved, and made accessible through our ReadTheDocs site; here: https://python-pycraft.readthedocs.io/en/pycraft-v9.5.0/ however, only major and minor versions of Pycraft's documentation will be made available to view. This change comes into effect after the full release of Pycraft v10.

Now, with that out of the way we sill stay with the documentation for Pycraft for a moment more to inform you that since last week we have made some adjustments and improvements to the Introduction, and Module Breakdown components (of the unreleased documentation for Pycraft v9.5.6) to improve formatting, and also extended the rollout of the docstrings into more of the utility programs for Pycraft.

In terms of our component-by-component breakdown of the progress on docstrings in Pycraft; this is where we are at currently:

* The fundamental setup/initialisation/startup programs - all complete
* The programs for each of the GUI/menus for Pycraft - all complete
* The utility programs for Pycraft - not yet finished; roughly 50% complete
* The installer for Pycraft - Not yet started

We have also been busy with work on the formatting guide for Pycraft, which acts as an extension and tracker of the implementation of the PEP-8 standards in Pycraft.

Now enough of the documentation, lets talk about improvements to the source code for Pycraft! Starting off with our revised schedule of focusing on the documentation and work on the source code for Pycraft on alternating days so we can more evenly make progress on both.

Since last week we have been focusing on taking the front end design, and adding in more of the backend for the saves GUI, so that includes introducing the mechanisms for making, removing and automatically making saves for Pycraft. This can be done by clicking on the save, or save and exit buttons in the inventory of Pycraft.

Now seeing that this has overwritten our hand-made sample layout of the saves structure, there have been some changes to the look of the saves menu. The most noticeable here is that the in game location where the save was made has been left blank, that is because there is currently no in game areas, and this will be added back in, when we work on that in future. Aside from that, we have been improving the projects flexibility towards having varying numbers of saves and games.

In addition to this, we have been working on the creation of new games, which wasn't present last week, when there are new games that can be created, there is now a difficulty menu that appears below the button to make that new game, this may sound confusing, but the preview we have shared at the bottom of this weekly progress update should hopefully make more sense. The difficulty of the game cannot be adjusted after the game has been created (to avoid players from potentially trying to exploit the changes in game mechanics, or to make certain areas of the game easier through a change in difficulty) and when you have decided on your difficulty, clicking on "create a new game" will immediately through you into the game engine, after it has loaded, and in future versions of Pycraft a cut scene will be added here so that it is made clear what is going on in game.

Now, we hope you have enjoyed this latest weekly progress update, thanks for reading, and attached below are some preview images of the current condition of the saves menu by the end of the week! - enjoy


![The new difficulty toggle for new games](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377313620/Osv43ZpW3.png)


![The option to delete a game has been added](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377315194/PbScUhd1f.png)
