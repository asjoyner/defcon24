# Can You Trust Autonomous Vehicles: Contactless Attacks Against Sensors of Self-driving Vehicle

[Abstract](https://www.defcon.org/html/defcon-24/dc-24-speakers.html#Liu)

## Summary
You can fool the sensors.  Nothing particularly concerning, looks like the worst you can do is cause autopilot to stop driving (currently okay, as the human needs to be able to cope with that anyway), makr cars run over people or into objects when using Summon or autopark irresponsibily (eg. not actually paying attention), make cars not autopark into otherwise-free parking spaces.

## Notes
Car hacking started with CAN bus hacking, then when they became connected people started ahcking the Telematics.  Now that they're autonomous, people are naturally hacking those attack surfaces.

He briefly describes what is autonomous driving, thelevels, etc. using the 0-5 scale, with tesla at 3, the lowest level of "hands off" driving, and Chaefer at the highest level 5, where you can sleep in your car.

Block diagram overview of the general idea of an autonomous car's environmental sensors, internals to handle driving, Human-Machine interface (HMI), etc. 

Overview of the various sensors, and their uses:
* Ulatrasonic
* Cameras
* LiDAR
* Radar

Overview of electronic controls:
* Break
* Throttle
* Power Steering

### How to hack the sensors?
Could spoof, jam, or blind the sensors, resulting in a crash or bad display in the HMI.

He briefly discusses the first fatal Tesla autopilot failure, indicating it was because of the sensor failure (somewhat true), as an example that causing the sensors to fail is a critical problem.

Give an overview of the sensors on a Model S.

Demo of ultrasonic jammer defeating the display of the rear distance indicator, which seemed to cause the tire-pressure interface to show.  Were they jamming the tire pressure gauge to override the display of the rear ultrasonic sensors?

They demo a "ghost car", in a parking garage, causing autopilot to stop the car by fooling the sensors into thinking that there's a car in front of it.

### Hacking the ultrasonic sensors
Suggests defending your parking space with a jammer instead of a sign saying "parking only for Me", so cars attempting to park there will stop on their own.

#### Jamming Attack
Jamming attack generates ultrasonic noises, denial of service
Spoofing, crafst fake ultrasonic echo pulses, to alter distance
Quieting Dinishes the original ultrasonic echoes to hide obstacles

The use an Ultrasonic transducer, $0.50
Signal suppliers, generate signals
   a. Arduino $25
   b. Signal generator $15

Tested and confirmed jamming of 8 models of stand-alone ultrasonic sensors in the lab, and outdoors against Tesla, Audi, Volksagen and Ford.

Different sensors have different responses to jamming, either *zero* distance or *maximum* distance.  How *should* a care behave?  They recommend zero distance as the fail-safe option.  Experiments against real cars indicate that today, they fail to reading maximum distance when jammed.  Video showing that behavior in an Audi in the field, with the sensor reading a distance of 65,536cm via the ODB-II display.  They demo a video of a guy standing in front of a Tesla, holding jammers, and summon the car into him and it runs into his legs.  His words: "That demo hurts!"  They demoed it in reverse, the human jumped out of the way, the car ran into the jammer and broke it, and then it stopped.  :)

Theory on why it reads zero, is that the sensor compares with the noise floor, which the echo doesn't overcome, so it believes it never heard the echo hence an infinite distance.

The pulled the sensor apart, and inspected what the chip reads from the actual sensor does under various levels of jammer to confirm that theory.  They believe the designer had good intentions, but didn't consider this attack.

#### Spoofing Attack
Have to inject your spoof before the actual echo will arrive.  Demo video on a Tesla Model S where their jammer makes the obstacle appear to increase and decrease smoothly towards the car, while nothing is moving.  Demo video on a an Audi using the spoofing to display a sound graphic analyzer in time with the music.

#### Acousting Quieting
Cancel original sound with ones of reversed phase.  Have to use dedicated hardware to do this in real time.

#### Cloaking
Cheap, using dampening material, has the same effect.  Hilarious video of them putting egg crate foam on the side of a car, and a guy walking in front of the car holding the foam vs. not.  :)

### Attacking Millimeter Wave Radars
Tesla Model S has Millimeter Wave Radar.  measures distance, angle, speed, shape from short to long distance (30-250m).  Used for ACC, Collision Avoidance and Blind Spot detection.

Risks:
* Not stoping when it should, eg. impending accident.
* Not alerting you of obstacles in the blind spot.

Very similar operation as the Ultrasonic Sensors, but uses RF.  This is much harder because it travels at the speed of light.  Have to use modulation scheme, [FMCW](https://en.wikipedia.org/wiki/Continuous-wave_radar) at 24GHz or 76-77GHz.

The test gear they used was 3x the price of the Tesla, much thanks to KeyInsight for providing them access to the gear.  :)  Could be done more cheaply by buying your own Radar and using it as a jammer.

Radar outputs at 76.65GHz, 450MHz bandwidth, FMCW modulation.

#### Jamming
Output a similar RF signal, sweeping or fixed frequency.  Beautiful demo video of autopilot in Hold mode, with a car in front, turning on the Radar interferer, and the blue car disappears from the display.

#### Spoofing
Can spoof the distance to the car ahead.  No video.

### Attacking Cameras
Lane departure warning
lane keeping
traffic sign recogniztion
parking assistance

If the camera doesn't work, the car may not steer when it should (eg. in a curve).  The attack we have is a blinding attack.  Can use:
* LED spot $10
* Laser Pointer $9
* Infrared LED spot $11

Demoed blinding w/ laser, resulting in permanently damaged the camera.  Infrared LED didn't work very well.

Tested blinding camera on Tesla.  Good news: the car immediately asks you to take over; a relieving response.

They notified Tesla.  Their response is that they appreciate the work put in to research attacks against the sensors, and they're looking into the results.

### Countermeasures
* Sensors fail safe
   a. zero or maximum
   b. detect jamming directly
* Sensore redundancy
   a. mimo system
   b. different types of sensors
* Sensor data fusion
   a. if the sensors disagree, stop.

### What's next
* Moving vehicle experiences
* Obtain range and angle measurement on radar
* Increase attack range
