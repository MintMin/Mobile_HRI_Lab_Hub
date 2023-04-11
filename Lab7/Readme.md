# Interact with with people + chatty robot


**List the names and NetID for your partners here.

Qianti Min qm45
Ananya Ganesh ag2227
Calvin Tirrell cat248
Jonah Brucker-Cohen jb2662


In this lab, let's try out some moves with our robots and make them talk!


## Prep
If you haven't finished your robot chassis, try to wrap it up in this lab.


### For this lab, you will need:
1. Your laptop
2. Your hoverbot
3. Speaker (Will arrive later this week, I will make a post when they arrive. I have two for now.)


### Deliverables for this lab are:


1. Before/after sketches of your robot interacting with people
2. A video sketch of your designed interaction
3. Videos trying out elicited interactions
4. Before/after sketch of your robot interacting with people through motion and voice
5. A video sketch of your designed interaction
6. Videos trying out elicited verbal interaction




## Lab Overview
For this assignment, you are going to:

A) [Prototype Speech Interaction](#part-a-prototype-speech-interaction)

B) [Prototype Interaction Routines](#part-b-prototype-interaction-routines)

C) [Test out some interaction](#part-c-test-out-some-interaction)

Labs are due on Tuesdays after Spring break. Make sure this page is linked to your main class hub page.


## Part A. Prototype Speech Interaction

Try out the robot's ability to generate speech:
``` bash
# In a RPi terminal
sudo apt-get install espeak
```

``` bash
# espeak "text-you-want-your-robot-to-say"
espeak "Hello"
espeak "how are you"
```

You can also change the speed and pitch of the voice. Check out the instructions [here](https://espeak.sourceforge.net/commands.html).

## Part B. Prototype Interaction Routines

So far, we only used two joysticks on the controller to give robots moves. We should utilize the other buttons to trigger some pre-defined routines.
I suggest that you modify the script in the [joy_teleop_keymapping package](https://github.com/FAR-Lab/mobilehri2023/blob/main/joy_teleop_keymapping/joy_teleop_keymapping/keymapping_node.py).

Specifically, in the `sendCommand()` function
``` python
def sendCommand(self, msg):
        t = Twist()
        # safety lock, press top left button
        if msg.buttons[4] == 1.0:
            t.linear.x = msg.axes[1] # for some of you, the wheel is spinning too fast, this is also a good place to slow them down.
            # use to represent angular velocity
            t.angular.z = msg.axes[3]
            self.twist_pub.publish(t)
        else:
            t.linear.x = 0.0
            t.angular.z = 0.0
            self.twist_pub.publish(t)
```
Here, we programmed the following logic, 
- if the 4th button is pressed (our safety button), we publish twist commands based on inputs form the first and third axes (the two joysticks).

Feel free to add additional `if-else` conditions to trigger different motion routines! Here is an example of a wiggle behavior (pseudo code).
``` python
import time

...

if wiggle_button_pressed:
      start = time.time() # get current time
      while time.time() <= start + 1: # do the following command for 1 second
          t.linear.x = 0.0
          t.angular.z = variable_depending_on_time
          self.twist_pub.publish(t)
          time.sleep(0.2) # good to pause a little bit in practice
      self.twist_pub.publish(t)
      start = time.time()
      while time.time() <= start + 1: # do the following command for 1 second
          t.linear.x = 0.0
          t.angular.z = variable_depending_on_time
          self.twist_pub.publish(t)
          time.sleep(0.2) # good to pause a little bit in practice
```
## Part C. Test out some interaction!

Based on your final project proposal, sketch out a simple interaction scenario where your robot is interacting (verbally and/or physically) with at least one person. The robot must interact with at least one person. 
1. Scout out the location for the interaction. What are the features and existing activities in the space?

As we anticipate the interactions to occur outdoors, we will initially test our robot in the open space outside the Bloomberg building. The landscape of the area is not ideal, with many obstacles and people often walking or resting.

2. Stage the interaction you expect with your robot to go. (Remember to take a video.)
- Greetings 
- Dance

3. Figure out 2-3 interaction triggers that the Wizard will respond to for the interaction. Are there things that need to be done to make it eaiser to spot these triggers? For example, one trigger might be if a person is looking at the robot. Another is if someone is gesturing at the robot.

- Trigger 1: person initiates interaction with robot, ie: “hello there!” or “hi there”
- Trigger 2: person doesn’t want to be bothered, ie: “go away” or “leave me alone”
- Trigger 3: person asks about the robot, ie: “what do you do?” or “you speak or dance?”

4. Figure out 2-3 interaction routines that the robot should use for the interaction. For example, maybe the robot  backs up slightly before going forward to signal that its going to go, makes angry noises when it is blocked, or wiggles side to side to indicate confusion

- Interaction 1: The robot reaches a safe distance from the person/ people. Cues the interaction trigger and spins twice.
- Interaction 2: On response from the audience, the robot performs one of two dance routines. 

Dance routines 
- A simple shuffle - half turns on both wheels
- Four complete turns of increasing then decreasing circles 


5. Try unscripted interaction with at least 5 people. (Again, remember to take a video; this means you have to get their permission to record them, but not tell them what to do. Please don't shoot creeper videos.) That is, don't tell the people involved in the interaction what to do. Use WoZ to enable the people to see how the interaction would unfold if the robot were autonomous. 

While our robot does the basic actions we require, we ran into some anger issues with our robot over spring break. Our robot had difficulty understanding the speech and motion aspect at the same time and started bolting towards a wall without any assistance from our console. 

We decided our robot needs a break too and have given it some cool down time until we figure out how to tackle this. We have elaborated on the issues below.

6. Reflection on what you learned about the interaction; revise the interaction sketch with your new insights.Be mindful of the others around you. Be safe.

Please see the OUR FEEDBACK session for more details.


### Again, the deliverables for this lab are:


1. Before/after sketches of your robot interacting with people
![sketch](https://user-images.githubusercontent.com/32082801/230128717-ab02b1df-094a-42de-b699-760b42bba8e2.jpg)

2. A video sketch of your designed interaction
3. Videos trying out elicited interactions
4. Before/after sketch of your robot interacting with people through motion and voice
![sketch with motion](https://user-images.githubusercontent.com/32082801/230128791-cd8c46a8-7aa2-4c16-9e07-8a8652270fe1.jpg)

5. A video sketch of your designed interaction
6. Videos trying out elicited verbal interaction


### Our Feedback:

1. The speaker works only without the motion-controlling system 
- the volume of the speaker is low even when we adjust it to maximum  
https://drive.google.com/file/d/1wYot9_NBTfHrmmH22PN0trU-OmqvmVLH/view?usp=sharing

2. We got tons of errors when the speaker interfering with motion
![Screenshot 2023-04-05 at 12 08 02 PM](https://user-images.githubusercontent.com/32082801/231191855-8112dfd2-37e9-4c7f-8b85-a5a31e17b97f.png)
- The motorError here was new and we did not know how to rectify it,  probably since it crashed on the wall.
![Screenshot 2023-04-05 at 12 14 14 PM](https://user-images.githubusercontent.com/32082801/231191979-178e3f52-cdc3-4e36-835a-bc50a7730b2a.png)
- The below image shows how the robot was ignoring the user prompt to cancel motion and kept going in circles. This might be due to the watchdog timer. But still needs to be investigated. Frankly, it was a bit scary - almost like the robot had developed intelligence and was going berserk.  
![error2](https://user-images.githubusercontent.com/32082801/231208238-092443ea-4d3f-4523-93a2-d311f2483afa.png)

3. The robot still moves...but in an AGGRESSIVE way (videos highly recommended!!!)
- The robot is highly sensitive to joystick movements, responding even to small changes  
https://drive.google.com/file/d/1XoZRgBpjG7P-Kzh3XNtBHL0kq4SKDSuM/view?usp=share_link
- Its speed is also dangerously high, causing it to collide with walls and obstacles. We suspect that the issue may be related to the watchdog code  
https://drive.google.com/file/d/1Ny5N47QGbkkt_0Kh2q__kygiYCe6-sw7/view?usp=sharing

4. Future Steps
- Fix initial velocity
- Check key mapping
- Map Dance moves
- Add new Chassis
- Fix wiring - make it look better quite a mess now



