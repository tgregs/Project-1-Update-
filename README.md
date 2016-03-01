float sunX, sunY; //variables for sun
float xGold, yGold; //position of gold
float xPhil, yPhil; // position of phil
float r,g,b,a; // variables for colors
float dx,dy; // variables for random gold position
float score; 

void setup() {
  size(600, 600);  //screen size
  reset();
  dx = random(width);
  dy = random(height);
} 
void reset(){
  
  sunX=  width/2;   // Reset the sun position.
  sunY= random (200, 250);
  score = 0;
}
  

void draw() {
   
  scene(); //calls the scene function
  randomColor(); //calls the random color function
  messages(); //calls the messages function 
  action(); //calls the action function
  gold(); // calls the gold funtion
  phil(); //calls the hero function
 
}
  
  void scene(){
    background(0, 175, 255);//background color
    fill(0, 200, 0); //green grass rectangle color
    rect(0, 350, 600, 300); //rectangle size
    //SUN
    fill(255, 255, 0); //sun color
    ellipse( sunX, sunY, 30, 30 );   // Yellow sun 
    //HOUSE
    fill(255, 0, 0 ); // house color 
    rect(200, 300, 100, 50 ); //house size
    triangle( 190, 300, 310, 300, 250, 250 );  // roof size
    fill(218,165,32);//door color
    rect(235,310,25,40); //door size
    fill(240,248,255); // window color
    rect(210,310,20,20); // window left
    rect(265,310,20,20); //window right
    //Tree
    fill(139,69,19);
    rect(400,250,30,100);
    fill(0,100,0);
    ellipse(415,250,70,70);
  }
  void phil(){
    fill(255,69,0); // body color
    rect( xPhil,yPhil, 35, 60 ); // hero body
    fill(255,228,181); //head color
    ellipse( xPhil+18,yPhil, 40, 40 ); // head on top
    fill(0,0,0);
    text( "PHIL", xPhil+5,yPhil+40 ); //name
    // eyes.
    fill( r,g,b,a );
    ellipse(xPhil+10,yPhil-5 , 12, 12 );
    ellipse(xPhil+25,yPhil-5, 12, 12 );
   //legs  
    fill(160,82,45);
    rect( xPhil,yPhil+60,10,40 ); //left leg
    rect( xPhil+25,yPhil+60,10,40 ); //right let
   //arms
   fill(160,82,45);
    rect( xPhil-10,yPhil,10,30 ); //left arm
    rect( xPhil+35,yPhil,10,30 ); //right arm
    
  }
  void action(){
    sunX = sunX + 1; //add 1 to position of sun
    if (sunX > width){
    sunX=  0;
    sunY=  random( 200, 220 ); // randomly changes the height of the sun
    }
    xPhil = xPhil + (xGold-xPhil)/15; // moves phil to gold x axis 
    yPhil = yPhil + (yGold-yPhil)/15; // moves phil to gold y axis  
    
  
    
      score = score + 100;
    } 
  
  
  void randomColor(){
  r = random(255);
  g = random(255);
  b = random(255);
  a = random(255); 
  }
  
  void messages(){
    fill(0);
    text(" Your score is:"+score,10,10 ); // displays the score 
  }
  void gold(){
    fill(218,165,32);
    ellipse( xGold, yGold, 40,40 );
    fill(255,25,0);
    ellipse( xGold, yGold, 20,20 );
  }  
    
  void mousePressed(){
    xGold= mouseX;
    yGold= mouseY;
  }
  void keyPressed(){ 
    if (key == 's'){
    sunY= sunY + 50;
    }
    if (key == 'r'){
      reset();
  }
    if (key == 'q'){
      exit();
  }
  }
