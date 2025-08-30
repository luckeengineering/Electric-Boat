# Portland Pudgy Project
An engineering project built for a boat company in Maine

https://github.com/user-attachments/assets/bc0ef08b-5a2e-4c46-ada0-7dc857ba6e61

https://github.com/user-attachments/assets/a14000be-332a-45c6-8daa-01f3b376f408

# 🚤 Portland Pudgy Development Timeline  

## 1. Where it began
- **What to include:**
  - This all began when I went to Mike the owner of Portland Pudgy looking for an engineering internship. Instead I struck the opportunity with Mike to work on an R&D project to build out an RC electric motor kit for the boats they sell. 
  - The opportunity here is that Currently there is no good remote control solution for turning your boat from gas powered to electric powered. This would be a unique selling point as no one has really done it yet. Also Portland Pudgy having their own unique custom electric boat motor kit would be a unique selling point compared to other electric boat motor kits like Torqueedo and ePropulsion make.
  - This mattered to me to create as it was an exciting and meaningful project as it steered towards reducing carbon emissions from boats, but also stimulated my engineering mind to solve a project using my electrical engineering know how that I was just starting to build while in schoool. This was a task that was certainly out of my comfortzone, but a welcome challenge to really build up my engineering skillset. 

---

### 📍 Phase 1: Concept & Research  
- **Situation:**
    - The early stages where I have no real idea what the project will need for components besides batteries to power the boat, rf connection communicate between the RC controller and motors, motors to power the boat, and a microcontroller to program it. I was very much on the edge of my comfort zone where I had an idea of how to go about it, but trusted in my intuition and judgement to make it happen.
- **Task:**
    - First thing to do at this point is start researching previous engineering projects and parts for this project to get familiar.
- **Action:**
    - I tackled the hardest problem first being the RF communcation from the remote control to the motors, solving this first would be critical as without it we can't create an RC boat.
- **Result:** [Outcome, lesson, or milestone achieved]  
## 2. Task  
  - When it comes to starting projects I like to start them like how I like to start my day by doing the hardest part first. Which in this case was figuring out the remote control part.
  - To get myself familiar I got my hands on a pair of NRF24L01 Modules to figure out how to get them to communicate over radio frequencies.
![IMG_3540](https://github.com/user-attachments/assets/a51ecfae-a98a-4295-b162-865e6e3f34cb)
  - Eventually through a lot of trial and error I was able to create this C++ code for one side of the code to receive the data from the other one and interpret that data with an arduino
  - This code below is a part of the final code for the project so there is more than just the connection setup 
```cpp
#include<SPI.h>
#include "printf.h"
#include "RF24.h"
#include <Wire.h>

#define JOYSTICK_ADDR 0x40
#define CE_PIN 9
#define CSN_PIN 10

// instantiate an object for the nRF24L01 transceiver
RF24 radio(CE_PIN, CSN_PIN);
// Let these addresses be used for the pair
uint8_t address[][6] = { "pm117", "pc117"};
// It is very helpful to think of an address as a path instead of as an identifying device destination
// to use different addresses on a pair of radios, we need a variable to uniquely identify which address this radio will use to transmit
uint8_t radioNumber = 1; 
String bind = address[radioNumber]; // setting up our bind address
// Used to control whether this node is sending or receiving
bool role = true;  // true = TX role, false = RX role
int payload[] = { 100, 9, 9 };
int switchPin = 5;
unsigned long buttonPressStart = 0; // Cruise Control Start Time
const unsigned long holdTime = 5000; // 5 seconds in milliseconds
bool inCruiseMode = false; // set to manual control initially
int cruiseLED = 2; // Cruise contro LED pin
int switchPos;
int LeftMotorSpeed = 1500;
int RightMotorSpeed = 1500;
int TransistorBasePin = 3;

void setup() {

  Serial.begin(115200);
  while (!Serial) {
    // some boards need to wait to ensure access to serial over USB
  }

  Wire.begin();

  // initialize the transceiver on the SPI bus
  if (!radio.begin()) {
    Serial.println(F("radio hardware is not responding!!"));
    while (1) {}  // hold in infinite loop to signify it's not connecting
  }

  // Set the PA Level low to try preventing power supply related problems because these examples are likely run with nodes in close proximity to each other.
  radio.setPALevel(RF24_PA_LOW);  // RF24_PA_MAX is default.

  // save on transmission time by setting the radio to only transmit the number of bytes we need to transmit a float
  radio.setPayloadSize(sizeof(payload));  // float datatype occupies 4 bytes

  // set the TX address of the RX node into the TX pipe
  radio.openWritingPipe(address[radioNumber]);  // always uses pipe 0

  // set the RX address of the TX node into a RX pipe
  radio.openReadingPipe(1, address[0]);  // using pipe 1
  // in the future adjust the above for another ReadingPipe from the RC
  
  // additional setup specific to the node's role
  if (role) {
    radio.stopListening();  // put radio in TX mode
  } else {
    radio.startListening();  // put radio in RX mode
  }

  // For debugging info
  // printf_begin();             // needed only once for printing details
  // radio.printDetails();       // (smaller) function that prints raw register values
  // radio.printPrettyDetails(); // (larger) function that prints human readable data
  digitalWrite(switchPin, LOW);  // set LOW to detect HIGH signal from 
} 

void loop() {
  Wire.beginTransmission(JOYSTICK_ADDR);
  Wire.write(0x00);  // Register to start reading from
  Wire.endTransmission(false);

  Wire.requestFrom(JOYSTICK_ADDR, 2);  // Request 2 bytes (X and Y axis data from joystick)

  int inputRead = digitalRead(5);

  int PWM[3];
  bool report;

  switchPos = digitalRead(switchPin);
  Serial.print(switchPos);
  Serial.print(inCruiseMode);
   if (!inCruiseMode && switchPos) {
        // If button press just started, record the start time
        if (buttonPressStart == 0) {
            buttonPressStart = millis();
        }
        // Check if button is held for more than 5 seconds
        if (millis() - buttonPressStart >= holdTime && !inCruiseMode) {
            inCruiseMode = true; // Activate cruise mode
            digitalWrite(cruiseLED, HIGH); // Turn on cruise mode LED
            Serial.println("Cruise mode activated!");
            while (switchPos) {
              switchPos = digitalRead(switchPin);

              if (Wire.available() == 2) {
                  byte xData = Wire.read();  // Read X axis data
                  byte yData = Wire.read();  // Read Y axis data
                  //  X-axis (North-South)
                  if (xData <= 80) {  // East side
                      if (yData <= 80) {  // North-East 
                        LeftMotorSpeed = 2000; // set to static full throttle on left motor
                        RightMotorSpeed = map(xData, 0, 80, 2000, 1000);  // Map right motor speed 0-80 to 2000-1000
                      } else if (yData >= 175) {  // South-East side
                        LeftMotorSpeed = map(yData, 255, 175, 2000, 1000);  // Map left motor speed 255-175 to 2000-1000
                        RightMotorSpeed = 1000; // set to static full reverse on right motor
                      } 
                  } else if (xData >= 175) {  // West side
                      if (yData <= 80) {  // North-West side
                        RightMotorSpeed = 2000; // set to static full throttle on right motor
                        LeftMotorSpeed = map(yData, 0, 80, 1000, 2000);  // Map left motor speed 0-80 to 1000-2000
                      } else if (yData >= 176) {  // South-West side
                        RightMotorSpeed = map(xData, 255, 176, 1000, 2000);  // Map right motor speed 255-176 to 1000-2000
                        LeftMotorSpeed = 1000;  // set to static full reverse on left motor
                      }
                  }
                PWM[0] = RightMotorSpeed;
                PWM[1] = LeftMotorSpeed;
            }
              // blink the button led on
          }          
        }
    } else {
      buttonPressStart = 0;
    }
    // if user still happens to be holding button past 5 sec (which will happen) we need to be able to 
    // let go of joystick so it goes to a neutral position, but still stay at the LOCKED speed and rightLeft
    // perhaps we implement a timer that will start counting down to let the user have time to go back to neutral joystick position
    // or maybe the user is told to let go of joystick and then the button to allow it to go to neutral and be safe to stay
    // in cruise control. could add small time buffer after button release just to give some flexibility.
    // maybe have another button or something to add improved functionality?

    if (inCruiseMode && !switchPos) { // Cruise Control Constant Speed
      report = radio.write(&PWM, sizeof(PWM));
        if (report) {
          Serial.print(F("Transmission successful! "));  // payload was delivered
          Serial.print("Left Motor: ");
          Serial.println(PWM[0]);  // print payload sent
          Serial.print("Right Motor: ");
          Serial.println(PWM[1]);
        } else {
          Serial.println(F("Transmission failed or timed out"));  // payload was not delivered
        }
    } else if (inCruiseMode && switchPos) {
      inCruiseMode = false;
      digitalWrite(cruiseLED, LOW);
    }

  // This device is a TX node
  if (!inCruiseMode) {
    if (Wire.available() == 2) {
          byte xData = Wire.read();  // Read X axis data
          byte yData = Wire.read();  // Read Y axis data

          //  X-axis (North-South)
          if (xData <= 80 && xData > 0) {  // East side
              if (yData <= 80 && xData > 0) {  // North-East 
                LeftMotorSpeed = 2000; // set to static full throttle on left motor
                RightMotorSpeed = map(xData, 0, 80, 2000, 1000);  // Map right motor speed 0-80 to 2000-1000
              } else if (yData >= 175) {  // South-East side
                LeftMotorSpeed = map(yData, 255, 175, 2000, 1000);  // Map left motor speed 255-175 to 2000-1000
                RightMotorSpeed = 1000; // set to static full reverse on right motor
              } 
          } else if (xData >= 175) {  // West side
              if (yData <= 80) {  // North-West side
                RightMotorSpeed = 2000; // set to static full throttle on right motor
                LeftMotorSpeed = map(yData, 0, 80, 1000, 2000);  // Map left motor speed 0-80 to 1000-2000
              } else if (yData >= 176) {  // South-West side
                RightMotorSpeed = map(xData, 255, 176, 1000, 2000);  // Map right motor speed 255-176 to 1000-2000
                LeftMotorSpeed = 1000;  // set to static full reverse on left motor
              }
          } else {
            LeftMotorSpeed = 1500;
            RightMotorSpeed = 1500;
          }

          // Print the raw values from Joystick 0-80 and 255-175
          // Serial.print("X Raw: ");
          // Serial.print(xData);
          // Serial.print(" Right Motor: ");
          // Serial.print(RightMotorSpeed);

          // Serial.print(" | Y Raw: ");
          // Serial.print(yData);
          // Serial.print(" Left Motor: ");
          // Serial.println(LeftMotorSpeed);
    }

    PWM[0] = RightMotorSpeed;
    PWM[1] = LeftMotorSpeed;

    bool report = radio.write(&PWM, sizeof(PWM));  // transmit & save the report

    if (report) {
      Serial.println(F("Transmission successful! "));  // payload was delivered
      Serial.println(PWM[0]);  // print payload sent
      Serial.println(PWM[1]);
    } else {
      Serial.println(F("Transmission failed or timed out"));  // payload was not delivered
    }
  }

} 
```
---

## 3. Action (Timeline of Development)  


- **Situation:** Describe the initial ideas and inspirations.  
- **Task:** What you set out to figure out at this stage.  
- **Action:** How you researched, gathered requirements, and explored design options.  
- **Result:** Early insights that shaped your approach.  

---

### 📍 Phase 2: Early Prototyping  
- **Situation:** First steps moving from idea → hardware.  
- **Task:** Building small-scale prototypes to test feasibility.  
- **Action:** Breadboarding, wiring, experimenting with motor control, trial-and-error.  
- **Result:** Wins (and funny failures) that taught you what works in practice.  

---

### 📍 Phase 3: System Integration  
- **Situation:** Needing to connect subsystems (ESCs, batteries, thrusters, wireless).  
- **Task:** Get everything talking together reliably.  
- **Action:** Debugging, soldering, testing communication (e.g., NRF24L01, ESP32).  
- **Result:** A partially functional system — first time everything “came alive.”  

---

### 📍 Phase 4: PCB Design & Refinement  
- **Situation:** Prototype too messy / fragile for real use.  
- **Task:** Create a robust PCB to house the system.  
- **Action:** Designing in KiCad, selecting components, handling first board spin issues.  
- **Result:** A professional-looking board (with a few lessons learned from mistakes).  

---

### 📍 Phase 5: Waterproofing & Field Testing  
- **Situation:** Electronics must survive saltwater & rough handling.  
- **Task:** Make the system marine-proof.  
- **Action:** Testing waterproof enclosures, connectors, lanyards, wireless charging case.  
- **Result:** Successful water tests (or dramatic failures that led to better designs).  

---

### 📍 Phase 6: Iteration & Scaling  
- **Situation:** Adding advanced features (e.g., regenerative charging).  
- **Task:** Improve performance and add capabilities.  
- **Action:** Redesigning circuits, implementing smarter firmware, revisiting system constraints.  
- **Result:** Stronger, more capable system closer to real-world applications.  

---

## 4. Result  
- **What to include:**  
  - Tangible outcomes (working RC dinghy system, battery management success).  
  - Quantifiable performance metrics if available (runtime, charge efficiency, range).  
  - Skills gained: circuit design, embedded programming, waterproofing, testing.  
  - The project’s potential impact in sustainability/marine robotics.  

---

## 5. Reflection & Next Steps  
- **What to include:**  
  - Lessons learned about engineering, iteration, and persistence.  
  - Personal growth (problem-solving, project management, creativity).  
  - How this project connects to your career ambitions (BMS, marine robotics, renewable energy).  
  - Future development plans (improving, scaling, commercialization).  

---
