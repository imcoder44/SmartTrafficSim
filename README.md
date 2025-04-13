Here’s a complete and detailed README for the Traffic Simulation Unity Project, written in markdown for clarity and structure.

---

# Traffic Simulation Unity Project

This project is a Unity-based simulation of a traffic system featuring vehicles, traffic lights, sensors, and camera management. It demonstrates vehicle spawning, AI-driven movement, traffic light control, and real-time statistics in a virtual environment.

---

## Table of Contents

1. [Overview](#overview)
2. [Project Structure](#project-structure)
3. [Scripts Explanation](#scripts-explanation)
4. [Setup Instructions](#setup-instructions)
5. [Usage](#usage)
6. [Customization](#customization)
7. [Known Issues](#known-issues)
8. [Future Improvements](#future-improvements)

---

## Overview

The Traffic Simulation Unity Project models traffic flow across multiple lanes and roads. Key features include:

- **Vehicle Spawning**: Vehicles spawn randomly on designated lanes.
- **Vehicle AI**: Uses Unity’s NavMesh for pathfinding and movement.
- **Traffic Lights**: Dynamic timing adjusts based on vehicle counts.
- **Sensors**: Detect vehicles to manage traffic flow and light timings.
- **Camera Management**: Switch between multiple camera views.
- **UI Updates**: Displays real-time vehicle counts and traffic light timers.

This simulation is ideal for testing traffic management systems, AI behavior, or educational purposes.

---

## Project Structure

The project is organized around several C# scripts, each responsible for specific functionality:

- **Vehicle Spawning**:
  - `Lane1Spawner.cs`: Handles spawning on Lane 1.
  - `VehicleSpawnerLane2or4.cs`: Manages spawning on Lanes 2 and 4.

- **Vehicle AI**:
  - `CarAILane1.cs`, `CarAILane2.cs`, `CarAILane3.cs`: Lane-specific AI logic.
  - `CarAI.cs`: Generalized AI for other roads.

- **Traffic Lights**:
  - `Road1TrafficLight.cs`: Controls traffic light states and timers.
  - `TrafficSystemController.cs`: Synchronizes traffic lights across roads.

- **Sensors**:
  - `Sensor.cs`, `Sensor2.cs`, `Sensor3.cs`: Detect vehicles on Lanes 1, 2, and 3.
  - `SensorForOtherCars.cs`: Monitors vehicles on additional roads.

- **Camera and UI**:
  - `CameraAndPanelManager.cs`: Manages camera switching and UI panels.
  - `UpdateRoadStats.cs`: Updates UI with real-time data.

---

## Scripts Explanation

Below is a detailed breakdown of each script’s purpose and features:

### 1. Lane1Spawner.cs
- **Purpose**: Spawns vehicles on Lane 1 at random intervals.
- **Key Features**:
  - Spawns 0–9 vehicles per batch.
  - Delay between individual vehicle spawns: 6–15 seconds.
  - Time between batches: 15–30 seconds.

### 2. VehicleSpawnerLane2or4.cs
- **Purpose**: Spawns vehicles on Lanes 2 and 4.
- **Key Features**:
  - Spawns 0–5 vehicles per batch.
  - Delay between vehicles: 8–15 seconds.
  - Time between batches: 15–30 seconds.

### 3. CarAILane1.cs, CarAILane2.cs, CarAILane3.cs
- **Purpose**: Controls vehicle movement on specific lanes using Unity’s NavMesh.
- **Key Features**:
  - Pathfinding to random or predefined destinations.
  - Steering and physics managed via wheel colliders.
  - Vehicles are destroyed upon reaching their destination.

### 4. CarAI.cs
- **Purpose**: Provides generalized AI for vehicles on other roads.
- **Key Features**:
  - Assigns destinations based on road and lane configurations.
  - Uses similar pathfinding and movement mechanics as lane-specific scripts.

### 5. Road1TrafficLight.cs
- **Purpose**: Manages traffic light states (red, yellow, green) for Road 1.
- **Key Features**:
  - Adjusts green light duration based on detected vehicle count.
  - Includes timers for yellow and green phases.

### 6. TrafficSystemController.cs
- **Purpose**: Coordinates traffic lights across four roads.
- **Key Features**:
  - Manages transitions between light states (e.g., yellow to green).
  - Adjusts timing dynamically using sensor data.

### 7. Sensor.cs, Sensor2.cs, Sensor3.cs
- **Purpose**: Detects vehicles on Lanes 1, 2, and 3.
- **Key Features**:
  - Halts vehicles at red or yellow lights.
  - Counts vehicles to inform traffic light timing.

### 8. SensorForOtherCars.cs
- **Purpose**: Detects vehicles on roads beyond Lanes 1–3.
- **Key Features**:
  - Functions similarly to lane sensors but is tailored for broader road coverage.

### 9. CameraAndPanelManager.cs
- **Purpose**: Handles camera switching and UI panel management.
- **Key Features**:
  - Uses keyboard inputs (0–4) to toggle between views and panels.

### 10. UpdateRoadStats.cs
- **Purpose**: Updates the UI with real-time traffic data.
- **Key Features**:
  - Displays current and previous vehicle counts per road.
  - Shows traffic light timer statuses.

---

## Setup Instructions

Follow these steps to set up the project in Unity:

1. **Unity Version**:
   - Use Unity 2020.3 or later for compatibility.

2. **Clone the Repository**:
   - Clone the project using Git:  
     ```bash
     git clone <repository-url>
     ```

3. **Open in Unity**:
   - Launch Unity Hub, select “Add,” and choose the cloned project folder.

4. **Scene Setup**:
   - Verify that all prefabs (vehicles, traffic lights, sensors) are linked in the Unity Inspector.
   - In `CameraAndPanelManager.cs`, assign the appropriate cameras and UI panels.

5. **NavMesh Baking**:
   - Open the Navigation window (Window > AI > Navigation).
   - Select the terrain or road objects and bake the NavMesh for pathfinding.

---

## Usage

Here’s how to run and interact with the simulation:

1. **Run the Simulation**:
   - Click the Play button in Unity.
   - Vehicles will spawn automatically and move according to traffic light states.

2. **Switch Cameras**:
   - Press keys 0–4 to switch between different camera perspectives and UI panels.

3. **Monitor UI**:
   - Observe the UI for real-time updates on vehicle counts and traffic light timers per road.

---

## Customization

You can tailor the simulation to your needs with these options:

- **Vehicle Prefabs**:
  - Add or replace vehicle models in the `vehicalsPrefabs` array in the spawner scripts.

- **Spawn Rates**:
  - Modify spawn delays and batch sizes in `Lane1Spawner.cs` and `VehicleSpawnerLane2or4.cs`.

- **Traffic Light Timers**:
  - Adjust timing logic in `Road1TrafficLight.cs` and `TrafficSystemController.cs`.

- **Destinations**:
  - Edit AI scripts (`CarAILaneX.cs` or `CarAI.cs`) to set new or custom vehicle destinations.

---

## Known Issues

- **Vehicle Collisions**:
  - Vehicles may overlap or collide unnaturally due to unoptimized physics settings.
- **Timer Synchronization**:
  - Traffic light timers across roads may occasionally fall out of sync.
- **UI Updates**:
  - Slight delays in UI updates may occur under heavy load.

---

## Future Improvements

Consider these enhancements for future development:

- **Advanced Pathfinding**:
  - Add overtaking and lane-changing capabilities to vehicle AI.
- **Pedestrian Simulation**:
  - Integrate pedestrians and crosswalks into the system.
- **Emergency Vehicles**:
  - Implement priority logic for emergency vehicles (e.g., ambulances).
- **Multi-Intersection Support**:
  - Expand the simulation to handle multiple interconnected intersections.

---

This README provides a comprehensive guide to understanding, setting up, and using the Traffic Simulation Unity Project. For additional details, check the inline comments within the scripts or consult Unity’s official documentation. Enjoy experimenting with the simulation!
