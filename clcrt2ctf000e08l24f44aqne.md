# Pycraft Progress Report 03/09/22

###Hello there reader;
We decided that transferring the posts we made on Twitter every few weeks to Dev was slow and inefficient, and also didn’t match the style of content we were aiming for on Dev. So, from Monday the 3rd of October onwards we will be taking a new approach, welcome to Pycraft’s weekly summary! Here we will be taking the highlight moments from the last week in Pycraft and summarising it into one post.

We kicked off the start of the week, on Monday the 3rd of October, with a continuation of the restructuring process.
For those unfamiliar the restructuring of Pycraft v0.9.3 started with the completion of Pycraft v0.9.6-2.0 (the settings update, part 1), as it was at this time that we realised that it as all well and good improving the settings menu, but when other areas of Pycraft don’t apply these changes until Pycraft is restarted, it takes the shine off all that work. At the time we had two main problems, once you loaded the game engine once, changing Pycraft’s configuration would necessitate a full restart of the game, something that would quickly grow annoying. Our second major problem was Pycraft’s game engine wouldn’t behave as expected, even before the settings update there were some seriously game breaking bugs; we have listed a few here that have since been patched in Pycraft v0.9.6-3:
- Entering the inventory when in full-screen mode would display a blank image instead of the scene when you left the game engine.
- The events system was buggy, keys would remain pressed after they had been released by the user, and the controller compatibility was always terrible at best, suffering from some serious problems.
- When exiting the game, for example to use the Inventory or to leave, your mouse may not be ‘freed’ from the window, causing it to be stuck in an invisible box.
- When the game crashed (something that occurred too often) the window would often flicker, sounds would often play wrong (in a way that could hurt your ears), errors would not be properly logged and the window would repeatedly reopen, often hundreds of times before eventually closing.

All of these problems and more have been fixed by restructuring Pycraft’s game engine, in part because we made the decision then to also switch out the windowing engine from Pyglet to Pygame. Unfortunately, this came at a few costs, namely:

- The Inventory and Map GUIs would cause segmentation faults.
- The load screen was no longer operational.
- The performance of the game engine dropped by as much as 10x.

But the improved reliability of Pycraft now means that we managed to fix a lot of the bugs we mentioned earlier. The Inventory and Map GUIs where more complex to figure out, and this was when the restructuring of the game engine quickly turned into the restructuring of Pycraft entirely.
In order to get the Inventory to work we needed to run it in a separate process (not thread), and in order to do that we needed to remove Pycraft’s reliance on centrally loaded modules. In short this meant completely reprogramming large areas of Pycraft, clearing up a lot of useless subroutines in the process.
With that out the way we stepped back to look at our handy work and realised something. We didn’t add docstrings into Pycraft before this because every subroutine call went through some really complex system, now that this had been simplified somewhat, we where able to add in functional docstrings.
Adding docstrings into Pycraft was the work on the weeks leading up to, and including the 3rd, 4th and 5th of this week. Not very exciting.

Then, having completed a lot of the work we realised that the installer didn’t work either, which meant another bath of reprogramming, to firstly fix the installer, then add in Linux support, and finally docstrings and restructuring of that too.

All of that means that Pycraft is more stable, more reliable, better organised, easier for developers to understand, and also more PEP8 performant.

Now having done this we could start work on adding in some of the features that we were not able to at the release of Pycraft v0.9.6-2.5, including translations, a way to add custom themes, a way to enable festive features and a way to control the compilation of maths-based functions – and that’s just the settings menu! On the other hand, we have been working on getting the Inventory back to a working state, as well as the Map GUI. Both of these have been re-added, and we plan to work on the load screen between the main menu and the game engine soon. The end of the week was focused on adding a new widget to the settings menu, the dropdown menu to make choosing from a larger array of options easier.

It has been a busy week, we started with a mess of unstructured, unformatted code, and managed to shape that back into Pycraft, whilst making it better in the process! Thank you for reading 😊

This was more of a recap of the last few weeks of work, than what we have done in Pycraft this week, but we are going to adapt and improve our writing to find a style that works! Feel free to leave feedback!

Highlights from this week:


![Docstrings](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377343946/KO8A2wfn1.png)


![Pycraft's storage and permissions menu](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377345359/aR4f2KbEj.png)


![Pycraft's main menu](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377346906/Zi0o9jQV8.png)


![Pycraft's game engine](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377348257/LyV_gtu0d.png)


![Pycrafts installer](https://cdn.hashnode.com/res/hashnode/image/upload/v1673377349612/q-OzMrUh4.png)






