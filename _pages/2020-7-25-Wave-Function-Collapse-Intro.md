---
layout: post
title: An Introduction to the Wave Function Collapse Algorithm
description: "Post 1 on the WFC algorithm."
keywords: "proc gen, quantum mechanics, game dev"
comments: true
---

You may or may not already be familiar with the wave function collapse algorithm (wfc from now on), but if you're not, here's a brief overview.

First developed in October 2016 by [Maxim Gumin](https://twitter.com/ExUtumno/), the [wfc algorithm](https://github.com/mxgmn/WaveFunctionCollapse) is a method of generating novel textures from a given input texture. The main reason this algorithm is interesting is that the output is locally similar to the input, as defined in the repository:
> Each NxN pattern of pixels in the output should occur at least once in the input. Distribution of NxN patterns in the input should be similar to the distribution of NxN patterns over a sufficiently large number of outputs. In other words, probability to meet a particular pattern in the output should be close to the density of such patterns in the input.

That essentially just means that the output looks like the input, but because it's procedurally generated it can be arbitrarily large and even generated on the fly. Here's an example of it in action from Maxim's repository:

![wfc gif](/assets/images/wfc.gif)

Pretty cool, right?

### My Project

If you're like me when you saw that gif, your first instinct would be to poke around and see if you could figure out how it works to make your own. In my experience however, while there are lots of great resources to learn generally how wfc works, there are far fewer in-depth analyses of the algorithm, its quirks, and the difficulties you might face trying to build your own version. The best resource, in my opinion, is [Isaac Karth](https://twitter.com/isaackarth) and [Adam M. Smith's](https://twitter.com/rndmcnlly) paper, [WaveFunctionCollapse is Constraint Solving in the Wild](https://adamsmith.as/papers/wfc_is_constraint_solving_in_the_wild.pdf), which provides a pretty detailed description of some of the main systems in the algorithm.

My goal (over an embarrassingly long span of time) has been to write my own implementation of the algorithm in the Lua language, with LOVE2D to make the graphics easier to handle. While I'm still not quite finished with the algorithm, in these posts I'll be explaining what I've done so far, the problems I've faced and the ways I solved them, and what I'm currently working on as I catch up to myself. All of that will include some actual code I've written (I apologize in advance for my atrocious formatting), and perhaps some diagrams and such depending on how artistic I'm feeling.

### Other Resources

Here are some good videos, articles, and papers which I've used in my own research:
- The [aforementioned paper](https://adamsmith.as/papers/wfc_is_constraint_solving_in_the_wild.pdf) by [Isaac Karth](https://twitter.com/isaackarth) and [Adam M. Smith](https://twitter.com/rndmcnlly)
- [Maxim Gumin's](https://twitter.com/ExUtumno/) [repository](https://github.com/mxgmn/WaveFunctionCollapse)
- [Oskar Stålberg's](https://twitter.com/OskSta) [talk](https://www.youtube.com/watch?v=0bcZb-SsnrA) at EPC2018 on how wfc works
- [Brian Bucklew's](https://twitter.com/unormal) [very interesting talk](https://www.youtube.com/watch?v=fnFj3dOKcIQ&t=1s) on using wfc in dungeon generation in [Caves of Qud](http://www.cavesofqud.com/) during the 2019 Roguelike Celebration, which I actually got to see in person!
- [Robert Heaton's](https://twitter.com/RobJHeaton) great article called ["The Wavefunction Collapse Algorithm explained very clearly"](https://robertheaton.com/2018/12/17/wavefunction-collapse-algorithm/)
