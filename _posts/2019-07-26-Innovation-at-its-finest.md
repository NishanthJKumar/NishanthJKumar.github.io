---
tags: Research For-Laughs
---

A while ago, I was attempting to run last-minute experiments to finish up a paper just in time for a conference deadline.

![Robot Button Pressing](/images/innovation-pics/Robot_Experiment.png){: .align-center}

Our project essentially involved getting our beautiful white robot-arm shown above to press the buttons on the panel in front of it. Unfortunately for us, our approach required lots of data of the robot pressing different buttons (captured with the camera you see on that tripod there). Fortunately for us though, I had automated the data collection – so I simply started my button-pressing script, left for the night and came back to find all the data we needed!

However, to my great surprise, our algorithm failed rather catastrophically when I fed in this data. After hours of debugging, I realized that most of the images I’d collected had been dark. Literally – the camera feed had been pitch black. Someone had turned off the lights!!!

After a while spent wondering which evil, soulless person would so cruelly mess with our experiment right before a deadline, I found the culprit.

![Auto Switch](/images/innovation-pics/switch.png){: .align-center}

It turned out the room had an automatic, motion-activated light switch…

This left me with a unique problem: I needed to find a way to keep the lights on. Being an Engineering student, I began searching for materials to construct something to fool the motion-sensor. I needed a solution that would be simple and fast-to-build given it was already late and I very much did not want to deal with this problem.

Here’s what I came up with:

![Auto Switch](/images/innovation-pics/disco_ball.png){: .align-center}

This is exactly what it looks like: a disco ball with a folded piece of paper taped to it. I chose a disco ball because its speed of rotation was slow enough that the sensor would register some movement (as opposed to a fan, which was my first idea). The paper was to fool the sensor into picking up actual movement…

I was extremely proud of myself at the time. Now, the robot would collect the data we needed and I could happily walk in the next morning, ready to run experiments!

Unfortunately for us, it turned out that the paper-on-a-disco-ball wasn’t a stroke of genius. I walked in the next morning to find a dark room.

Moral of the story: if you choose to become a robotics researcher, know that you’ll encounter the weirdest, most unexpected and annoying bugs right before deadlines…
