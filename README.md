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
    - The early stages where I had no real idea exactly how to build the project, but I had an idea of what compnents will be needed including: batteries to power the boat, rf connection communicate between the RC controller and motors, motors to power the boat, and a microcontroller to program it.
    - I was very much on the edge of my comfort zone where I had an idea of how to go about it, but trusted in my intuition and judgement to make it happen.
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

*Figure 3: bare bones prototype of the motor control system*

- [Go to code file for RC controller](./RC.ino/)
- [Go to ino file for motor controller](./Motors.ino/)

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
