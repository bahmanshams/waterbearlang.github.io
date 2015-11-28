---
layout: post
title: How To Make A Simple Game In Waterbear
author: Samuel Massinon
---

Making a game can be hard. There's so many pieces inside of the simplest game that trying to do it with no prior experience can be near impossible. That's why I am making this guide. A tutorial can help you tackle this challenge. I will be making the game of pong, but if you want to make another game you can easily take the lessons here and apply it to your project.

I assume you have some familiarity with the waterbear language, enough to know where to find blocks and how to use them. I will only be showing the script as I create my game.

## Make Some Pieces

In this game of pong, there will be 2 blocks on the left and right side, and a pong somewhere between them. This part we will create two blocks and a rectangle.

Start with making a player block. To make this follow these steps:

1. Grab the sprite with block and drop it on your script.
    - Sprites are images or shape that can move, spin, collide, and other neat stuff. 
2. Now grab the rectangle shape block and drop it into the sprite with block.
    - We are going to make our sprite a rectangle.
3. Add the properties to the rectangle block.
    1. Place a `zero vector <0,0>` into the first property.
    2. Put a width of `20`.
    3. Make the height `100`.
4. Make the name of the block `player 1`.
    - Now, whenever you are using the variable `player 1`, it means this sprite.

You should have the below now. Now do the same thing except for `player 2`. 

![Sprite]({{ site.baseurl }}/images/makingAGame/Sprite.png)

For the `pong`, do the same as above except for a rectangle block, use the circle block and give it a radius of `20`.

You should have this now,

![Sprites]({{ site.baseurl }}/images/makingAGame/Sprites.png)

## Place the Pieces

Now that you got your players and pong, you want to place them in the right spots. 

To give `player 1` a starting position on the left side, do the following:

1. Grab the move to block from sprites list and drop it on your script.
    - This block is how we tell sprites where to go.
2. Now grab the `player 1` variables and drop it into the move to block.
    - This mean we are telling the rectangle sprite `player 1` to move to somewhere.
3. Grab a vector at block from points list and drop it into the move to block.
    1. Put `10` into the x coordinate .
    2. Put the Center Y block into y coordinate.
    - Now `player 1` will now be placed on the left side in the middle.

You should have this now,

![MoveTo]({{ site.baseurl }}/images/makingAGame/MoveTo.png)

For player 2, you'll want to do the same as above *except* for the x coordinate. Since you want `player 2` on the right side, you'll need to grab some more blocks:

1. Grab the - (minus) block.
2. Place the Stage Width block in the first spot for the - (minus) block.
3. Enter `30` into the second part of the - (minus) block.
- Why I put `30` into the second part is because I want the block to be `10` away from the right side, and I need `20` because that's the width of `player 2`.

For `pong`, do the same as `player 1` but at step 3 just use the Center point block instead. Because I want it to start in the middle.

You should have this now,

![MoveTos]({{ site.baseurl }}/images/makingAGame/MoveTos.png)

## Display those Pieces

So far your script does a lot behind the scenes, but you aren't seeing anything from your hard work. Let's change that.

1. Grab the each frame block from the Controls list. 
    - This block is how we update the game. Everytime we start a new frame, we go through all the blocks in here.
2. Now take a clear to block from the Stage list and place it into the each frame block. Use the default black. 
    - This block will clear your game area on every frame so that old stuff is removed.
3. Grab two fill style blocks from Colors list under the clear to block and in the each frame block. 
    - One fill style will color your players and the other the pong. 
    - Give them whatever colors you want.
4. Now grab three draw blocks from the Sprites list. Place two of them under one of the fill styles block and the third under the other fill style block.
    - The sprites under one fill style will have a different color than the sprites under the other. 

Now you can hit run and see this,

![DrawPieces]({{ site.baseurl }}/images/makingAGame/DrawPieces.png)

Congrats! You can see the start of your great game!

## Moving pieces

Now lets get to the fun stuff. At the moment, your game is really just a cool picture. 

### Moving the Pong

You have to get the pong to move around. Luckly, that's pretty easy to do in waterbear. You'll need three following blocks:

1. Grab a set velocity to block and place it before the each from block.
    1. Place the `pong` sprite into the first part.
    2. Grab a x (multiply) block from the Points (Vectors) list.
        1. Place a random unit vector block into the first part.
        2. Give the second part a number, the higher the number, the faster the pong.
            - This will tell the sprite to move in a random direction with a certain speed you give it.
2. Grab the move block from the Sprite list and place it after the clear to block.
    1. Place the `pong` sprite into this block.
        - This will update your sprite to move at the speed and direction you gave it above. Your pong will not move without this.
3. Also put a bounce at edge block from the Sprite list at the bottom of the each frame block.
    - Your pong will fly of the board without this. 

It should look like this,

![MovingPieces]({{ site.baseurl }}/images/makingAGame/MovingPieces.png)

Hit run to see the pong flying all over the place!

### Moving the Players

With the pong, we can just set it's velocity and leave it. Players are a little different. They should only move when we tell them. Luckily, there's a few blocks designed just for that.

Follow these steps for moving player 1 around:

1. Grab a set block from the control list and place it after the bounce at edge block. Give it the name `speed` and give it a number; I gave it the number `10`. 
    - This will determine how fast a play can move.
2. Get a set velocity block from sprites list and drop it after the set block from step 
    1. Put `player 1` in the sprite part.
    2. Grab a vector at angle block from the points list and place it in the points part.
        1. Give it an angle of `0`.
        2. Give it a magnitude of `0`.
            - This block will be used to stop moving your block unless you tell it to.
3. Grab an if block from the control list, and place it after the block in step 2.
    1. Grab a key pressed? block from inputs list and drop it into the if boolean spot.
        1. Which input key do you want `player 1` to move on? I choosed `w`.
    2. Now do the same as step 2 above, where we set the velocity of player 1.Except, this time we are going to tell the `player 1` to move up.
        1. Give it an angle of `270`, which means up.
        2. Give it a magnitude of `speed`.
            -  The if block means that only when something is true, the block in there will be used. In this case, if you are pressing on the key `w`, the `player 1` will move up.
4. Now do the same thing in step 3, except we want `player 1` to move down.
    1. Change the input key to something different that above. I did `s`.
    2. Give it an angle of `90`, which means down.
        - This block will tell `player 1` to move down when the player is pressing the `s` key.
5. Now if you remember from getting the pong to move, it is very important that we grab a move block from the sprite list, and place it after the the move block for pong.
    - If you skip this nothing will happen.

Now you should have these in your program.

![MovingPlayer1_1]({{ site.baseurl }}/images/makingAGame/MovingPlayer1_1.png)

![MovingPlayer1_2]({{ site.baseurl }}/images/makingAGame/MovingPlayer1_2.png)

Now hit run and press `w` and `s` and see player 1 fly up and down.

You'll want to do the same thing for `player 2`, but pick different keys. I used the `up` and `down` keys.

![MovingPlayer2_1]({{ site.baseurl }}/images/makingAGame/MovingPlayer2_1.png)

![MovingPlayer2_2]({{ site.baseurl }}/images/makingAGame/MovingPlayer2_2.png)

## Bouncing Pong off Players

Now you got a great game that moves around, the pong goes right through the players! That's no good. Let's change that. In the game of pong, when the pong makes contact with the player, it should go in the opposite direction. So let's make that happen.

1. Grab another if block from controls list and place it at the bottom of the each frame block.
    1. You'll want to grab an is collision block from the sprite list.
        1. Put `player 1` in the first slot.
        2. Put `pong` in the second slot 
            - This will tell the if block to use the blocks inside if `player 1` and `pong` sprites are touching.
    2.  Take the degree block from the math list and place it at the start of the if block.
        1. Grab a get velocity block from sprites list and place it in degrees block.
            1. Put pong into get velocity block.
        2. Call the set block `degree`.
        - This block tell you the angle the pong is at when it collides.
    3. This part is a bit confusing, but just trust me on the math. We want the pong to bounce off the player, so we need to give it a different angle. This is the calculating I'm using `180 - degree`. This should mirror the pong except the other way.
        1. Grab a - (minus) block from math and place it after `degree`.
            1. Put `180` into the first part.
            2. Put `degree` in the second part.
            3. Call this block `angle`.
    4. Grab a set velocity block and place it after `angle`.
        1. Place `pong` into the first part.
        2. Grab a vector at angle block from vectors list and put it into the second part.
            1. Put `angle` into the first part.
            2. Give it a magnitude you want, I choose `7`.
            - When this blocks is used, your `pong` will go in a different direction.

This is what it should look like.

![Bouncing_1]({{ site.baseurl }}/images/makingAGame/Bouncing_1.png)

Try it out, and you'll see that the `pong` doesn't go through `player 1` anymore.

For `player 2`, the math is the same. So it makes sense to run the same if block for `pong` colliding with `player 1` for `player 2`. Instead of making a nearly identical block, just use a conditional statement.

1. Grab the collision block in the if statement and place it somewhere out of the way.
2. Grab an or block from the boolean list and place it into the if statement.
    1. Grab the collision block you set aside and place it in the first or slot.
    2. Take another collision block from the sprites list and place it into the second slot.
        1. Put the `player 2` sprite into the first part.
        2. Place the `pong` sprite into the second part.
        - We are using this or to say we use everything in this if block if either collision after.

It should look like this now.

![Bouncing_2]({{ site.baseurl }}/images/makingAGame/Bouncing_2.png)

So now, collision will happen whenever the `pong` hits either player. 

## Fin

That's it! You made your own game of two player pong!

Now the best part is that you can add your own magic to make the game even better. You can make it so that the pong goes a faster overtime. You can add a scoreboard. You can add whatever you can think of!
