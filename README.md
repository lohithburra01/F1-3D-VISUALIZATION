# **F1 Race Simulation Project**


https://github.com/user-attachments/assets/94285cf4-a3fd-4fd3-9ce8-a23ce3f09c50


## **Overview**  

This project showcases a **high-fidelity 3D race simulation system**, built to process **real telemetry data** and generate **accurate visualizations of vehicle movement on a track**. By integrating **real-world spatial data, photorealistic rendering, and automation workflows**, I developed a scalable pipeline that reconstructs race laps with **precision and realism**.  

The core principles of this project—**data-driven visualization, terrain modeling, and real-time simulation**—are highly adaptable to broader applications, including **planetary exploration and autonomous navigation systems**.

---

## **Key Components**  

### **1. Data Extraction & Processing (Python & FastF1 API)**  

- Implemented a **data pipeline** to fetch live and historical telemetry data via the **FastF1 API**.  
- Extracted **precise positional (X, Y), velocity, and timing data (4Hz sampling)** to reconstruct vehicle motion.  
- Organized the processed data into structured formats (**CSV & GeoJSON**) for simulation input.  

This structured approach ensures a **high level of accuracy**, allowing seamless integration with **game engines and real-time rendering environments**.

---

### **2. Terrain & Track Modeling (GIS, QGIS & Blender)**  

Realistic environment modeling requires **high-resolution terrain data and accurate circuit layouts**:  

- **QGIS & GIS Data Processing**:  
  - Extracted **satellite imagery** and **digital elevation models (DEMs)** to model the real-world track.  
  - Converted geographic data to **GeoJSON** format for 3D processing.  

- **3D Model Generation in Blender**:  
  - Used **parametric curves** and **array modifiers** to generate a **continuous race track model**.  
  - Applied **real-world textures** for photorealistic rendering.  

This workflow allows the creation of **high-fidelity virtual terrains**, an approach that can be adapted for **lunar and planetary surface simulations**.

---

### **3. Vehicle Motion & Path Generation (Blender Python Scripting)**  

Accurate simulation of vehicle movement requires a **data-driven animation system**:  

- **Path Generation**:  
  - Parsed **X, Y coordinates** from telemetry data to create a **motion path** inside Blender.  
  - Utilized **Bezier curve smoothing** for realistic transitions.  

- **Physics-Based Motion Simulation**:  
  - Developed a **Follow Path constraint system** to control vehicle movement.  
  - Keyframed velocity adjustments based on **real-world acceleration & braking data**.  

By automating **data-to-motion conversion**, this system can be extended to simulate **rover movement across planetary terrains**.

---

### **4. Animation & Real-Time Simulation (Blender Python & Unreal Engine 5)**  

To bring the simulation to life, I implemented a **time-synchronized animation system** that accurately represents real-world vehicle dynamics:  

- **Speed-Based Keyframing**:  
  - Normalized **telemetry speed data** to adjust vehicle acceleration and deceleration dynamically.  
  - Ensured smooth **transitioning between high-speed straights and braking zones**.  

- **Rendering & Realism (Unreal Engine 5 Integration)**:  
  - Experimented with **real-time rendering** for interactive visualization.  
  - Used **ray tracing & dynamic lighting** to enhance environmental realism.  

The ability to **integrate real-world telemetry into a high-fidelity simulation pipeline** is crucial for applications in **robotic navigation and planetary mission planning**.

---

## **Challenges & Solutions**  

### **1. Steering Angle Approximation**  

- Unlike traditional racing simulations, **telemetry data lacks explicit steering angle values**.  
- I initially tried a **5-step look-ahead/behind tanh-based angle approximation**, but it led to errors in sharp corners.  
- **Solution:**  
  - Implemented a **curve-based orientation system** in Blender that dynamically adjusts vehicle heading.  
  - Used **Follow Path constraints** to ensure natural cornering behavior.  

This method allows **realistic vehicle orientation without direct steering inputs**, a technique applicable to **autonomous navigation simulations**.

### **2. Large-Scale Terrain Accuracy**  

- **GIS-to-3D model conversion introduced distortions** in high-detail track models.  
- **Solution:**  
  - Used **QGIS spatial corrections** to refine **topographical accuracy** before importing into Blender.  
  - Developed **custom interpolation scripts** to enhance surface continuity.  

The same methods can be applied to **lunar or Martian terrain modeling**, improving simulation accuracy for off-world exploration.

---

## **Future Enhancements & Broader Applications**  

This project serves as a **foundational prototype** for real-time visualization systems that merge **scientific data with high-fidelity rendering**. Possible extensions include:  

✅ **Real-Time Simulation**  
- Expand the system to **process live telemetry data**, allowing **real-time vehicle visualization**.  
- Similar approaches could be used for **rover navigation telemetry playback**.  

✅ **Dynamic Terrain Adaptation**  
- Automate **topographical adjustments** using DEMs & LiDAR datasets.  
- Extend methods for **moon/Mars terrain simulation & obstacle avoidance testing**.  

✅ **Expanding Physics-Based Motion Models**  
- Enhance the simulation with **suspension dynamics & real-world physics constraints**.  
- Investigate real-time integration with **autonomous driving algorithms** for planetary mobility applications.  

---

## **Conclusion**  

This project demonstrates the power of **data-driven simulation**, **high-fidelity visualization**, and **real-time rendering** to create **realistic, interactive environments**.  

The core techniques—**GIS data processing, procedural 3D modeling, and animation automation**—can be extended beyond motorsports, finding applications in **robotic exploration, planetary navigation, and space mission visualization**.  

As I continue refining this pipeline, I’m excited about its **potential applications in space exploration, research, and real-time planetary simulations**.  

