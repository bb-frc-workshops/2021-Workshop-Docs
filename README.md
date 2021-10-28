# **2021 BB Workshop Documentation**
This repo contains the documentation for the 2021 Virtual Workshop. 

## Goal
The goal of this workshop is to create a competitive robot for the New Englan Alliance Antics The Recharge game (see [Game](#Game) section below).

## Pre-requisites
It is assumed that you already have a Romi robot, fully assembled, and some supplies (TODO: ADD LINK HERE FOR EXAMPLES). We will try to make this document as self-guiding as possible but some experience will be assumed. If you have questions, please leverage your coaches and mentors as well as our office hours.

## Setup Romi Networking
It is recommended that you connect your Romi through your local wifi network in order to connect the robot, and leverage your computer for Zoom or other virtual communication and screen sharing. Please follow the installation documentation [BB Workshop Network Instructions](./BB%20Workshop%20Network%20Instructions.md)

# Intro to the Romi
The official [Wpilib Romi documentation](https://docs.wpilib.org/en/stable/docs/romi-robot/index.html) is the best place to start. Additionally, to see a quick video on the background of workshops and a little more info about the Romi hardware, watch this [video](https://www.youtube.com/watch?v=W3hX-cEsVwM&t=1207s). 

## <a name="Game"></a>Game
The game we will be building for is called [Alliance Antics The Recharge](https://wpilib.org/blog/alliance-antics-the-recharge). 

## Recommended approach
You will get a chance to create and design robots basically from scratch to participate in this competition. Have fun prototyping different ideas to determine their feasibility. Once you feel confident about a particular design, start coding to command the robot to behave as you demostated with your prototype.

### Design
It's important to take some time and think about what strategy you'd like to take to achieve the best results during the game play. When coming up with various designs, think about how you want the robot to behave. What action do you want the robot to perform? How will the robot interact with the objects on the field? How would you interact with the robot? How would that action set you up for another action. For example, if you have to pick up an object, then you will want to think about how to transport it and position it for the next action you will want to take.

### Prototyping
Prototyping is a way to test out your designs without having to fully implement them. Prototyping will help you identify gaps and unknowns that you were unaware of prior. It will help you to determine if these gaps can be easily overcome with tweaks to the design, or if you should discard that option in favor of another. We highly recommend prototyping for this reason. When you are prototyping, build only what's necessary. This may even mean that what you build is not even attached to the robot or secured firmly. Remember, you only trying to determine if this design has potential to behave how you expect, not fully determine if it will.

### Integration
Once you have chosen the prototype(s) that you'd like to move forward with, the next step is to see if the attachment to the robot, and actions given from the program continue to behave as you expected. Integrating these pieces together can identify new areas to address ... not to mention the challenges of coding it up to behave as expected. We recommend you start with the *romireference* example in VS Code as shown [here](https://docs.wpilib.org/en/stable/docs/romi-robot/programming-romi.html).

## Anatomy of a robot
In particular, you should become familar with what options you have for inputs and outputs of your robot. Outputs, which we call actuators, are used to make the robot move or behave a certain way. The actuators we will use are motors. In our case, we have motors for the wheels. Servo motors are useful for adding additional motion (such as raising/lowing an arm, opening/closing gates, or rotating a conveyor belt). Inputs to our robot are called sensors. This is ways for us to programatically understand our environment. Examples are limit switches, encoders, gyroscopes, or cameras. For more information on actuators and sensors, please see:
- [Motor](https://en.wikipedia.org/wiki/Electric_motor)
- [Servo](https://en.wikipedia.org/wiki/Servomotor)
- [Limit switch](https://en.wikipedia.org/wiki/Limit_switch)
- [Encoder](https://en.wikipedia.org/wiki/Rotary_encoder)
- [Gyroscope (type of Inertial Measurement Unit)](https://en.wikipedia.org/wiki/Gyroscope)
- [Camera](https://en.wikipedia.org/wiki/Computer_vision)

## Office Hours
We will have office hours where you can come and ask questions between 4:00 - 6:00 p.m. EST, Nov. 8th-11th and Nov. 15th-18th. Please join using this [TODO: Zoom link]()

## Mini-competition Weekend
To have some additional fun, we will hold our own competion before the Dec. 4th New England challenge. This will be held Nov. 20th from 10:00 a.m. - 2:00 p.m EST.