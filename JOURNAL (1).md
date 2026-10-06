---
title: "RefloBot"
author: "k.migueloliveira2009"
description: "RefloBot is a 4x4 autonomous off-road robotic platform designed for reforestation in degraded areas.\n\nThe robot will have a custom mechanical design built primarily from 3030 and 3060 aluminum extrusion profiles, along with custom-designed off-road wheels for operating on uneven terrain.\n\nThe wheels will use a hybrid construction. The outer tire section will be 3D-printed in flexible TPU to provide traction and compliance on rough terrain, while the internal rims will be 3D-printed in ABS using a 3D printer I already have access to. This approach reduces the amount of TPU required while maintaining a rigid internal structure and a flexible off-road contact surface.\n\nIts electronics will be based around a custom ESP32-S3 breakout board, using two ESP32-S3 modules. One will handle the robot's general control and movement, while the other will be responsible for autonomous navigation, sensors, and the seed-dispensing system.\n\nThe robot will also have a custom seed-dispensing mechanism based on a camera-lens iris mechanism. The iris opens at a controlled position, allowing a seed to fall through by gravity. This provides a simple and mechanically reliable way to release individual seeds without requiring a complex feeding mechanism.\n\nFor navigation and autonomy, I plan to integrate a GPS module and IMU sensors, allowing the robot to autonomously navigate through a designated reforestation area.\n\nNote: I’m going to switch the aluminum profiles from 3030/3060 to 2020/2040, as the structure would otherwise be unnecessarily robust; I’m also going to resize it to accommodate solar panels, though I still need to decide whether to use them now or simply leave the space reserved for a future version 2."
created_at: "2026-09-09"
---

# 2026-10-06: Rubber Wheel Design - Provisory Version (I think) -> Forgot to post the devlog

**Total time spent: 22 minutes**

# Temporary Wheel Mounting Solution

After looking at some wheel models on Amazon, I realized that I could not directly attach them to the motor flange as I had originally planned.

The main problem is that some of the wheels already have bearings and their own mounting system, which makes it difficult to connect them directly to my motor flange without redesigning or modifying the wheel itself.

Because of this, I decided to think about a temporary version of the wheel mounting system.

The current idea is to keep the wheel mounted on its original rim and then create an adapter that connects the rim to the motor flange using screws.

I know that this solution is not the most beautiful one, but for now the priority is to make the mechanical system work and validate the concept before spending more time designing a completely custom wheel.

The temporary solution would also allow me to test the motors, drivetrain, ground clearance, and overall chassis before finalizing the wheel design.

Later, I can replace this solution with a cleaner custom hub/rim that is designed specifically around the motor flange.

For now, I am treating this as a prototype solution rather than the final mechanical design.

And it looks like this:
![image.png](https://cdn.hackclub.com/01a1139e-86ae-7d5f-85ec-fff0357a8302/image.png)

# 2026-10-06: Frame Paint and Motor Ajusts - Forgot to post the devlog

**Total time spent: 12 minutes**

# Frame Paint and Motor Adjustments

## Frame Paint

I decided to paint the aluminium frame **black**, mainly to improve the overall appearance of the robot and give the chassis a more consistent and finished look.

![Black painted frame](https://cdn.hackclub.com/01a1138c-de76-7d80-94ce-a23130737031/image.png)

Besides the aesthetic aspect, the black finish also gives me a better idea of how the final robot will look once the solar panels, wheels, electronics, and other components are installed.

I wanted the Reflobot to have a more **clean and cohesive visual identity**, while still keeping the mechanical structure visible.

## Motor Adjustments

I also made some adjustments to the motor design and mounting geometry.

![Motor adjustments](https://cdn.hackclub.com/01a1138c-506d-72b7-9382-8944c19dbc53/image.png)

These changes were made to improve the integration between the motor, its support, and the aluminium frame.

The motor position is especially important because it affects several other parts of the robot, including the wheel position, ground clearance, motor flange, and internal space available for the batteries and electronics.

I am continuing to refine this part of the design before finalizing the wheel and motor-flange connection.

## Current Status

At this stage, the frame geometry is becoming more defined, while the motor mounting system is still being iterated.

The next mechanical iterations will focus on making sure that the **motor supports, wheel assembly, and chassis** work together without interfering with each other.


# 2026-10-06: BOM Update , Frame Updates and Inner Plate - Forgot to post the devlog

**Total time spent: 42 minutes**

# BOM Update, Frame Updates and Inner Plate

## BOM Update

I updated the **BOM (Bill of Materials)** to reflect the latest changes to the robot's mechanical design.

The main change was updating the aluminium extrusion list to match the new **2020/2040 profiles** that I am using for the chassis.

This makes the BOM more accurate and gives me a better estimate of the actual materials and costs required to build the Reflobot.

## Frame Updates

I also made some adjustments to the dimensions of the aluminium frame.

These changes were made based on the space required by the motors, wheels, batteries, H-Bridges, and other internal components.

The goal is to keep the chassis **compact and lightweight** while still providing enough space for all the components and maintaining a rigid structure.

## Inner Plate

I also added an **MDF inner plate** to the chassis.
![image.png](https://cdn.hackclub.com/01a1138a-5526-7a30-81c6-4fb8a160f5c7/image.png)

The purpose of this plate is to provide a flat surface where I can mount and organize the batteries, H-Bridges, DC-DC converters, and other electronics.

Using MDF for the prototype allows me to test the dimensions and component layout before producing a final version in a more suitable material.

It also makes it easier to modify the plate during the prototyping stage if I need to change the position of any component.

## Current Status

With these changes, the main chassis structure is becoming more defined.

The next iterations will focus on finalizing the **internal component layout, motor supports, wheel mounting system, and electronics organization** before moving toward manufacturing the final mechanical parts.


# 2026-10-06: AS5600 Encoders Support 

**Total time spent: 1 hour and 4 minutes**

## AS5600 Encoder Support

I also started designing a support for the AS5600 magnetic encoders that will be used to measure the rotation of the motors.

The main challenge with this type of encoder is that the sensor and the magnet need to remain properly aligned. Because of this, the support needs to hold the encoder in a fixed position relative to the motor while keeping the correct distance from the magnet.

### Encoder Support

I designed a custom support that can be attached to the motor assembly.

![AS5600 encoder support](https://cdn.hackclub.com/01a11368-ed18-71e5-a3bf-05cb39a8ce28/image.png)

The support is designed to keep the AS5600 board stable and aligned with the rotating magnet. I also tried to keep the structure compact so that it does not interfere with the wheel, motor support, or other components around the drivetrain.

### Encoder Mounted on the Motor

After designing the support, I integrated the AS5600 into the motor assembly.

![AS5600 encoder mounted on the motor](https://cdn.hackclub.com/01a1136a-1362-7fbc-ae48-8394286670c0/image.png)

The encoder will allow the ESP32 to obtain rotational feedback from the motor instead of relying only on the commanded motor speed.

This can be useful for more precise control of the drivetrain, especially when the robot is moving over terrain where the motors may experience different loads.

### Magnet and Motor Assembly

The magnetic element is positioned on the motor axis so that it rotates together with the shaft while the AS5600 remains stationary.

![Motor with AS5600 magnet](https://cdn.hackclub.com/01a1136a-a6c8-71a7-9a7c-df9bad75dc2a/image.png)

The important part of this design is maintaining the correct radial alignment and axial distance between the magnet and the AS5600 sensor. If the magnet is not properly centered over the sensor, the angle measurement can become inaccurate or unstable.

For the final version, I will need to verify the exact magnet dimensions, mounting tolerance, and sensor-to-magnet distance recommended for the AS5600.

### Why Add Encoders?

Adding encoders gives the Reflobot access to feedback from the drivetrain.

With the motor commands alone, I can tell the motor to rotate at a certain PWM, but I cannot directly know how fast the shaft is actually rotating.

With the AS5600, I can measure the shaft's angular position and calculate its rotational speed. This opens the possibility of implementing closed-loop motor control later.

For example, the encoder feedback could eventually be used to:

* Measure the actual motor RPM.
* Improve straight-line driving.
* Implement closed-loop speed control.
* Detect wheel or motor stalls.
* Estimate wheel movement and distance traveled.
* Combine wheel feedback with other sensors for autonomous navigation.
* (Also will help for odometry, but i think to apply this later)

This is especially useful for the Reflobot because the four wheels will not necessarily experience the same amount of traction when operating on soil, grass, or uneven terrain.

The current design is focused on creating a reliable mechanical interface between the motor, magnet, and AS5600 sensor before moving on to the electronics and control implementation.


# 2026-10-03: H-Bridge Support for Fixing , New Motors Supports, Battery and H-Bridge organization , Alterations of Size on some alumminium parts. and some research

**Total time spent: 2 hours and 28 minutes**

## H-Bridge Supports

After organizing the drivetrain, I started working on a way to properly fix the H-Bridge modules to the chassis.

Instead of leaving the H-Bridges loose inside the robot, I designed a dedicated support that can be attached to the aluminium extrusion frame. This should make the wiring more organized and prevent the modules from moving during the robot's operation.

Since the Reflobot will operate outdoors and experience vibration from the motors and uneven terrain, I also want the electronics to have a defined mounting position rather than simply being placed on the internal plate.

The support is being designed around the dimensions of the H-Bridge modules and the available space between the aluminium profiles.

![image.png](https://cdn.hackclub.com/01a1042c-550d-7865-a6d0-a5130a9e0238/image.png)

---

## New Motor Supports

I also continued developing the motor supports after changing the motor orientation.

The new supports are being adapted to the updated chassis geometry and the position of the motor axis. The main objective is to keep the motors rigidly attached to the aluminium frame while maintaining the desired wheel position and ground clearance.

The motor support is particularly important because it has to transfer the torque generated by the motor into the chassis without allowing excessive movement or misalignment.

I am also trying to keep the supports as compact as possible so they do not consume space that could be used by the batteries, electronics, or wheel assembly.

![image.png](https://cdn.hackclub.com/01a1041a-ef5e-7f43-bcf8-0d93c92d2903/image.png)

---

## Battery and H-Bridge Organization

After defining the approximate position of the motors, I started organizing the battery and H-Bridge layout inside the chassis.

The objective is to create a more structured internal arrangement instead of placing the components wherever there is available space.

I am considering the position of the batteries, H-Bridges, DC-DC converters, wiring, and other electronics together because their locations affect both the available space and the center of mass of the robot.

For the batteries in particular, I want them to remain securely fixed while still being accessible for maintenance or replacement.

![image.png](https://cdn.hackclub.com/01a10423-318e-7925-a063-9314024292f2/image.png)

The H-Bridges also need to be positioned close enough to the motors to avoid unnecessarily long high-current motor wires, while still leaving enough space for proper cable routing and access to the electrical connections.

---

## Aluminium Extrusion Size Adjustments

While organizing the internal components, I noticed that some of the aluminium extrusion pieces could be shorter or could use a different profile without compromising the overall structure.

Because the chassis uses both 2020 and 2040 profiles, I am adjusting some of their dimensions according to the loads and function of each part and also for the hour when i buy them.

The 2040 profiles are being kept in areas where additional stiffness or a larger mounting surface is useful, while 2020 can be used in lighter structural sections.

This approach helps avoid using larger profiles everywhere and keeps the robot closer to the original objective of being lightweight and compact.

The 2020 and 2040 profiles also belong to the same 20-series system, so compatible mounting hardware can generally be shared, depending on the exact extrusion standard and slot dimensions.

![image.png](https://cdn.hackclub.com/01a10425-7edc-7305-a66d-50c45c9de44f/image.png)

It will give the robot a height of exacly (without the wheels and with the mdf plates ) 146mm 

---

## Research and Design Decisions

Alongside the CAD work, I continued researching possible solutions for the mechanical and electrical integration of the robot.

Some of the main points I have been investigating are:

  * Features for the gps module 
  * Size of the seed droping mechanism 
  * Wires width and if it could get noises in the i2c communication 
The goal of these changes is not only to make the CAD model look cleaner, but to make the final robot lighter, more compact, easier to assemble, and easier to maintain.

## Current Design Status

At this stage, the main mechanical structure is becoming more defined. The next step is to finalize the mounting points for the motors, batteries, and H-Bridges and then use those dimensions to finalize the internal plate and cable routing.

![image.png](https://cdn.hackclub.com/01a1042b-2c66-71e1-ba96-b9106382ff45/image.png)

I am trying to avoid finalizing individual parts in isolation. Changes to the motor position affect the wheels, which affect the chassis dimensions, which affect the battery and electronics placement. Because of this, I am iterating the CAD model as a complete system rather than treating each component separately.

Very soon i will finish the cad and will start the pcb design 

# 2026-09-24: V1 RefloBOT - With new aluminium extrusions

**Total time spent: 32 minutes**

### Chassis

I changed the aluminium extrusions from 3030/3060 to 2020/2040 to make the robot slimmer and lighter. The previous profiles were stronger, but they also made the chassis larger and heavier than I originally expected.

The new profiles should be enough for the current chassis concept while reducing the overall size and weight. They also give the robot a cleaner appearance and provide a suitable structure for supporting the solar panels.

![Chassis with 2020/2040 aluminium extrusions](https://cdn.hackclub.com/01a0d582-29c5-7d2b-abbe-72528820f26d/image.png)

After changing the extrusion dimensions, I started working on the motor placement. I positioned the motors sideways because of the available space inside the chassis.

This configuration helps reduce the amount of space required around the wheel axis and keeps the drivetrain more compact. It also gives me more flexibility when positioning the batteries, electronics, and other components inside the robot.

![Motor positioning inside the chassis](https://cdn.hackclub.com/01a0d582-9568-7fee-b55b-2e5e1d4d0802/image.png)

---

### Wheels V1

For the first version of the wheels, I started by designing the inner part of the wheel. I then added the motor flange and the TPU tire section to create a complete representation of how the wheel would connect to the drivetrain.

![Wheel V1 internal structure](https://cdn.hackclub.com/01a0d583-1da0-723a-b2f2-91f4e2da2e0f/image.png)

At this stage, the main objective was not to create the final tire design, but to verify the overall dimensions, wheel position, motor flange interface, and available space around the chassis.

![Wheel V1 assembly](https://cdn.hackclub.com/01a0d583-7872-7bd7-862d-a871cf71e7fe/image.png)

The current design is mainly focused on getting the wheel dimensions and motor mounting geometry correct before adding the off-road tread pattern.

I also need to evaluate the manufacturing method for the final wheel. The original plan was to use TPU for the tire, but I am currently considering using rubber off-road tires with a custom 3D-printed rim. This could reduce the cost and make the final wheel easier to manufacture and replace.

The connection between the wheel and the motor flange will also need to be finalized before the wheel design can be considered complete.

---

Note: I am posting this because, unfortunately, I deleted the first devlog.



# 2026-09-24: Frame Updates and Wheel Search

**Total time spent: 1 hour and 28 minutes**

# Motor Position, Motor Support and Wheel Design

## 1. Changing the Motor Position

First, I changed the position of the motors from the original configuration.

![Original motor position](https://cdn.hackclub.com/01a0d570-fc65-7d70-9eb1-472821d028c1/image.png)

The main reason for this change was to increase the distance between the motor axis and the ground without having to increase the wheel diameter.

![New motor position](https://cdn.hackclub.com/01a0d577-bd5a-7e2b-9cb2-7603a6a8bda0/image.png)

By changing the motor orientation and position, I was able to move the motor axis higher relative to the ground while keeping the chassis compact.

This is important for the Reflobot because it is designed to operate on uneven outdoor terrain. A motor axis positioned too close to the ground could reduce the robot's ground clearance and increase the chance of the motor or other drivetrain components hitting rocks, soil, roots, or other obstacles.

Another advantage of this configuration is that I don't need to compensate for the lower motor position by using a larger wheel. Keeping the wheels smaller helps me control the overall size and weight of the robot.

---

## 2. Designing the Motor Support

After changing the motor position, I started designing a custom support to attach the motors to the aluminium extrusion frame.

![Motor support](https://cdn.hackclub.com/01a0d575-ff80-71f5-9182-61506a165cd8/image.png)

The support was designed around the new motor orientation and the dimensions of the aluminium profiles.

The main objectives were:

* Securely fix the motor to the chassis.
* Maintain the motor axis at the desired height.
* Keep the motor aligned with the wheel.
* Avoid interfering with the aluminium extrusion.
* Keep the structure as compact as possible.
* Make the support easy to manufacture and replace if necessary.

I am also trying to keep the motor support modular. This should make it easier to modify or replace the mounting system later if I change the motors, wheel design, or drivetrain configuration.

The final version will also need to account for the forces generated by the wheels. Since the Reflobot is a 4-wheel-drive robot, the supports need to handle not only the weight of the robot but also the torque and mechanical loads transmitted from the motors to the wheels.

---

## 3. Changing the Wheel Size

After testing the new motor position, I decided to reduce the wheel diameter from 8 inches to 6 inches.

![6-inch wheel concept](https://cdn.hackclub.com/01a0d574-b904-7960-b6d2-df75d1cdf176/image.png)

The original 8-inch wheels were becoming too large for the new, slimmer chassis. Reducing the diameter helps keep the robot more compact and better matches the dimensions of the new 2020/2040 aluminium extrusion frame.

The smaller wheels also reduce the amount of space required around the drivetrain and make it easier to integrate the wheels with the rest of the chassis.

However, I still need to make sure that the 6-inch wheels provide enough ground clearance for the terrain where the Reflobot is intended to operate.

---

## 4. Rubber Tires vs. 3D-Printed TPU

I am also reconsidering the original plan of manufacturing the entire wheel using TPU.

Instead, I am currently looking at using rubber off-road tires and designing the wheel rim separately.

There are currently two possibilities:

### Option 1 — Rubber Tire + 3D-Printed Rim

I could purchase only the rubber tire and manufacture the rim myself.

This would allow me to design the rim specifically around the motor flange and the dimensions of the motor shaft.

It would also give me more control over the wheel geometry and make future modifications easier.

### Option 2 — Complete Wheel + Modified Mounting

The other possibility is to purchase a complete 6-inch off-road wheel and modify its center section so that it can be attached to the motor flange.

This could be simpler mechanically, but I would have less control over the original wheel mounting geometry.

---



# 2026-09-22: RefloBot V1 Design - Frame and Wheels

**Total time spent: 1 Hour and 12 min**

### Solar Panels

I started by creating a block with the same dimensions as the solar panel that a friend in our school's research group has available.

After that, I started mounting the panels on top of the frame. I moved and duplicated the blocks to test different positions and spacing, until I found an arrangement with an equal distance between the panels around the frame.

![image.png](https://cdn.hackclub.com/01a0cb9c-5da0-7e4b-853e-aad5401f3e69/image.png)

### Electronics and Battery Plate

After working on the solar panel supports, I started designing a preview of the inner plate that will hold the electronics and batteries.

I also created a block with the same dimensions as the battery to verify the available space and make sure the components can fit inside the chassis.

This will help me finalize the internal layout before manufacturing the actual plate.
![image.png](https://cdn.hackclub.com/01a0cb9c-d896-753a-beef-bdfd4a751b77/image.png)

### Tires

I also started researching off-road rubber tires to compare them with the TPU tires I was originally planning to use.

At the moment, rubber tires are looking like the better option because they seem to be cheaper and easier to mount on the wheels.

However, I still need to find a reliable way to connect the tires to the motor axis and flange, so this part of the design is not finalized yet.

(the winner for now is this):
![image.png](https://cdn.hackclub.com/01a0cb9d-ba3a-757d-a8e2-06ea0b4cfe4b/image.png)

### Frame Fixer
I also designed a simple version of the frame extrusions fixer
![image.png](https://cdn.hackclub.com/01a0cba0-6621-7e3d-86ba-3978025f9862/image.png)

Note: I still need to see if is avaliable in my contry

