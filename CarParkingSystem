#include<Servo.h>
int servopin=2;
int irpin=3;
Servo myservo;
int pos=0;

int trig1=4;
int echo1=5;

int trig2=6;
int echo2=7;

int trig3=8;
int echo3=9;
bool a=false;
bool b=false;
bool c=false;
#include <SPI.h>
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define SCREEN_WIDTH 128 // OLED display width, in pixels
#define SCREEN_HEIGHT 64 // OLED display height, in pixels

// Declaration for an SSD1306 display connected to I2C (SDA, SCL pins)
#define OLED_RESET     -1 // Reset pin # (or -1 if sharing Arduino reset pin)
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);


void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  myservo.attach(servopin);
  pinMode(irpin,INPUT);
  
  myservo.write(0);
  

  pinMode(trig1,OUTPUT);
  pinMode(echo1,INPUT);
  digitalWrite(trig1,LOW);

  pinMode(trig2,OUTPUT);
  pinMode(echo2,INPUT);
  digitalWrite(trig2,LOW);

  pinMode(trig3,OUTPUT);
  pinMode(echo3,INPUT);
  digitalWrite(trig3,LOW);
  lcd();
}

void loop() {
  // put your main code here, to run repeatedly:
  a=false;
  b=false;
  c=false;
  
  servofunc();
  ultra1();
  ultra2();
  ultra3();
  if(((a && b) && c)){
    
    display.setTextSize(2); // Default text size
    display.setTextColor(SSD1306_WHITE); // Set text color to white
    display.setCursor(0,0);
    display.println("*PARKING*");
    display.display();
    display.setCursor(0,18);
    display.println("FULL");
    display.display();
    delay(1500);
    
    display.clearDisplay();
  }
}

void servofunc(){
  int sensorstatus=digitalRead(irpin);
  if(sensorstatus==HIGH)
  {
    myservo.write(90);
    delay(1000);

  }
  else{
    myservo.write(0);
    delay(1000);
  }
}
void lcd(){
    if(!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) { 
    Serial.println(F("SSD1306 allocation failed"));
    for(;;); // Don't proceed, loop forever
  }

  // Show initial display buffer contents on the screen --
  // the library initializes this with an Adafruit splash screen.
  display.display();
  delay(2000); // Pause for 2 seconds

  // Clear the buffer
  display.clearDisplay();

  // Draw a single pixel in white
  display.drawPixel(10, 10, WHITE);

  // Show the display buffer on the screen. You MUST call display() after
  // drawing commands to make them visible on screen!
  display.display();

  display.setTextSize(2); // Default text size
  display.setTextColor(SSD1306_WHITE); // Set text color to white
  display.setCursor(8,10);
  display.println("WELCOME");
  display.display();
  display.clearDisplay();
  
}
void ultra1(){
  
  digitalWrite(trig1,HIGH);
  delay(10);
  digitalWrite(trig1,LOW);
  int duration1=pulseIn(echo1,HIGH);
  int distance1=0.352*duration1/2;
  Serial.println(distance1);

  if(distance1>50){
          
    display.setTextSize(2); // Default text size
    display.setTextColor(SSD1306_WHITE); // Set text color to white
    display.setCursor(0,0);
    display.println("*PARKING*");
    display.display();
    display.setCursor(0,18);
    display.println("PARKING 1 is empty");
    display.display();
    delay(1500);
    
    display.clearDisplay();
    }
    else{
    a=true;     
    display.setTextSize(2); // Default text size
    display.setTextColor(SSD1306_WHITE); // Set text color to white
    display.setCursor(0,0);
    display.println("*PARKING*");
    display.display();
    display.clearDisplay();
    }
}
void ultra2(){
    
  digitalWrite(trig2,HIGH);
  delay(10);
  digitalWrite(trig2,LOW);
  int duration2=pulseIn(echo2,HIGH);
  int distance2=0.352*duration2/2;
  Serial.println(distance2);
  if(distance2>50){
    
    display.setTextSize(2); // Default text size
    display.setTextColor(SSD1306_WHITE); // Set text color to white
    display.setCursor(0,0);
    display.println("*PARKING*");
    display.display();
    display.setCursor(0,18);
    display.println("PARKING 2 is empty");
    display.display();
    delay(1500);
    
    display.clearDisplay();
    }
    else{
    b=true;
    display.setTextSize(2); // Default text size
    display.setTextColor(SSD1306_WHITE); // Set text color to white
    display.setCursor(0,0);
    display.println("*PARKING*");
    display.display();
    display.clearDisplay();
    }

}

void ultra3(){
  
  digitalWrite(trig3,HIGH);
  delay(10);
  digitalWrite(trig3,LOW);
  int duration3=pulseIn(echo3,HIGH);
  int distance3=0.352*duration3/2;
  Serial.println(distance3);

  if(distance3>100 || distance3<0){
          
    display.setTextSize(2); // Default text size
    display.setTextColor(SSD1306_WHITE); // Set text color to white
    display.setCursor(0,0);
    display.println("*PARKING*");
    display.display();
    display.setCursor(0,18);
    display.println("PARKING 3 is empty");
    display.display();
    delay(1500);
    
    display.clearDisplay();
    }
    else{
    c=true;    
    display.setTextSize(2); // Default text size
    display.setTextColor(SSD1306_WHITE); // Set text color to white
    display.setCursor(0,0);
    display.println("*PARKING*");
    display.display();
    display.clearDisplay();
    }
}
