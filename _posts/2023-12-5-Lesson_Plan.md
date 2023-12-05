Parallax and Scrolling Effects
Make a lesson and code around Parallax. Integrate ideas so they can be adapted by Teacher project. Add elements to improve transitions screens and backgrounds. Below are a couple of ideas, but there should be many more.

Use a transition effect to smoothly move from the start screen to the game screen, etc.
Overlaying Backgrounds
Implement a dual-layered background system where the primary background is static, and a passive background moves to create a parallax effect.
Adjust the opacity or blending mode to avoid shadows of screen moving over screen.
Association with Character Movement
Trigger the scrolling screen movement when the player reaches a specific x-coordinate.
Synchronize the screen scrolling speed with the player’s movement speed.
Consider incorporating easing functions for a smoother scrolling effect.

Resources

What is a parallax effect
17 unique websites with parallax scrolling effects

Plan:
Show examples parallax scrolling/what it is
Parallax scrolling → Different layers of backgrounds to create a sense of depth, so one thing is stationery while a background moves
Adds interest to an otherwise static website/game
Apple Website https://www.apple.com/airpods-pro/ 


Example code snippets of parallax
Process of getting parallax into game
Get background into game
resize images to be same, 754 x 331px
change class GameEnv
if(background) but with background 2
make a new canvas
12/1: Overlaying backgrounds
defined mountains as background image
mountains: { src: "/images/platformer/backgrounds/mountains.jpg"}
Added mountains as background2 to GameLevel constructor
new GameLevel( {tag: "hills", background: assets.backgrounds.hills, background2: assets.backgrounds.mountains, platform: assets.platforms.grass, player: assets.players.mario, tube: assets.obstacles.tube, callback: testerCallBack } );
Defined backgroundImg2 in GameLevel.js file
this.backgroundImg2 = gameObject.background2?.file;
Loaded backgroundImg2
const imagesToLoad = [];
       if (this.backgroundImg2) {
           imagesToLoad.push(this.loadImage(this.backgroundImg2));
       }
In //Prepare HTML with Background Canvas (if backgroundImg is defined) copy and paste backgroundImg statement except replace with backgroundImg2. IMPORTANT: place before backgroundImg if statement, or else will not be below it as a layer
if (this.backgroundImg2) {
               const backgroundCanvas = document.createElement("canvas");
               backgroundCanvas.id = "background";
               document.querySelector("#canvasContainer").appendChild(backgroundCanvas);
               const backgroundSpeedRatio = 0;
               new Background(backgroundCanvas, loadedImages[i], backgroundSpeedRatio);
               i++;
           }
adding actual parallax effect Change backgroundSpeedRatio to 1, make sure this is for background image 2
if (this.backgroundImg2) {
               const backgroundCanvas = document.createElement("canvas");
               backgroundCanvas.id = "background";
               document.querySelector("#canvasContainer").appendChild(backgroundCanvas);
               const backgroundSpeedRatio = 1;
               new Background(backgroundCanvas, loadedImages[i], backgroundSpeedRatio);
               i++;
           }
12/5 adding transition effect
Add keyframes, in this case fadein and fadeout change opacity and flashing makes button flash, fadein 2s, fadeout 3s, 4s; means 4s between fadein and fadeout
#startGame{
   animation: fadeout 1.5s, fadein 1.5s 0.5s;
}


#canvasContainer{
 animation: fadein 5s;
}


#toggleCanvasEffect{
 animation: flash 0.5s infinite;
}


@keyframes flash {
 50% {
   opacity: 0;
 }
}
@keyframes fadeout{
   from {opacity: 1}
   to {opacity: 0}
}


@keyframes fadein{
   from {opacity: 0}
   to {opacity: 1}
}

