# Frogger
Frogger game
<!doctype html>
<html>
	<head>
    	<title>Frogger</title>
        <script type="text/javascript"src="easel.js"></script>
         <script type="text/javascript"src="sound.js"></script>
		<script src="http://code.createjs.com/easeljs-0.7.1.min.js"></script>
             
        <script type="text/javascript">
		var stage;
		var canvas;
		var Froger;
		var FrogerImg;
		var FrogerImg2;
		var moveRight=false;
		var moveLeft=false;		
		var moveUp=false;
		var moveDown=false;
		var speed = 10;
		function init(){
			canvas = document.getElementById("canvas");
				stage = new Stage(canvas);
				Ticker.setFPS(35);
				Ticker.addListener(window);
				FrogerImg = new Image();
				FrogerImg.onload = onFrogerLoaded();
				FrogerImg.src ="frogger.png";
			
				document.onkeydown = onKeyDown;
				document.onkeyup = onKeyUp;
		}
			function onKeyDown(e){
			if(!e){ var e = window.event;}
				switch(e.keyCode){
					//left
					case 37:moveLeft=true;moveRight = false;
					break;
					//right
					case 39:moveLeft=false;moveRight = true;
					break;
					//up
					case 38:moveUp=true;moveDown = false;
					break;
					//down
					case 40:moveUp=false;moveDown = true;
					break;
				}
			}
			function onKeyUp(e){
			if(!e){ var e = window.event;}
				switch(e.keyCode){
					//left
					//case 37:moveLeft=false;
						//break;
					//right
					//case 39:moveRight = false;
						//break;
					//up
					//case 38:moveUp=false;
						//break;
					//down
					//case 40:moveDown = false;
						//break;
					//case 32:doFire();
						//break;
					//left
					case 37: Froger.x -= speed; //moveLeft=true;moveRight = false;
					break;
					//right
					case 39: Froger.x += speed;//moveLeft=false;moveRight = true;
					break;
					//up
					case 38:Froger.y -= speed; //moveUp=true;moveDown = false;
					break;
					//down
					case 40: Froger.y += speed;//moveUp=false;moveDown = true;
					break;
				}
			}
			function checkMovement(){
				if(moveLeft){
					Froger.x -= speed;			
					if(Froger.x < 0){
						Froger.x= 640;	
					}
				}
				else if(moveRight){
					Froger.x += speed;
					if(Froger.x > 640){
						Froger.x= 0;	
					}
				}
				else if(moveUp){
					if(Froger.y - speed > 24){
						Froger.y -= speed;	
					}
				}
				else if(moveDown){
					if(Froger.y + speed < 415){
						Froger.y += speed;	
					}
				}
			}
			function distance(obj1,obj2){
				var diffX = obj2.x-obj1.x;
				var diffY = obj2.y-obj1.y;
				return Math.sqrt((diffX*diffX)+(diffY*diffY));
			}
			function randRange(min,max){
			return Math.floor(Math.random()*(max-min))+ min;
			}
			function tick(){
				//checkMovement();
				stage.update();
			}
			function onFrogerLoaded(){
				Froger = new Bitmap(FrogerImg);
				Froger.scaleX = .4;
				Froger.scaleY = Froger.scaleX;
				Froger.regX = Froger.image.width*.5 +65 ;
				Froger.regY = Froger.image.height*.5;
				Froger.x = 295;
				Froger.y = 420;
				stage.addChild(Froger);
			}
		</script>  
          </head>
    <body onload="init();"style="background-color:#666;">
    	<div id="wrapper"style="width:640px;height:480px;
        		 margin-left:auto; margin-right:auto;
                 background-color:#000000;border:5px ridge #cc8811">
       		<canvas id="canvas"width=640 height=480
        		 style= "margin-left:auto; margin-right:auto;">
             </canvas>
         </div>
     </body>   
</html> 
