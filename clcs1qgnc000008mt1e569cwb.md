# Pycraft Progress Report! 02/01/23

Hello there everyone, it’s time for our weekly progress update, and this is for the week beginning the 2nd of January. This was a week full of small changes to features that we have been working on over the past few weeks in Pycraft, and clearing up some rough edges, particularly focusing on the new save mechanic for Pycraft.

Last week we looked at the theory and discussed the current progress of the save’s menu, however, it was very much this week where we took last week’s work and made adjustments and improvements to it so that it is now in a pretty much-finished state.

To start with, last week we worked on the ability to create new games, something that we had not yet done as we focused more on saving and updating existing saves. Now when the saves menu opens, if there are no saves present then the option to create a new game will appear in the centre of the screen with a difficulty toggle. Clicking on the “create new game” option will not open the save menu, as you have started a new game it now immediately launches the game engine. If you click on the button below the “create new game” option, then the difficulty will change. This week we extended this functionality by changing the behaviour of text rendering slightly on the saves screen: in normal mode the “create new game” font is coloured as specified by the theme you have selected. In hard mode, the text for the game will turn red, this is something that has been applied globally to the text of the game selector, so regardless of what stage of the saves menu you are in, or what number of saves you have, a hard-mode game will always be identifiable by its red font (provided that the user does not choose all fonts to be red, in which case the effect does break; something we are not however sure on how to fix as yet). For the sake of readability the red colour scheme does not apply to saves themselves, although they are affected by the difficulty. As always, the difficulty of the game cannot be adjusted after the game is created, more on that later though.

In addition to this, the red trash-can icon that could be seen in the most recent previews of the save’s menu has been removed, and replaced with a series of 3 dots, like this: “[⋮](https://en.wiktionary.org/wiki/%E2%8B%AE)”. This, when pressed, opens a small menu that contains a series of 3 options:

* “Export” – This allows you to export the entire game folder to a file location that can be accessed by your file manager.
    
* “Export as zip” – This allows you to export the entire game folder, as a zip file, to a file location that can be accessed by your file manager.
    
* “Remove” – This allows you to send the entire game to the recycle bin on your system.
    

We always send files to the recycle bin now instead of removing them forever, this allows the user to recover anything they didn’t want to remove, and however small reduces the risk of accidentally removing important files.

We did also consider the possibility of saving files to other locations beyond what your file manager can access (for example cloud storage locations), however this was deemed too complex for its final purpose, and a potential security vulnerability, and also, they may break at any time for a large range of reasons.

Now, all of this puts us pretty much finished with the new save mechanic of Pycraft, there are still areas that we can optimise and will be testing for bugs, but in terms of features still, to add, we are now finished with that. Unfortunately, this doesn’t mean that we are finished with the development of Pycraft v9.5.6, however, it does mean that we have finished with the key focus of this update which was the new saves mechanic. Currently, we still need to do some essential maintenance and improvements to the installer as we try and reach feature parity between Windows and Linux, and allow it to dynamically adjust the other options available based on the platform that you are using. In addition to that, whilst we have made enough progress on the formatting guide to deem it ready for release, we still have plenty to do in the “Module Breakdown” which is by no means complete.

Now, we think that it is time that we share one of the things we are aiming to work on in Pycraft v9.5.7; and that is our new alternative to messagebox. For those unfamiliar, messagebox is a section of Tkinter that allows us to create those prompts for permissions and error messages that are styled in the same way as the rest of your system. Now, error messages will not be changing, however, the way we ask for permissions will be. Without spoiling too much, we will be asking for permissions by using the new blur mechanic in Pycraft which will make it much easier to deal with these prompts when in full screen. Additionally, we are considering making the choice between exclusive and Fullscreen modes an option available in the settings menu under “video”.

Attached below are some highlights of the last week of development:

![Pycraft's new save selection screen now with a small context menu](https://cdn.hashnode.com/res/hashnode/image/upload/v1673464670333/a47e33e2-5705-4775-871d-1b38be9d7b70.png align="center")