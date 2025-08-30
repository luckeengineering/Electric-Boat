# Portland Pudgy Project
An engineering project built for a boat company in Maine

https://github.com/user-attachments/assets/bc0ef08b-5a2e-4c46-ada0-7dc857ba6e61

https://github.com/user-attachments/assets/a14000be-332a-45c6-8daa-01f3b376f408

# 🚤 Portland Pudgy Brief Overview of Development Timeline.

## 1. Where it began
- This began when I went to Mike the owner of Portland Pudgy looking for an engineering internship. Instead I struck the opportunity with Mike to work on an R&D project to build out an RC electric motor kit for the boats they sell. 
- The opportunity here is that Currently there is no good remote control solution for turning your boat from gas powered to electric powered. This would be a unique selling point as no one has really done it yet. Also Portland Pudgy having their own unique custom electric boat motor kit would be a unique selling point compared to other electric boat motor kits like Torqueedo and ePropulsion make.
- This mattered to me to create as it was an exciting and meaningful project as it steered towards reducing carbon emissions from boats, but also stimulated my engineering mind to solve a project using my electrical engineering know how that I was just starting to build while in schoool. This was a task that was certainly out of my comfortzone, but a welcome challenge to really build up my engineering skillset. 

---

### 📍 Phase 1: Research & Prototyping 
- **Situation:**
    - The early stages where I had no real idea exactly how to build the project, but I had an idea of what compnents will be needed including: batteries to power the boat, rf connection communicate between the RC controller and motors, motors to power the boat, and a microcontroller to program it.
    - I was very much on the edge of my comfort zone where I had an idea of how to go about it, but trusted in my intuition and judgement to make it happen.
  
  <img width="400" height="380" alt="image" src="https://github.com/user-attachments/assets/146db013-29ac-407a-8f6c-d80745037487" /> <img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/cdea9f0a-501a-4db8-85cc-809eddfaf786" />

  *Figure 1 and 2: a couple early stage drawings brainstorming concept designs*

- **Task:**
    - First thing to do at this point is start researching previous engineering projects and parts for this project to get familiar.
- **Action:**
    - I tackled the hardest problem first being the RF communcation from the remote control to the motors, solving this first would be critical as without it we can't create an RC boat.
<img width="400" height="600" alt="image" src="https://github.com/user-attachments/assets/5724b90e-cad5-4366-91d9-5db23db6739e" />

*Figure 1: Early RF module setup prototype.*

- Picked out hall effect sensors for the next step

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/645d3798-d35e-4803-90d9-29e1b4695a59" />

*Figure 2: soldering connector to hall effect sensor.*

- Then I created a prototype for the remote control handle to control the parallel dual motor system. Utilizing hall effect sensors to make sure the device stayed waterproof while reading the throttle angle to steer and change the speed of the boat.
- **Result:**
- Outcome was successful communication between the NRF24L01 modules and proper throttle angle readout from the sensors to the arduino nano.

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/90030db1-d89d-4033-9084-8c4ced8c5fbc" />

- Later I hooked up a joystick to test an alternative control method and demonstrated both the joystick and dual throttle handles working to control two motors over RF in the two video below

https://github.com/user-attachments/assets/e939c655-a342-40a1-9173-6da3d57cf0f0


https://github.com/user-attachments/assets/966d6bb1-3ce8-419e-9093-0f69fefe3af6


<img width="400" height="380" alt="image" src="https://github.com/user-attachments/assets/130476ad-b02b-46fd-8d14-11f9ed618ece" />


*Figure 3: bare bones prototype of the remote control system*

- [Go to code file for RC controller](./RC.ino/)
- [Go to ino file for motor controller](./Motors.ino/)

---

### 📍 Phase 2: Improving Remote controler  
- **Situation:**
    - The original design technically speaking works, but having two throttle arms to control each motor independently was a bit cumbersome and awkward.
    - The case for the ESCs, batteries and arduino to control the motors needs to be more robust and capable of charging the batteries.
- **Task:**
    - Build a more ergonomic and easier to use remote control, and source a case with new batteries with built in charging circuitry and charge level monitoring
- **Action:**
    - I designed and sourced new parts to fit the new requirement for the remote control to be one handed and still work with the arduino as a microcontroller.
    - Mike sourced the batteries, relay, kill switch, connectors and case for the motor controller side.
    - Below are some images and videos of the design process for the next remote control and motor control proto pcb.
    - 
### Creating the motor controller prototype PCB
*Component List*
- NRF24L01 module for receiving signals and connected through SPI to arduino
- Arduino Nano for transcribing NRF signal to the ESC through PWM
- 3 pin connectors for esc connectors

<img width="400" height="420" alt="image" src="https://github.com/user-attachments/assets/371bb9df-6d9b-4a8f-bad2-c567e7da3e4d" />

*Figure #: Bottom side of the motor controller prototype PCB*

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/f5b638da-4478-41bf-b68f-6fb749ca5c9e" />

*Figure #: Top side of the motor controller prototype PCB*

### Creating the remote control with its prototype PCB
*Component List*
- NRF24L01 for transmitting both motor speed data
- Arduino Nano for programming the controls
- USB C charging module for 3.7V LiPo battery
- AMS1117-3.3 3.3V linear regulator to provide constant power to the NRF24L01 module from the battery.


<img width="621" height="684" alt="image" src="https://github.com/user-attachments/assets/d324ccda-093f-4889-819b-bed1f0170f34" />

*Figure #: Planning out the connections before soldering*

<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/04d177e5-0afd-4dd3-af83-1b9201205a3a" />

*Figure #: Planning out the physical layout*

<img width="400" height="500" alt="image" src="https://github.com/user-attachments/assets/f70ec104-527c-4565-ae15-186174d085e0" />

*Figure #: Bottom side fully connected*

### Testing that it powers on properly

https://github.com/user-attachments/assets/1ca8e420-8746-4f1e-82d7-e80ea1a08b36


- **Result:**
    - Created a fully functional electric motor kit for the portland pudgy boat
   
  <img width="1200" height="846" alt="image" src="https://github.com/user-attachments/assets/6320a5a1-b578-4c39-ad6e-a727cebe4478" />

*Figure #: picture of both the RC and Motor Controls case in the lab*

### Video of the final product sending correct signal to motors.

https://github.com/user-attachments/assets/9eaa58ca-ce71-4e6e-a35c-d470198fcaeb

### Range testing batteries at 24V
- Found that at 24V the batteries can last roughly 50min
- Haven't tested at 12V yet

https://github.com/user-attachments/assets/fed265d4-b45e-4843-9327-b66bcf27dee5


### Opportunities for improvement
- Boat currently only works with the batteries in parallel making the motors powered at 12V. The 24V series battery hookup worked outside of water, but not in the water likely due to inrush current being too high to power through the water and cutting out the ESCs or perhaps the batteries themselves as they have short circuit protection built in.
- Custom PCB for the remote control to improve battery power supply to NRF24L01 so it has enough constant power to remove weird stuttering in connection.
- Custom BMS charging circuits for both the remote control and motor controls to improve power flow and get the motors to be powered at 24V for more powerful thrust in the water

### Attempt one at custom PCB design for the motor controls. This is being changed to an ESP32 and using KiCAD instead after this attempt at a PCB schematic.

<img width="400" height="350" alt="image" src="https://github.com/user-attachments/assets/c509c30d-4b0e-4005-8690-64e814b384a7" />


## Skills Gained!
- circuit design
- testing
- rapid prototyping
- working independently under the guidance of a seasoned engineer Mike
- soldering
- waterproofing
- learned about connectors, relays, charging, RF, batteries, buck and boost converters, and embedded communication protocols like I2C, SPI and PWM
- problem solving
- project management
- patience (especially with the NRF24L01 modules)
- part sourcing
- reading datasheets more effectively

---

## Reflection & Next Steps  
- Engineering is a lot of trial and error at times and can definitely test your patience, but by powering through with grit and tenacity, anything is possible.
- I learned a lot about the importance of iteration when it comes to prototyping and testing continously. I only included a small amount of all the photos and other problems I ran into, but there were a LOT of problems I ran into. Solving those problems was very rewarding and proved to myself that I can be an engineer.
** Next Steps **
- Design and order the custom PCB for the remote controller to get an idea of how to go about BMS circuits at a lower voltage then try to design the bigger motor 24V BMS circuitry.

** Already reverse engineering an electric lawnmower BMS circuit **
https://github.com/user-attachments/assets/1c880cf7-097f-4a7b-8667-faa390535135

** As well as a segway BMS circuit **
<img width="461" height="880" alt="image" src="https://github.com/user-attachments/assets/c302b465-6b88-44d0-ab4b-c4b1071777ec" />



  - Lessons learned about engineering, iteration, and persistence.  
  - Personal growth (problem-solving, project management, creativity).  
  - How this project connects to your career ambitions (BMS, marine robotics, renewable energy).  
  - Future development plans (improving, scaling, commercialization).  

---
