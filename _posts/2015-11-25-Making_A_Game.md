---
layout: post
title: How To Make A Simple Game In Waterbear
author: Samuel Massinon
---

Making a game can be hard. There's so many pieces inside of the simplest game that trying to do it with no prior experience can be near impossible. That's why I am making this guide. A tutorial can help you tackle this challenge. I will be making the game of pong, but if you want to make another game you can eaily take the lessons here and apply it to your project.

I assume you have some familiarity with the waterbear language, enough to know where to find blocks and how to use them. I will only be showing the script as I create my game.

## Make Some Pieces

In this game of pong, there will be 2 blocks on the left and right side, and a pong somewhere between them. This part we will create two blocks and a rectangle.

Start with making a player block. To make this follow these steps:

1. Grab the sprite with block and drop it on your script.
2. Now grab the rectangle shape block and drop it into the sprite with block.
3. Add the properties to the rectangle block.
    - Place a `zero vector <0,0>` into the first property.
    - Put a width of `20`.
    - Make the height `100`.
4. Make the name of the block `player 1`.

You should have the below now. Now do the same thing except for `player 2`. 

![Sprite]({{ site.baseurl }}/images/makingAGame/Sprite.png)

For the `pong`, do the same as above except for a rectangle block, use the circle block and give it a radius of `20`.

You should have this now,

![Sprites]({{ site.baseurl }}/images/makingAGame/Sprites.png)

## Place the Pieces

Now that you got your players and pong, you want to place them in the right spots. 

To give `player 1` a starting position on the left side, do the following:

1. Grab the move to block and drop it on your script.
2. Now grab the `player 1` variables and drop it into the move to block.
3. Grab a vector at block and drop it into the move to block.
    - Put `10` into the x coordinate .
    - Put the Center Y block into y coordinate.

You should have this now,

![MoveTo]({{ site.baseurl }}/images/makingAGame/MoveTo.png)

For player 2, you'll want to do the same as above *except* for the x coordinate. Since you want `player 2` on the right side, you'll need to grab some more blocks:

1. Grab the - (minus) block.
2. Place the Stage Width block in the first spot for the - (minus) block.
3. Enter `30` into the second part of the - (minus) block.

Why I put `30` into the second part is because I want the block to be `10` away from the right side, and I need `20` because that's the width of `player 2`.

For `pong`, do the same as `player 1` but at step 3 just use the Center point block instead.

You should have this now,

![MoveTos]({{ site.baseurl }}/images/makingAGame/MoveTos.png)

## Display those Pieces

So far your script does a lot behind the scenes, but you aren't seeing anything from your hard work. Let's change that.

1. Grab the each frame block from the Controls list. This block is how we update the game.
2. Now take a clear to block from the Stage list and place it into the each frame block. Use the default black. This block will clear your game area on every frame so that old stuff is removed.
3. Grab two fill style blocks from Colors list under the clear to block and in the each fram block. One fill style will color your players and the other the pong. Give them whatever colors you want.
4. Now grab three draw blocks from the Sprites list. Place two of them under one of the fill styles block and the third under the other fill style block.

Now you can hit run and see this,

![DrawPieces]({{ site.baseurl }}/images/makingAGame/DrawPieces.png)

Congrats! You can see the start of your great game!

## Moving pieces

Now lets get to the fun stuff. At the moment, your game is really just a cool picture. You have to get the pong to move around.

Luckly, that's pretty easy to do in waterbear. You'll need three following blocks:

1. Grab a set velocity to block and place it before the each from block.
    - Place the `pong` sprite into the first part.
    - Grab a x (multiply) block from the Points (Vectors) list.
        + Place a random unit vector block into the first part.
        + Give the second part a number, the higher the number, the faster the pong.
2. Grab the move block from the Sprite list and place it after the clear to block.
    - Place the `pong` sprite into this block.
3. Also put a bounce at edge block from the Sprite list at the bottom of the each frame block.

It should look like this,

![MovingPieces]({{ site.baseurl }}/images/makingAGame/MovingPieces.png)

Hit run to see the pong flying all over the place!

## Moving the Players

With the pong, we can just set it's velocity and leave it. Players are a little different. They should only move when we tell them. Luckily, there's a few blocks designed just for that.

Follow these steps for moving player 1 around:

1. Grab a set block from the control list and place it after the bounce at edge block. Give it the name `speed` and give it a number; I gave it the number `10`. This will determine how fast a play can move.
2. Get a set velocity block from sprites list and drop it after the set block from step 1. This block will be used to stop moving your block unless you tell it to.
    1. Put `player 1` in the sprite part.
    2. Grab a vector at angle block from the points list and place it in the points part.
        1. Give it an angle of `0`, which means up.
        2. Give it a magnitude of `0`.

