---
title: "Pycraft progress report! 27/02/2023"
datePublished: Wed Mar 08 2023 20:09:30 GMT+0000 (Coordinated Universal Time)
cuid: clf045suq000509l1g7hi7zqi
slug: pycraft-progress-report-27022023
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678304692513/e370a71f-2da3-43e1-b110-d99ca32f6b5e.png
tags: programming-blogs, python, game-development, pycraft

---

Hello there everyone! It's been another week, and what a successful one it has been! This is for the week commencing the 27th of February, and this week we began to shift focus from the 2D game engine to the 3D engine.

For that unfamiliar, Pycraft is comprised of two fundamental graphics engines, each one is built around the same general structure for Pycraft, but expands upon that in different ways. For instance, the 2D engine is designed to be user-friendly, look good and be adaptable to change, without perhaps being the most efficient in resources. In the 3D game engine, efficiency counts as we add another dimension of complexity by bringing hardware-accelerated rendering to Pycraft. At the time of writing, there is one menu that takes advantage of the 3D engine and 9 menus that take advantage of the 2D engine, and this isn't going to change much, with at present, the final menu composition for Pycraft being 3 that are using the 3D engine, and 8 that use the 2D engine.

Whilst built off the same architecture, the different graphics engines follow very different structures for rendering and handling events, with the 3D engine being much more complex. This knowledge, therefore, means we can split the development on improving the way data is shared through Pycraft into 3 fundamental categories, the start-up, 2D engine and 3D engine. The installer adds the 4th category to complete the list. The first two categories we have managed to complete, and we are now moving into the 3rd category. This was inherently going to lead to a few days of reduced progress as we adapt our workflow to be more optimised for the change, and also to refamiliarise ourselves with the code in question. Even before we started working on this stage of development, we were already however a good way through the changes we had yet to make as we had gone through the whole of Pycraft and removed at the start all of the interactions we had planned to replace.

Unfortunately, despite this head-start, we are still at a disadvantage as, if I draw your mind back to earlier, we currently only have 1 3D engine-based menu, where we have 9 2D menus, meaning that essentially we were able to go through the 2D engine much faster, as the same interactions are often repeated (but to a minimum where possible) for each menu. Additionally, the 3D engine may only have one menu, but that menu is the longest file in Pycraft, and is considerably more complex. It also shares two additional menus with the 2D engine.

Sharing data and transitioning between the 2D and 3D engines has always been an inherent problem for us, and is one we have gotten much better at addressing recently, however one way we are planning to improve this further is to bring the two attached 2D engines to the main 3D engine into the 3D engine. Currently, this means that the installer and map, the two 2D menus, linked to Pycraft's 3D engine, will eventually actually become a part of the 3D engine, which is why they haven't been updated much, as they are going to be needing a complete rewrite for that to be effective.

This means we have got lots of work to do, and plenty of which by the end of the week we have now done, which is excellent news, as we managed to get the loading screen, map and inventory sections each operational after only a day of work, and we are now getting close to finishing the full loading of the 3D engine. This is huge news as the 3D engine, by being the most complex menu, is where the capabilities of the latest structural changes will be most challenged and pushed to its limits, and currently, we have seen the 3D engine adapting well to the slight structural change, which is excellent news, and even if we don't expect the changes we are making now to be noticeable in any way to the end user, it has revolutionised the transfer of data throughout Pycraft, not just the 3D game engine, and that will allow future expansion to be much easier!

We hope that you have enjoyed this article, and we are planning to update this within 24 hours with some images to share for our progress this week, although sadly don't have time to do that today! Thanks for reading.