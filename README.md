[README.md](https://github.com/user-attachments/files/31240226/README.md)
# r6bot ROS 2 Integration

A team robotics project exploring the path from **physical assembly** to **ROS 2 control and simulation** for a 6-DOF r6bot arm.

The project adapted `ros2_control_demos` example 9 from the default **rrbot** model toward **r6bot**, using a bottom-up debugging approach: robot structure -> URDF/xacro -> joint names -> `ros2_control` -> controller configuration -> Gazebo.

## What I worked on

My contribution focused on **physical assembly and ROS 2 compatibility support**.

- Assembled assigned sections of the arm, mainly steps **4, 5, 11, 16, and 18**.
- Helped troubleshoot a step-13 bracket / motor-orientation issue and learned to verify mechanical assumptions before changing a shared assembly pipeline.
- Followed the ROS 2 compatibility debugging and helped reason about why adapting rrbot was more than a filename rename.
- Connected the mechanical side of the robot with the software-side dependencies between the description, joint names, controllers, Gazebo settings, and launch configuration.
## Documentation

The full project report is available as a PDF:

**[r6bot Bottom-Up Project Report](docs/r6bot_bottom_up_project_report.pdf)**

The report is also reproduced below for direct viewing.

![Project report page 1](docs/report-pages/page-01.png)
![Project report page 2](docs/report-pages/page-02.png)
![Project report page 3](docs/report-pages/page-03.png)
![Project report page 4](docs/report-pages/page-04.png)
![Project report page 5](docs/report-pages/page-05.png)
![Project report page 6](docs/report-pages/page-06.png)
![Project report page 7](docs/report-pages/page-07.png)
![Project report page 8](docs/report-pages/page-08.png)
![Project report page 9](docs/report-pages/page-09.png)
![Project report page 10](docs/report-pages/page-10.png)
![Project report page 11](docs/report-pages/page-11.png)
![Project report page 12](docs/report-pages/page-12.png)
![Project report page 13](docs/report-pages/page-13.png)
![Project report page 14](docs/report-pages/page-14.png)
![Project report page 15](docs/report-pages/page-15.png)
![Project report page 16](docs/report-pages/page-16.png)
![Project report page 17](docs/report-pages/page-17.png)
![Project report page 18](docs/report-pages/page-18.png)
![Project report page 19](docs/report-pages/page-19.png)
![Project report page 20](docs/report-pages/page-20.png)
![Project report page 21](docs/report-pages/page-21.png)
![Project report page 22](docs/report-pages/page-22.png)
![Project report page 23](docs/report-pages/page-23.png)

It covers the conceptual background, debugging workflow, current limitations, next implementation plan, and individual team reflections.
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
├── ORIGINAL_FILE_MANIFEST.tsv
├── PUBLICATION_NOTES.md
└── docs/
    └── r6bot_bottom_up_project_report.pdf
```

The uploaded project archive contained documentation rather than the full ROS workspace, so this repository preserves the available report and documents the work without inventing missing source code.

## Documentation

The full project report is available here:

**[r6bot Bottom-Up Project Report](docs/r6bot_bottom_up_project_report.pdf)**

It covers the conceptual background, debugging workflow, current limitations, next implementation plan, and individual team reflections.

---

**Main takeaway:** verify assumptions before changing a shared system - whether that system is a mechanical assembly or a ROS 2 integration stack.
