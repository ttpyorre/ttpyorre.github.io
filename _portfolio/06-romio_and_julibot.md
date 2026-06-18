---
title: "Romio and Julibot"
excerpt: "With Romio (the robots are called romi's) and Julibot I made scenes from shakespeare be acted by three robots. In my Junior and Senior years I ended up being a student assistant for this class. <br/><img src='/images/portfolio/romio_and_julibot/best_project.png'>"
collection: portfolio
---

I did this project in a team of three, with (Leona) Nhi Nguyen, Theo Winter, and me. 

Due to the impact of COVID19, WPI Drama/Theatre shows are in need of actors due to the restrictions on public performances. And we brought back everyone’s favorite Shakesphere’s play : Romio and Julibot. With our three actors: Leona’s Romi as Romio, Tom’s Romi as Tybot and Julibot, and Theo’s Romi as Mercutibot and Fribot.

<img src='/images/portfolio/romio_and_julibot/best_project.png'>

In this project we recreated three scenes from the play. The fight scene between Tybot and Mercutibot, where they both end up dying, balcony scene where Julibot climbs on the balcony and leaves Romio a message to ask him to follow her, and get married, and finally a curtain call. 

<img src='/images/portfolio/romio_and_julibot/fight_scene.png'>

Here is an example of the fight scene the robots did. They had to be able to do multiple things, detect when they got stabbed, communicate between each other, and find each other. There were multiple solutions to each of these aspects of the scenes, and we decided to implement multiple of them. One robot was equipped with a camera, that was able to read an april tag on the other robot using some classic computer vision algorithms, and determine the distance it was from the robot and follow them. Another robot had an IR camera, that was able to detect the other robots that had an IR emitter on them. To detect the stabbing, the robots were equipped with an IMU that told them when another robot "hit" them. 

During the balcony scene, Julibot was able to recognize when it was on the balcony also with an IMU. When it went up the ramp, it calculated the pitch angle based on the IMU readings. Once it reached the top it set its speeds to zero. While climbing the ramp, it stayed in the middle by utilizing ultrasonic sensors and a PID controller to stay a certain distance from the wall. Finally, to communicate to Romio, we made an MQTT network with which we were able to send data over the network between the robots. 

