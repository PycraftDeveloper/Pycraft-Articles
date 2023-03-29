---
title: "Pycraft progress report! 29/03/2023"
datePublished: Wed Mar 29 2023 17:15:42 GMT+0000 (Coordinated Universal Time)
cuid: clfty772c000209kv21nu8ehp
slug: pycraft-progress-report-29032023
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680105571652/fc5c8463-9784-4d57-a11e-5bca5d0ce795.png
tags: programming-blogs, python, python3, gamedev, pycraft

---

Hello there everyone! Its time for our weekly progress summary and this week was the first big test of the major changes we made to the way we work on updates, so in this article, we will be reflecting on how that transition went, and what we have been doing in this week of development!

For those unfamiliar, a week ago we made a major change to the way we worked on updates for Pycraft by sharing our progress to a dev branch on GitHub instead of only sharing code upon release. By doing this we can get much faster turnarounds on identified bugs and makes collaboration with other developers much easier. We have also made the entire GitHub repository more accessible by following a more commonly used structure and simplifying the repository considerably.

Now having recapped the work we did last week, this week we put that to the test and after a few days spent working out how to optimise our workflow to make the most of the adjustments, and to our surprise, Pycraft ran pretty much without fault through this transition, needing very little work to get to run, which is good news as it shows the added flexibility we introduced through the development on Pycraft v9.5.0 is working.

So all this meant we could get started on making improvements to Pycraft v9.5.0dev8 very quickly, so despite having allocated this week to get everything working, we were able to start making improvements early, and have already cleaned up many different areas of Pycraft, fixing 2 major bugs and making numerous behind the scenes improvements, like this change to the splash screen that we have also added, which we think makes Pycraft's startup look much cleaner:

![Pycraft's new splash screen](https://cdn.hashnode.com/res/hashnode/image/upload/v1680106610880/89fa9725-b85c-4098-b53c-ceab059d6b6f.png align="center")

Now, the main focus of Pycraft v9.5.0dev8 is to get the installer working and up to date, and so I think it would be wrong in talking about all the progress we have made without talking about the installer, which we have spent a large proportion of our week working on. Currently, we are updating the structure and design of the installer, and then from there, we will expand to support more features, like for example other operating systems. Expect the installer to become the focus of our progress over the next few weeks.

One final thing we would like to announce is that we are away next week, and subsequently, there will be no progress update next week - as we won't know what progress has been made - and we are currently unsure if the week after that we will have enough work done to discuss, so we might combine that into another two-week summary. Apologies for that!

Now, as we have been working on the installer this week, we are proud to share our progress here visually:

![Pycraft's initial install screen](https://cdn.hashnode.com/res/hashnode/image/upload/v1680109927170/dfaaf69e-82be-46d5-9a7e-b51803a106b5.png align="center")