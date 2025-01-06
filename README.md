# F1 Race Simulation Project

## Overview

This project aims to create a detailed 3D simulation of Formula 1 race laps using real telemetry data. By combining data extraction techniques, 3D modeling, and animation, I've developed a system that visualizes a car's movement on a track based on actual race information. This simulation provides insights into racing lines, speed variations, and overall lap performance in a visually engaging format.

## Components

### 1. Data Extraction (Python)

My data extraction process utilizes the FastF1 API, a powerful tool for accessing Formula 1 telemetry data. Here's a breakdown of the process:

- I use FastF1 to fetch driver data for a specific season, circuit, and lap.
- The extracted data includes x and y coordinates (representing the car's position on the track), timestamps (at a 4Hz frequency for precise timing), and speed information.
- This raw data is then processed and organized into a structured format.
- Finally, I save this processed data into a CSV file, which serves as the foundation for my 3D simulation.

This approach allows me to work with real, accurate data from actual F1 races, ensuring that my simulations reflect genuine racing scenarios.

### 2. Track Modeling (QGIS & Blender)

Creating an accurate representation of the race track is crucial for my simulation. I've developed a two-step process using QGIS and Blender:

1. QGIS Processing:
   - I use QGIS, a powerful Geographic Information System, to extract essential track data.
   - This includes obtaining a high-resolution satellite image of the track for texturing.
   - I also extract the track's geometry in GeoJSON format, which provides an accurate outline of the circuit.

2. Blender Modeling:
   - The GeoJSON data is imported into Blender and converted into a 3D curve, forming the backbone of my track model.
   - I then create a plane and apply an array modifier, carefully adjusting it to wrap around the curve. This technique allows me to create a smooth, continuous road surface that follows the exact path of the real track.
   - The satellite imagery extracted from QGIS is then applied as a texture to this road surface, providing realistic visual details such as track markings, run-off areas, and surrounding landscape.

This combination of GIS data and 3D modeling techniques results in a highly accurate and visually appealing track model.

### 3. Car Path Generation (Blender Python Script)

With my track model in place, the next step is to accurately position and move the car model along the racing line. Here's how I achieve this:

- I've developed a Python script that runs within Blender's script editor.
- This script reads the CSV file generated in my data extraction phase.
- Using the x and y coordinates from the CSV, the script generates a curve in Blender. This curve represents the exact path the car took during the actual race lap.
- I then import a detailed 3D model of the specific F1 car into my Blender scene.
- A Follow Path constraint is applied to the car model, binding it to the curve I created.

This approach ensures that my car model precisely follows the racing line taken by the actual F1 car during the race.

### 4. Animation (Blender Python Script)

To bring my simulation to life, I need to accurately represent the car's speed and acceleration. My animation script handles this crucial aspect:

- The script starts by reading the speed data from my CSV file.
- I normalize these speed values to work within Blender's animation system.
- The normalized speed data is then used to keyframe the offset of the Follow Path constraint applied to my car model.
- This technique allows me to simulate realistic acceleration and deceleration along the track.
- By adjusting the offset based on the actual speed data, I ensure that the car speeds up in straights and slows down for corners, just as it did in the real race.

The result is a smooth, realistic animation that accurately represents the car's varying speed throughout the lap.

## Challenges and Solutions

### Steering Angle Calculation

One of the most significant challenges I faced was the lack of steering angle data in the telemetry. This information is crucial for realistic car orientation, especially in corners. Here's how I approached this problem:

Initially, I attempted to calculate the steering angle using a 5-step look-ahead and look-behind approach combined with a tanh function. The idea was to analyze the upcoming and previous track positions to determine the appropriate steering angle. However, this method proved problematic, especially in sharp corners where it resulted in unrealistic 180-degree rotations of the car model.

To overcome this, I developed an alternative solution:
1. Instead of trying to calculate steering angles directly, I create a smooth curve from the telemetry data points in Blender.
2. I then use Blender's Follow Path constraint for the car model. This constraint naturally handles the orientation of the car along the curve.
3. To account for varying speeds, I keyframe the path offset based on my normalized speed values.

This approach provides a more realistic representation of the car's movement, especially in cornering scenarios, without requiring explicit steering angle data.

### Track Modeling

Another significant challenge was creating an accurate 3D model of the race track. Formula 1 circuits are complex, and accessing detailed, official track data can be difficult. Here's how I solved this:

1. I start by using QGIS to extract track outlines from satellite imagery. This gives me an accurate 2D representation of the circuit.
2. The extracted track data is then imported into Blender and converted into a 3D curve. This curve forms the basis of my track model.
3. To create the actual track surface, I use Blender's array modifier on a plane object, carefully adjusting it to wrap around my 3D curve. This technique allows me to create a continuous, smooth track surface that follows the exact path of the real circuit.
4. Finally, I apply the extracted satellite imagery as a texture to my 3D track model. This adds realistic details like track markings, run-off areas, and the surrounding landscape.

This workflow allows me to create visually accurate and detailed track models without needing access to official circuit data.

## Future Improvements

As I continue to develop this project, I have several exciting improvements in mind:

- Implement real-time simulation capabilities using live telemetry data. This would allow for near-instantaneous visualization of ongoing races.
- Enhance the accuracy of car positioning and rotation, especially during cornering. I'm exploring advanced interpolation techniques to achieve smoother, more realistic car movements.
- Optimize the track modeling process for quicker setup of new circuits. This could involve automating more of the QGIS to Blender workflow.
- Incorporate additional telemetry data such as gear changes, DRS activation, and tire wear for more detailed and insightful simulations.
- Develop a user-friendly interface for easier selection of races, drivers, and laps to simulate.

## Conclusion

This project demonstrates the powerful integration of various technologies and data sources to create a visually engaging and accurate F1 race simulation. By combining real telemetry data with advanced 3D modeling and animation techniques, I've created a platform that offers unique insights into F1 racing dynamics.

While there are certainly areas for improvement and expansion, this project serves as a solid foundation for more advanced racing visualizations and analyses. It showcases the potential of combining data science with 3D graphics to create informative and engaging sports visualizations.

As I continue to refine and expand this project, I'm excited about its potential applications in race analysis, fan engagement, and even as a tool for drivers and teams to study and improve their performance.
