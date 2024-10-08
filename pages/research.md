---
title: Research
permalink: /research/
---

We are pursuing several research directions simultaneously in the lab. The following vignettes provide a snapshot of some of the key challenges we are addressing and the innovative solutions we are developing.

### Motion Generation Algorithms

<img src="/assets/theme/images/research/relaxed_ik_hubo_3.png" alt="Alt text" width="450" height="450">

A core focus of our research in the APOLLO Lab is enabling robots to navigate and interact effectively within the complex environments of the real world. To address this, we explore innovative approaches in planning, optimization, sensing, and learning that equip robots with more efficient and adaptive methods for controlling their movements and actuating their joints over time. By developing new algorithms and frameworks, we aim to enhance a robot's ability to autonomously perform tasks with precision, robustness, and flexibility—whether it involves manipulating objects, navigating through cluttered spaces, or interacting with humans. This research not only advances fundamental capabilities in robot motion but also contributes to broader goals in fields like autonomous systems, human-robot collaboration, and industrial automation.   

### Combining Visual + Manipulation Learning

<img src="/assets/theme/images/research/viewpointselection.png" alt="Alt text" width="350" height="350">

One of our key goals is to develop adaptive robot systems—robots that can both manipulate objects and sense their environment in dynamic, flexible ways—so that they learn manipulation and viewpoint selection together in an integrated process, similar to how humans coordinate movement and perception. Rather than relying on static, fixed cameras, these robots can actively adjust their viewpoints to optimize the visual information they gather, minimizing issues like occlusions. By simultaneously learning to manipulate objects and choose optimal viewpoints, these systems can better align their actions with their perception, leading to more efficient and natural learning. This unified approach not only accelerates the development of manipulation policies but also enhances their robustness and adaptability in real-world environments. Whether it's a group of robots collaborating or a single humanoid robot, this integration of perception and action improves the overall intelligence and efficiency of robotic systems.

### Combining Continuous and Discrete Reasoning for Robot manipulation

![clutter_teaser-01.png](/assets/theme/images/research/clutter_teaser-01.png)

One of the most significant open questions in robotics today is how to effectively integrate the continuous dynamics of robotic systems—such as motion, physics, and sensor feedback—with the discrete abstractions required for high-level task planning, logical reasoning, and decision-making. This challenge involves bridging two fundamentally different paradigms: the smooth, often nonlinear, world of physics-based control and the symbolic, structured domain of tasks and objectives.

We are particularly focused on advancing approaches that leverage mixed-integer programming (MIP) optimization, large language models (LLMs), and receding horizon control (RHC) to tackle this problem. MIP allows for precise modeling of both discrete and continuous decision variables, making it a powerful tool for scenarios that involve both logical constraints and physical feasibility.  Large language models, offer an unprecedented capability to interpret and generate natural language descriptions of tasks, allowing robots to understand and follow abstract instructions, or even to reason over sequences of actions. Finally, receding horizon control plays a crucial role by enabling real-time, adaptive decision-making. RHC allows robots to continuously replan their actions by considering a finite time window into the future, making it well-suited to dynamic, uncertain environments where the robot's actions need to be responsive to changes in both the environment and task objectives. 

# We are currently assessing solutions to these problems in highly cluttered environments, for scenarios like disaster cleanup, fruit picking, and home-care.  

### Applied math for robotics (and beyond)

<img src="/assets/theme/images/research/math.png" alt="Alt text" width="250" height="250">

In the APOLLO Lab, we focus heavily on the development of advanced mathematical tools and optimization techniques to push the boundaries of robotics and related fields like machine learning and biology. Our research in this area includes:

- Better Automatic Differentiation Methods for Optimization: Optimization lies at the heart of many robotics and machine learning challenges, from trajectory planning to neural network training. We are developing more efficient and scalable automatic differentiation (AD) methods to improve the speed and accuracy of gradient-based optimization algorithms. These advancements will have a broad impact on both robotics and machine learning, where AD plays a crucial role in tasks like model training, control, and decision-making under uncertainty.

- Improved Mixed-Integer Programming (MIP) Solvers: Mixed-integer programming offers a powerful framework for handling problems that combine continuous and discrete variables, such as planning and decision-making in robotics, or complex biological systems. We are working on designing faster and more robust MIP solvers, which can unlock new possibilities for optimizing hybrid systems that involve logical constraints as well as continuous dynamics. This research is particularly important in applications like robot task scheduling, motion planning, and biological systems modeling.

- Unifying Spatial Computing with Geometric Algebra: Robotics frequently requires reasoning about spatial relationships and transformations, whether it's in manipulating objects or navigating environments. We are exploring better ways to unify these spatial computing tasks using concepts from geometric algebra, a mathematical framework that simplifies the representation and manipulation of geometric entities. By integrating geometric algebra into optimization workflows, we aim to develop more intuitive and computationally efficient methods for representing rotations, translations, and complex spatial interactions in robotic systems.

Together, these efforts in applied mathematics are helping to bridge key gaps in the fields of robotics and machine learning, enabling more robust, efficient, and intelligent systems.