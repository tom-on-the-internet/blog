---
title: Hack - Get to Know Your Browser
date: "2019-01-09"
---

**[A new version of Hack is in the works.]**

A couple months ago I started feeling self-concious about my command line Linux skills. There are levels to these things, you see, and I started feeling like I was stuck on level 2 or 3. I could navigate, update files, ssh into servers... but not too much else.

A trip to Reddit told me that there was a game called [Bandit](http://overthewire.org/wargames/bandit/) that can help you improve your command line skills. The game is simple. Each level requires you to log in to a server and find the password for the next level. Finding the password gets progressively harder, but along the way you learn about ssh, ncat, piping, archiving, permissions, bash scripts, git, passwords, and a lot more. I strongly recommend it to anyone who wants go learn a bit more about the command line.

## Time for a side project

Bandit inspired me to try and create a little hacking game of my own. I called it Hack. Hack is similar to Bandit in that each level is designed to make you learn something about how your browser works. Completing the level moves you to the next level until you complete the game. Hack is hidden in plain sight on the front page on this site. I hid it so that non developers wouldn't accidentally find it.

## What Hack teaches

Hack, in its current iteration, teaches four browser concepts.
1. You can inspect DOM elements and see how they are put together.
2. You can use all the JavaScript functions of any website you are on.
3. You can look at the responses in the network tab to see what data the server is giving you.
4. You can look at the requests in the network tab to see how the website is speaking to the server.

## Technical details

Hack is one of those projects that I thought would be a lot smaller than it turned out to be. Hack is just vanilla HTML, CSS and JS. I used ES6 classes to make creating levels easier. Each level class extends a base level class that contains much of the game logic. The audio is its own class and the terminal is, too. The radio is just a bunch of audio tags puppeteered by JavaScript. 

It's all pretty simple, but it also started to feel a bit unwieldy. Creating a new level is pretty easy because the code is extensible, but if I were to do it all over again I would use TypeScript and a front-end framework. TypeScript's abstract classes and object properties would have come in handy when creating the base level class. A framework would have helped with view encapsulation.

The back end of Hack is Laravel and the code isn't complicated. Some levels in Hack don't use the back end at all.
