---
layout: post
title: How To Create Video Games(A Technical perspective)
subtitle: What goes into making a computer game?
date: 2021-01-27 03:45:00
background: /images/create_games/game_dev.jpg
---
So you've been playing computer games for a while and now you want to know how to make them?

Maybe just out of curiosity or you want to make games as a hobby, or you want to secure a career in the game development industry. Maybe you want to start your own [indie](https://en.wikipedia.org/wiki/Indie_game_development) game studio.

![](/startbootstrap-clean-blog-jekyll/images/create_games/playing_game.jpg){: width="600" height="350"}

I'm gonna lay more emphasis on the programming aspect and I assume that the reader does not know how to code but knows how to google stuff. If you know how to code but are still confused as to how games are being made, this will be helpful :)

There are 3 major roles in bringing a video game to life:

1. Design
2. Art
3. Programming

\[in that order (or not :) \]

The **Design** part is more like a pre-development stage. It involves no technical know-how whatsoever, its pure creativity. Game Design basically involves coming up with an idea for the game. The game story, what the game characters should look like, levels, scenes, UI/UX all go into the design phase.

![](/startbootstrap-clean-blog-jekyll/images/create_games/designer.jpg){: width="600" height="300"}&nbsp;*Typically, designers communicate with artists and programmers and tell them what to create.*

**Artists** basically create the game assets such as characters, animations, spritesheets(for 2D games), models(for 3D games), music, sound effects, scenes, platforms for platformer games. Creating game art basically involves a lot of creativity and skills.

![](/startbootstrap-clean-blog-jekyll/images/create_games/artist.jpg){: width="600" height="300"}

A game artist would typically use tools like Gimp, Spriter, Blender, Maya, FMOD etc

![](/startbootstrap-clean-blog-jekyll/images/create_games/acharcter.jpg){: width="600" height="300"}

Although most folks like to separate those who create graphical art from sound composers, but heck, art is art.

**Programming** involves writing some code that actually gives life to the game. It is the most important role creating a video game. Dictating the gameplay logic, polling for user input, creating the UI for the game are all accomplished with some code written by a programmer.

What you have read above is just a generally overview of what goes into creating a video game. But in reality if you are just some random guy/girl and you want to make games solo, taking all the responsibility, and you don't know where to start from, you're gonna have to really humble yourself by starting with very little things.

I'm afraid but you cannot *"make a game like NFS heat within 1 month"(not even one year sis/bro )*, calm down please. Many of these huge titles typically take about 5 years(give or take 3 years) for a team of teams of experts from various works to complete.

Start by learning how to program. And by that I mean actually understanding the concepts of computer programming and not just *sort of* knowing the syntax of a particular programming language without actually understanding the program flow.

Pick a programming language (in my opinion, [python](https://www.python.org/downloads/) is good for a start), learn the syntax and write a lot of programs, solve a lot of problems, write trivial CLI games like quiz, hangman, tic-tac-toe etc. Then pick another language (I recommend one with C-like syntax, if you don't know what I mean by C-like syntax, just learn C.)

If you have written a lot of programs and you no longer feel intimidated seeing code then you should write your first graphical game :)

Don't rush it please, keep it simple and continue being humble chief. I am not going to tell you which tool or framework exactly you should use or the game you should create but I will give you some opinions which you may not heed if you wish.

You can write a simple game like pong, tetris, breakout or something of that sort. You can use [pygame](https://www.pygame.org/)(python), [Phaser](https://phaser.io/)(Javascript), [Cocos2D](http://cocos2d.org/)(C++), [monogame](https://www.monogame.net/)(C\#), [libgdx](https://libgdx.badlogicgames.com/)(Java) etc. There are tons of tutorials on the internet about using each of these frameworks to create pretty awesome games. This [2D breakout game using pure JavaScript](https://developer.mozilla.org/en-US/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript) really made sense to me as a beginner. You could as well go traditional, [learn openGL](http://learnopengl.com/) or [directX](https://www.youtube.com/playlist?list=PLv8DnRaQOs5-ST_VDqgbbMRtzMtpK36Hy) and write a simplistic game using C/C++ entirely from scratch. You most likely cannot do these by yourself so you gotta know how to google stuff(it is very important\!). I expect that you are going to write your first graphical game by following the exact instructions of a tutorial, do not be too hard on yourself.

![](/startbootstrap-clean-blog-jekyll/images/create_games/runner.png){: width="300" height="600"}

*A 2D runner game made with libgdx*

After writing your first graphical game, you should now understand what actually makes a game "a game". Basically, you are only telling objects on your canvas/screen to update itself every few milliseconds in a **game loop** based on some criteria(user input and some trivial arithmetic operations), render(draw) the updated world on the screen and eventually dispose of objects which are no longer needed to prevent leakage of memory. The rest should be based on your technical creativity. You can follow a few more tutorials and then write a game entirely on your own.

~~~
initializeGameObjects()

//the game loop
while(!gameOverConditionIsMet){
    pollUserInput()
    updateGameWorld()
    checkStatesOfGameObjects()
    render()
    checkGameOverCondition()
}

dispose(objectsNoLongerOfUse)
~~~

If you have made a few trivial games and you are now getting bored, you may then proceed to start using some real game engines like [Unity](https://unity.com/) and when you feel really comfortable making games already, start making 3D games, but please do not leap, start small as usual(how about a 3D version of pacman, or you could just simulate a bouncing ball for a start).

These days you do not really have to worry about being alone as a game developer if you don't know how to make game art, music or what not. There are tons of free game assets online, from animation spritesheets to pre-rigged, animated 3D models and background music and sound effects.

If you don't know how to code at all and do not feel like learning some obscure programming syntax, don't fret, you can still make games, you will only have to understand the game logic. There are a lot of drag-and-drop tools with which you can quickly make something quite impressive within just a few minutes. There's [GameMaker](https://www.yoyogames.com/gamemaker), [GDevelop](https://gdevelop-app.com/), [Buildbox](https://www.buildbox.com/), [RPG Maker](http://www.rpgmakerweb.com/), [Adventure Game Studio](http://www.adventuregamestudio.co.uk/). The major reason why some people still prefer to script their games is because these no-code engines may not exactly give you full freedom to customise your game as you wish but it's just OK if you aren't looking to secure a career as a [Game Programmer](https://en.wikipedia.org/wiki/Video_game_programmer).

![](/startbootstrap-clean-blog-jekyll/images/create_games/programmer.jpg){: width="600" height="500"}

If you want to secure a career as a full-time Game Programmer, it is advised to go down to the roots of computer graphics and learn a language like C/C++ which gives you more control over system resources because games are performance-critical applications that rely on speed and efficient memory management. Many other scripting languages like Java, C\#, lua, etc have some sort of memory management like garbage collection but you do not have full control. [RayLib](https://www.raylib.com) is a good starting point for someone who really wants to understand how games are being programmed at the very core. You should learn some graphics programming APIs like [openGL](https://www.opengl.org/), [directX](https://en.wikipedia.org/wiki/DirectX), [vulkan](https://www.khronos.org/vulkan/) or [metal](https://developer.apple.com/metal/)(for iOS and mac). It is advised to learn openGL or directX first. Take your time to learn these as they are low-level technologies and not like regular programming. Being able to write a game or a game engine entirely from scratch without the help of any advanced software gives you an edge to work as a Game Programmer in [AAA](https://en.wikipedia.org/wiki/AAA_&#40;video_game_industry&#41;) companies. Some AAA companies use [Unity](https://unity.com/), [Unreal](https://www.unrealengine.com) or [Cryengine](https://www.cryengine.com/) so learning at least one of these will definitely avail you some opportunities.

There are institutions of high prestige that offer Game Development courses in programming, Design and Art. A very good example is [Digipen](https://www.digipen.edu/), they offer Bachelors and Masters Degrees, you can see that the Game Development industry is no joke at all.

![](/startbootstrap-clean-blog-jekyll/images/afortnight.jpg){: width="600" height="300"}&nbsp;*Fortnite and far cry were made using [unreal](https://www.unrealengine.com) and [cryengine](https://www.cryengine.com/) respectively.*

## Links And Resources

* Languages: [Python](https://www.youtube.com/watch?v=rfscVS0vtbw), [C++](https://www.learncpp.com/), [Java](https://docs.oracle.com/javase/tutorial/)
* Tutorials: [2D breakout game using pure JavaScript](https://developer.mozilla.org/en-US/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript), [OpenGL Tutorials](https://learnopengl.com), [DirectX Tutorials](https://www.youtube.com/playlist?list=PLv8DnRaQOs5-ST_VDqgbbMRtzMtpK36Hy)
* Free Game Assets: [KENNEY](https://www.kenney.nl/), [openGameArt](https://www.opengameart.org), [gameArt2D](https://www.gameart2d.com), [itch-io](https://www.itch.io/game-assets), [freeSound](https://freesound.org/browse/)
* 3D models: [free3D](https://www.free3d.com), [CGTrader](https://www.cgtrader.com), [mixamo](https://www.mixamo.com/)
