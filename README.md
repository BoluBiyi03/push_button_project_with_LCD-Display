# push_button_project_with_LCD-Display
## By 
[Oluwabiyi Boluwatife](https://github.com/BoluBiyi03)
## Date 
2nd May, 2024
# Introduction 
In this enchanting world we inhabit, where the delicate dance of technology and human ingenuity constantly unfolds, lies an invitation to embark on a transformative journey. With the Push Button Project, we transcend mere hardware and code, delving into the art of crafting experiences that resonate deeply with our souls. Here, amidst the symphony of electrons and pixels, we discover the profound beauty of creation, where each button press becomes a brushstroke on the canvas of our imagination. Join us as we navigate this wondrous realm, sculpting moments of wonder and delight with every flicker of the LCD display.

# Problem Statement 
In a world increasingly defined by seamless digital interactions, there exists a need for personalized, tangible interfaces that engage users in meaningful ways. Traditional push-button systems often lack the dynamic feedback and customization desired in modern interactive experiences. Therefore, the challenge is to design and implement a push button project utilizing **Arduino** microcontrollers and an **LCD display**, creating an intuitive interface that responds to user input with visually captivating feedback. The project aims to empower individuals to bridge the gap between physical and digital realms, fostering creativity and exploration in the realm of interactive electronics.
# Required Hardware 
The following hardware component listed below was used for the coupling and assembling of the **Push Button Project**;
1) Arduino
2) LCD Display 
3) LED 
4) Resistors
5) Jumper Wires 
6) Push Button 
7) Buzzer 
# Circuit Design 
[schematic capture](https://drive.google.com/file/d/1P8YhsyOVkNzbV_2taMwtE42rhHZmEIG8/view?usp=sharing)
# Source Code 
``` cpp
/*This is my project
By Oluwabiyi Boluwatife
Date - 18/04/2024
Title- Alertify: Interactive Emergency Alert System with Push-Button Activation
The purpose is to signal the user whenever the button is pressed 
It will also been displaced on the LCD Display and buzzer will aslo been turned on 
It helps to alert users during an emergency.
*/

#include <LiquidCrystal.h>

//Define the pins
const int buttonPin = 3;//Push button connected to pin 3
const int ledPin = 10;// Led connected to pin 10
const int buzzer = 12;//Buzzer connected to pin 12

//Variables to store the button state
int buttonState = 0;
int lastButtonState = 0;

//Variable for timing 
unsigned long lastDebounceTime = 0;
unsigned long debounceDelay = 50;

//Initialize the LCD
LiquidCrystal lcd(9, 8, 7, 6, 5, 4);

void setup()
{
  //Initialize the Leds and button pins
  pinMode(buttonPin, INPUT);
  pinMode(ledPin, OUTPUT);
  pinMode(buzzer, OUTPUT);

  //Initialize the LCD
  lcd.begin(16, 2);
  lcd.setCursor(0, 0);
  lcd.print("Emergency Alert");
}

void loop()
{
  //Read the state of the button
  int reading = digitalRead(buttonPin);
  
  //Check if the button state has changed 
  if (reading != lastButtonState)
  {
    //Reset the debounce timer 
    lastDebounceTime = millis();
  }

//Check if the debounce delay has passed 
  if ((millis() - lastDebounceTime) > debounceDelay)
  {
    //Update the button state only if it as been stable for the debounce delay
    if (reading != buttonState)
    {
      buttonState = reading;
      if (buttonState == LOW)
      {
        //If the button the pressed, turn on the LED
        digitalWrite(ledPin, HIGH);
        digitalWrite(buzzer, HIGH);
        lcd.setCursor(0, 1);
        lcd.print("Emergency Alert");
      }
      else
      {
        //If the buttont is released, turn off the LED 
        digitalWrite(ledPin, LOW);
        digitalWrite(buzzer, LOW);
        lcd.setCursor(0, 1);
        lcd.print("No Emergency");

      }
    }
  }
lastButtonState = reading;
}
```
# HEX File
[text]([text](../../../../Volumes/BOOTCAMP/Users/OBJ/Desktop/arduino/push_button_with_lcd_sketch/push_button_with_lcd_sketch.ino))
# Advantages 
1) **Hands-On Learning**: The project provides a practical and hands-on learning experience for individuals interested in Arduino programming and hardware tinkering. Participants can gain valuable skills in wiring, coding, and interfacing electronic components.
2) **Customization**: One of the key advantages of the push button project is its potential for customization. Participants can tailor the project to suit their specific needs and preferences, whether it's adjusting the functionality of the buttons or designing unique visual feedback on the LCD display.
3) **User Interaction**: The project fosters user interaction through the use of push buttons, creating an intuitive interface for controlling electronic systems or displaying information. This can be particularly useful in applications such as home automation, gaming, or interactive art installations.
4) **Visual Feedback**: With the inclusion of an LCD display, the push button project offers visual feedback to users, enhancing the overall user experience. Participants can experiment with displaying various messages, graphics, or data on the LCD screen, adding a dynamic element to their projects.
5) **Problem-Solving Skills**: Participants can develop problem-solving skills as they troubleshoot issues and debug their projects. Working through challenges such as wiring errors or code bugs helps to build resilience and confidence in overcoming obstacles.
6) **Project Expansion**: The push button project serves as a foundation for further exploration and expansion. Once participants have mastered the basics, they can build upon their knowledge to create more complex projects or integrate additional sensors and components.
# Disadvantages 
1) **Complexity for Beginners**: For individuals new to Arduino programming and electronics, the push button project may initially seem complex. Understanding wiring diagrams, coding concepts, and troubleshooting issues can be challenging for beginners, potentially leading to frustration.
2) **Hardware Limitations**: The project's hardware components, such as the Arduino microcontroller and LCD display, may have limitations in terms of processing power, memory, and display capabilities. This could restrict the complexity of projects or the amount of data that can be displayed.
3) **Cost of Materials**: Acquiring the necessary materials for the push button project, including Arduino boards, push buttons, and LCD displays, can incur costs. For individuals on a tight budget, this may be a barrier to entry or limit the scope of experimentation.
4) **Technical Issues**: Like any electronics project, the push button project is susceptible to technical issues such as wiring errors, component failures, or software bugs. Troubleshooting these issues can be time-consuming and require a certain level of technical expertise.
5) **Limited Interaction**: While push buttons provide a tactile interface for user interaction, they may be less intuitive or versatile compared to other input methods such as touchscreens or voice commands. This could limit the types of interactions that can be implemented in projects.
6) **Learning Curve**: Mastering the skills required for the push button project, such as programming in Arduino IDE and understanding electronics principles, involves a learning curve. Some individuals may find the initial learning process daunting or may require additional resources to grasp concepts fully.
7) **Maintenance and Upkeep**: Over time, hardware components may degrade or require maintenance, especially in projects that are exposed to environmental factors such as dust or humidity. Regular upkeep and troubleshooting may be necessary to ensure the longevity of projects.
# Output
[schematic capture]()

[visual output]()
# Summary and Conclusion
The Push Button Project is an engaging and educational endeavor that explores the intersection of hardware tinkering and Arduino programming. Participants delve into the world of interactive electronics, learning how to wire up push buttons and an LCD display to an Arduino microcontroller.

The project offers numerous advantages, including hands-on learning opportunities, customization options, and user interaction through tactile interfaces and visual feedback. Participants have the freedom to experiment with different button layouts, display messages or graphics on the LCD screen, and explore various functionalities.

While the project presents exciting possibilities, it's important to consider potential disadvantages such as complexity for beginners, hardware limitations, and technical issues. However, with patience, perseverance, and a willingness to learn, participants can overcome challenges and unlock the project's full potential.

Overall, the Push Button Project serves as a gateway to creativity, empowering individuals to unleash their imagination and explore the exciting possibilities of interactive electronics. Through experimentation, problem-solving, and collaboration, participants gain valuable skills and insights that can be applied to future projects and endeavors.