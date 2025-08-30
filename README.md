# Portland Pudgy Project
An engineering project built for a boat company in Maine

https://github.com/user-attachments/assets/bc0ef08b-5a2e-4c46-ada0-7dc857ba6e61

https://github.com/user-attachments/assets/a14000be-332a-45c6-8daa-01f3b376f408

# 🚤 Portland Pudgy Brief Overview of Development Timeline.

## 1. Where it began
- **What to include:**
  - This all began when I went to Mike the owner of Portland Pudgy looking for an engineering internship. Instead I struck the opportunity with Mike to work on an R&D project to build out an RC electric motor kit for the boats they sell. 
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
    - The original design tehcnicall speaking works, but having two throttle arms to control each motor independently was a bit cumbersome and awkward.
    - The case for the ESCs, batteries and arduino to control the motors needs to be more robust and capable of charging the batteries.
- **Task:**
    - Build a more ergonomic and easier to use remote control, and source a case with new batteries with built in charging circuitry and charge level monitoring
- **Action:**
    - I designed and sourced new parts to fit the new requirement for the remote control to be one handed and still work with the arduino as a microcontroller
    - Mike sourced the batteries, relay, kill switch, connectors and case for the motor controller side.
- **Result:**
    - Ended up with this new design for remote controller and motor controls case
  <img width="1200" height="846" alt="image" src="https://github.com/user-attachments/assets/6320a5a1-b578-4c39-ad6e-a727cebe4478" />

*Figure #: picture of both the RC and Motor Controls case in the lab*

https://github.com/user-attachments/assets/9eaa58ca-ce71-4e6e-a35c-d470198fcaeb



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
