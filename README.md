# r6bot ROS 2 Integration

A team robotics project exploring the path from **physical assembly** to **ROS 2 control and simulation** for a 6-DOF r6bot arm.

The project adapted `ros2_control_demos` example 9 from the default **rrbot** model toward **r6bot**, using a bottom-up debugging approach: robot structure -> URDF/xacro -> joint names -> `ros2_control` -> controller configuration -> Gazebo.

## What I worked on

My contribution focused on **physical assembly and ROS 2 compatibility support**.

- Assembled assigned sections of the arm, mainly steps **4, 5, 11, 16, and 18**.
- Helped troubleshoot a step-13 bracket / motor-orientation issue and learned to verify mechanical assumptions before changing a shared assembly pipeline.
- Followed the ROS 2 compatibility debugging and helped reason about why adapting rrbot was more than a filename rename.
- Connected the mechanical side of the robot with the software-side dependencies between the description, joint names, controllers, Gazebo settings, and launch configuration.

## Technical scope

`ROS 2 Jazzy` · `ros2_control` · `Gazebo` · `RViz` · `URDF / xacro` · `colcon` · robot kinematics

The integration work highlighted several practical checks:

- xacro macro interfaces must match the actual r6bot description rather than copied rrbot assumptions;
- controller joint names must exactly match the generated robot description;
- RViz success only validates the visualization/control path, not full physics simulation;
- Gazebo additionally requires collision geometry, inertial properties, mass, plugins, and matching control interfaces.

## Project status

The project reached a real intermediate state:

- **r6bot displayed and could be controlled in RViz**;
- the **default example-9 Gazebo setup worked** as a baseline;
- the **r6bot-specific Gazebo integration was not fully validated** and still required file-level cleanup and consistency checks.

I keep that distinction explicit because the useful part of this project was the integration and debugging process, not claiming a simulation result that had not yet been verified.

## Repository contents

```text
.
├── README.md
└── docs/
    └── r6bot_bottom_up_project_report.pdf
```

The uploaded project archive contained documentation rather than the full ROS workspace, so this repository preserves the available report and documents the work without inventing missing source code.

## Documentation

The full project report is available here:

**[r6bot Bottom-Up Project Report](docs/r6bot_bottom_up_project_report.pdf)**

It covers the conceptual background, debugging workflow, current limitations, next implementation plan.

---

**Main takeaway:** verify assumptions before changing a shared system - whether that system is a mechanical assembly or a ROS 2 integration stack.
