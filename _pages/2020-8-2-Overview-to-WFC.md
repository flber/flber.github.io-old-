---
layout: post
title: A High-Level Overview of WFC
description: "Post 2 on the WFC algorithm."
keywords: "proc gen, quantum mechanics, game dev"
comments: true
---

With the assumption that you've either read the previous article on wfc or already know what it is, I'm just going to launch straight into an overview of the systems of the algorithm and how they operate together.

### Overview

My wfc implementation is made of four main systems. Mine are called the tile generator, the propagator constructor, the observer, and the propogator, and though other people may call them different things they make up the basis of how wfc works. They all act on or help to create the main data structure of wfc, the wave. The wave keeps track of which tiles can go in which spaces, and to begin with it starts as a totally "uncollapsed" wave, which means that every tile is allowed everywhere. Over the course of the algorithm's running, the four main systems will "collapse" the wave into a definite image.
Note: the word "collapsed" is taken from quantum physics, which this algorithm is loosely based on, and corresponds to the chance that any one tile will be in a space. For example, a fully collapsed space is one where there is only one possible tile. An uncollapsed space is one where every tile is possible. This also conencts to the idea of "entropy", which you can think of as how many possible options there are in a space. In the case of this algorithm there are also a few other things which affect the entropy value of a space, but I'll explain that more in another article.

Here's a rough overview of wfc's cycle:

Tile Generator  -->  Propagator Constructor  -->  Observer  --+
                                                     ^        |
                                                     |        V
                                                     +--  Propagator

- The tile generator does exactly what it sounds like: it generates tiles.
- The propagator contructor creates the data structure which the propagator will use to efficiently figure out which tiles will be allowed after a change (this won't make much sense now, but I'll explain it in more detail later).
- The observer starts each cycle of the wfc by picking the space with the lowest entropy (in the begining this is just random), and then picks a random possible tile to be in that space.
- The propagator updates the wave using the propagator structure, based on a list of spaces which have been changed, either by the observer or by the propagator in a previous update cycle.

I'll be writing an article on each of these in the future, with maybe a few extras to go over vocabulary, problems I've faced, and then however many more articles it takes before I've finished my own implementation.
