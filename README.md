# 🚤 Portland Pudgy Project  
An engineering R&D project for **Portland Pudgy**, a boat company in Maine.  

## 📹 Final project videos

https://github.com/user-attachments/assets/bc0ef08b-5a2e-4c46-ada0-7dc857ba6e61

https://github.com/user-attachments/assets/a14000be-332a-45c6-8daa-01f3b376f408

---

# 🗂️ Development Timeline (Brief Overview)  

## 1️⃣ Where It Began  
- This project started when I approached **Mike, the owner of Portland Pudgy**, seeking an engineering internship. Instead of a traditional role, I was given the chance to work on an **R&D project**: creating a remote-controlled (RC) electric motor kit for their boats.  
- The opportunity: there is **no widely available RC solution** to retrofit boats from gas to electric propulsion. A custom electric kit from Portland Pudgy would be a **unique selling point** compared to others.  
- Why it mattered: this project combined **sustainability (reducing carbon emissions from boats)** with a challenging hands-on build that pushed me out of my comfort zone and helped me grow my engineering skill set.  

---

## 📍 Phase 1: Research & Early Prototyping  

### 🔎 Situation  
- At the start, I had only a rough idea of what components would be needed:  
  - 12V batteries to power the boat  
  - RF modules for remote communication  
  - Motors + ESCs for propulsion  
  - A microcontroller for programming and system integration  
- I was working at the **edge of my comfort zone**, but trusted my intuition and problem-solving to move forward.  

<p align="center">
  <img width="400" height="380" src="https://github.com/user-attachments/assets/146db013-29ac-407a-8f6c-d80745037487" />
  <img width="400" height="300" src="https://github.com/user-attachments/assets/cdea9f0a-501a-4db8-85cc-809eddfaf786" />
  <br>
  <em>✏️ Brainstorming sketches of early system concepts</em>
</p>

### 🎯 Task  
- Begin researching prior projects and parts to familiarize myself.  
- Establish basic **RF communication** between a controller and motors (the hardest and most critical problem to solve first).  

### ⚡ Action  
- Experimented with **NRF24L01 modules** to set up a working RF link.  
- Prototyped early connections and soldered **hall effect sensors** for waterproofing the throttle control.  

<p align="center">
  <img width="400" height="600" src="https://github.com/user-attachments/assets/5724b90e-cad5-4366-91d9-5db23db6739e" />
  <br>
  <em>🛰️ Early NRF24L01 RF module transmission testing to mimic the remote controller and motor controller</em>
</p>

<p align="center">
  <img width="400" height="400" src="https://github.com/user-attachments/assets/645d3798-d35e-4803-90d9-29e1b4695a59" />
  <br>
  <em>🔧 Soldering connectors to hall effect sensor</em>
</p>

- Built a **dual-throttle prototype remote control** using hall effect sensors to waterproof throttle inputs.  

<p align="center">
  <img width="400" height="400" src="https://github.com/user-attachments/assets/90030db1-d89d-4033-9084-8c4ced8c5fbc" />
  <br>
  <em>🎮 Barebones dual-throttle remote prototype</em>
</p>

- Also tested a **joystick-based controller** as an alternative method. Which actually turned into the choice for phase 2  

📹 Videos:

**Joystick Demo**  

https://github.com/user-attachments/assets/e939c655-a342-40a1-9173-6da3d57cf0f0

**Dual Motor Demo**  

https://github.com/user-attachments/assets/966d6bb1-3ce8-419e-9093-0f69fefe3af6


### ✅ Result  
- Achieved **successful RF communication** between controller and motors.  
- Verified **throttle angle readout** from hall effect sensors to Arduino.  
- Demonstrated both joystick and throttle handle input controlling motors.  

🔗 [View RC Controller Code](./RC.ino) - This is for the remote control transmitter

🔗 [View Motor Controller Code](./MotorController.ino) - This is for the receiver in the battery case to control the motors via 2 ESCs

---

## 📍 Phase 2: Improving the Remote & Motor Controls  

### 🔎 Situation  
- The first design worked but was **awkward to use** with two throttle arms.  
- The battery case including the motor controller also needed to be **robust**, with proper battery charging connections.  

### 🎯 Task  
- Build a **one-handed, ergonomic remote control**.  
- Source a new battery case and 2 12V batteries with a BMS charging circuit built in  

### ⚡ Action  

#### 🔲 Motor Controller Prototype PCB  
- NRF24L01 (SPI comms)  
- Arduino Nano (signal translation + PWM outputs)  
- 3-pin ESC connectors  

<p align="center">
  <img width="400" height="420" src="https://github.com/user-attachments/assets/371bb9df-6d9b-4a8f-bad2-c567e7da3e4d" />
  <img width="400" height="400" src="https://github.com/user-attachments/assets/f5b638da-4478-41bf-b68f-6fb749ca5c9e" />
  <br>
  <em>⚡ Motor controller prototype PCB (bottom + top views)</em>
</p>

#### 🎮 Remote Control with Prototype PCB  
- NRF24L01 for transmitting motor data  
- Arduino Nano for programming  
- USB-C charging module for 3.7V LiPo  
- AMS1117-3.3 regulator for RF stability  

<p align="center">
  <img width="400" height="400" src="https://github.com/user-attachments/assets/04d177e5-0afd-4dd3-af83-1b9201205a3a" />
  <img width="621" height="684" src="https://github.com/user-attachments/assets/d324ccda-093f-4889-819b-bed1f0170f34" />
  <br>
  <em>🔌 Mapping out connections before soldering</em>
</p>

<p align="center">
  <img width="400" height="500" src="https://github.com/user-attachments/assets/f70ec104-527c-4565-ae15-186174d085e0" />
  <br>
  <em>🛠️ Remote PCB soldered + fully connected</em>
</p>

**First Power-On Test**  

https://github.com/user-attachments/assets/1ca8e420-8746-4f1e-82d7-e80ea1a08b36

While I focused on the **remote control design**, Mike took on the motor controller hardware side.  
- **Mike’s role:** He sourced a new battery case and outfitted it with an integrated **relay, kill switch, and battery charging circuitry**, ensuring the system was rugged and safe.  
- **My role:** I designed and built a **one-handed, ergonomic remote control** with a custom PCB and power regulation to communicate reliably with the motors.  

Together, these efforts brought both halves of the system to life.  

### ✅ Result  
- Built a **fully functional RC electric motor kit** for the Portland Pudgy.  

<p align="center">
  <img width="1200" height="846" src="https://github.com/user-attachments/assets/6320a5a1-b578-4c39-ad6e-a727cebe4478" />
  <br>
  <em>🚤 Final lab setup: RC remote + motor controller cases</em>
</p>

**Final Signal Test**  

https://github.com/user-attachments/assets/9eaa58ca-ce71-4e6e-a35c-d470198fcaeb

**Battery Range Test @ 24V**  

https://github.com/user-attachments/assets/fed265d4-b45e-4843-9327-b66bcf27dee5

- Runtime: ~50 minutes at 24V  
- 12V performance: still testing


---

## 🔧 Opportunities for Improvement  
- Currently motors only run at 12V (parallel config). At 24V, the ESCs cut out under load in water — possibly due to **inrush current or battery protection circuits**.  
- Need a custom PCB for the remote to improve **NRF24L01 stability** (fix stuttering).  
- Design **custom BMS charging circuits** for both remote + motor controls.  
- Explore scaling up to 24V operation for stronger thrust.  

---

## 🧰 Skills Gained  
- Circuit design & debugging  
- Rapid prototyping  
- Soldering & waterproofing  
- Part sourcing & datasheet analysis  
- Embedded comms: I²C, SPI, PWM  
- RF troubleshooting (NRF24L01)  
- Project management & documentation  
- Patience + problem-solving under pressure  

---

## 🔮 Reflection & Next Steps  
- Engineering requires **iteration, persistence, and grit**. I encountered countless problems, but each solution was rewarding and reinforced my confidence as an engineer.  
- I’ve learned the **importance of iteration** — testing, failing, and improving in cycles.  

### 📌 Next Steps  
- Design and test a **custom PCB** for the remote, including BMS features.  
- Scale up motor control to reliable **24V operation**.  
- Collect user feedback from Portland Pudgy boat owners.  
- Work toward a **market-ready RC electric kit**.  

### ⚡ Reverse Engineering for BMS Design Inspiration  
- Electric lawnmower BMS  
  ![](https://github.com/user-attachments/assets/1c880cf7-097f-4a7b-8667-faa390535135)  

- Segway BMS  
  <img width="461" height="880" src="https://github.com/user-attachments/assets/c302b465-6b88-44d0-ab4b-c4b1071777ec" />  

---
