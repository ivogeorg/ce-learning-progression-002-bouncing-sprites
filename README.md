# CPE 1040 - Spring 2020
## Assignement 2: Bouncing Sprite

This is the second assignment for the Spring 2020 installment of the CPE 1040 - Intro to Computer Engineering course at MSU Denver.

### Overview
This assignment asks you to write a simple program using the "sprites" provided by the Game package in the micro:bit. It also asks you to make a video of your program running on your micro:bit, upload it to [Imgur](https://imgur.com/), and reference it in this [README](README.md).

### Requirements
#### 1. Game sprites
1. In [Makecode](https://makecode.microbit.org/), create a new project.
2. In the editor, select JavaScript. **Note:** Do not use Blocks!
3. In the box, where _Untitled_ is shown, write _bouncing-sprite_.
4. Open the micro:bit reference on the [Game](https://makecode.microbit.org/reference/game) page.
5. Look through the functions and examples in the **Sprites** section. You will use these functions to write the required program.
6. Play around: create a sprite, move it, turn it, etc. _Note: Use the `forever` loop so you can see repeated motion. Otherwise the program will run too quickly to the end, and you won't see anything._

#### 2. Bouncing sprite
1. Create a sprite.
2. Have it move and bounce of the walls forever.
3. On the pressing of button A, turn it 45°.
4. On the pressing of button B, place it at a new random (x, y) location.
5. When your program runs in the simulator, program the micro:bit.
6. Create a new JavaScript source file in this repository and copy over your program from the Makecode editor.

#### 3. Demo video on Imgur
1. Look at this [video](https://imgur.com/a/WYlc90q) for the expected behavior of your micro:bit program.
2. The website which opens is Imgur (read like _imager_), a popular social media destination for images and short videos.
3. Record a video (up to 60 seconds) of your own micro:bit running your program. Press the buttons to demonstrate the functionality. _Note: The easiest way is to get the mobile app and record the video with your phone. 
4. Paste the link to your video under the heading [Submission demo](#submission-demo) at the end of this [README](README.md).

#### 4. Program structure
1. Follow this program structure:
   ```
   #############################################################
   ##                                                         ##
   ##                                                         ##
   ##  1. Declare global variables, using the 'let' keyword.  ##
   ##                                                         ##
   ##                                                         ##
   #############################################################
   
   #############################################################
   ##                                                         ##
   ##                                                         ##
   ##  2. Handle button pressing events.                      ##
   ##                                                         ##
   ##                                                         ##
   #############################################################
   
   #############################################################
   ##                                                         ##
   ##                                                         ##
   ##  3. Define any additional functions you need.           ##
   ##                                                         ##
   ##                                                         ##
   #############################################################

   #############################################################
   ##                                                         ##
   ##                                                         ##
   ##  4. Put repetitive functionality in the forever loop.   ##
   ##                                                         ##
   ##                                                         ##
   #############################################################
   ```
2. Start perusing the [JavaScript reference for the micro:bit](https://makecode.microbit.org/javascript).

### Submission demo

My [demo video](https://imgur.com/your/demo/video/url/here) shows my micro:bit executing my program. _(Edit the URL in the parentheses of the hyperlink.)_
