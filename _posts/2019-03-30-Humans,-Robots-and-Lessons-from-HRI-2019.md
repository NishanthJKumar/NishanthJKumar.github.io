---
tags: Research Conference
---

Over winter break, I had the opportunity to write an extended abstract (my first first-author thing!) for an idea I’d been kicking around with some other members of my lab. We ended up submitting said abstract to VAM-HRI 2019: a workshop centered on Mixed-Reality for Human-Robot Interaction. Fortunately enough, our work got accepted (find it here!) and I had the incredible opportunity to miss a week of classes to attend Human-Robot Interaction 2019 in South Korea! This was my first ever robotics conference and what follows will be my thoughts from the conference, roughly organized as below:

- Major takeaways + trends from HRI 2019
- Robot companies + demos!
- Overall thoughts

# Major Takeaways and Trends from HRI 2019
## 1. The rise of Virtual, Augmented and Mixed Reality
I admit that this may be my own biased opinion. After all, my primary purpose behind going to this conference was to attend the VAM (Virtual, Augmented and Mixed-Reality) workshop where I myself had authored work that heavily relied on Mixed Reality. But, I was (pleasantly) surprised to see quite a few people that weren’t just part of VAM-HRI actually use VR, AR or MR for things from robot learning to conducting experiments on social robots.

![AR Robot](/images/HRI-pics/AR_small.jpg){: .align-center}

Some used VR or AR for prototyping and design, and many others used it for experiments. Of particular interest was the fact that three different works attempted to use VAM technologies to facilitate robot Learning from Demonstration (LfD). Two of these focused on methods to build large-scale VR simulations of environments and tasks to collect a very large amount of training data from users via the internet.  This idea has been around for a while (there has even been some work from our lab about it!) but it was encouraging to see other people attempting to take it forward. Indeed, it would be incredible if we could have some sort of game where players could record themselves doing common tasks and we could then use these recordings to train a robot (in simulation) to do the same tasks (and hopefully eventually do them in real life!). The third LfD work was unique in that it proposed to use Mixed Reality holograms to provide constraints on demonstrations being collected. This was an incredibly fascinating (and apt!) use of MR for robot learning and I ended up tracking down the authors and attempting to pick their brains on how they’d come up with this idea and what they planned to do with it in the future.

![AR Prezi](/images/HRI-pics/AR_Prezi.jpg){: .align-center}

Overall however, there were many more works that used VR, AR or MR than I’d expected. Earlier this year, some (smarter) lab members made me have the key realization that VR, AR and MR could act like new communication modalities between humans and robots. It was interesting and very exciting to see others realize this too and use these modalities in significant and unique ways!

## 2. Ethics and Accountability

This probably stuck with me because of how surprised I was to hear about it. As a (still-developing) robotics researcher, I’m used to hearing technical computer science or engineering fueled discussions. So hearing someone raise ethical concerns and begin talking about public policy and law while describing human-robot experiments was surprising to say the least.

Before attending the conference, I didn’t think ethics or accountability were major problems that deserved attention – primarily because robots aren’t sufficiently advanced to be significantly dangerous yet. ‘We can figure this out after we have intelligent and generally-capable robots’ – I thought. I’m really glad multiple people have devoted more thought to this issue than I had. People raised important issues regarding self-driving cars and drones and pointed out that these inventions are already here and are already being used to do [questionable things](https://www.bbc.com/news/uk-46827542). At one point, there was an interesting debate about the difference between a robot and a pencil. Is a robot only a tool who’s accountability lies solely with the wielder? Or – given these are intelligent, decision-making agents – are the programmers or makers accountable?

While people debated back and forth on what the legal and ethical status of robots should be, most concurred that we as researchers need to be thinking about these problems as we build our robots and not after the fact.

## 3. Robots as caregivers

Before the conference, I’d been tangentially aware that people were thinking about using robots to care for seniors, patients and children. What I didn’t know was just how many people were working on this and how serious they were about it. And it turns out there are quite a lot of people that are very serious about this.

There turned out to be two entire sessions of the conference dedicated to caregiving robots: “Robots in care” and “Robots engaging children”. I was consistently surprised by the kind of challenges people were solving for these domains; the conference’s best paper ended up being about the best way for a robot to feed a human – something I’d never even considered was a challenging technical problem (and one that had an interesting and quite innovative solution at that!). There were quite a few people that conducted large-scale studies on what users would want from a robot caregiver, and while results differed, the common fact was that almost every user wants a caregiving robot. This was incredibly interesting because I’m used to people being afraid that robots will steal their jobs; but here is a legitimate, real-world domain where people overwhelmingly want robots.


# Robot companies + demos!
One of the coolest things I got to see at the conference was all the companies and demos they’d brought. There were a lot, but I only got to visit and take pictures of a few, which I’ll try to summarize them (with pictures!) below.

## A simulated robot arm for CAD
So I unfortunately forgot this company’s name – but their demo was one of the coolest I’ve seen. They had a physical robotic arm with a simulation where you could create virtual objects but feel them for real using the physical arm. Unfortunately, we were informed we’d have to ask for a quote if we’d like to own one…

![CAD Arm demo](/images/HRI-pics/CAD_arm.jpg){: .align-center}

## Robotis

This was a company that made various small robots for education or research. They’re intended to be cheap so the average school or small research lab could buy them. Despite this, they were pretty cool and had impressive demos.

![Robotis hands](/images/HRI-pics/robotis_hands.jpg){: .align-center}

![Robotic Classifier](/images/HRI-pics/classification.jpg){: .align-center}

## Furhat Robotics

This was by far the most interesting company I saw and I ended up talking to them for quite a while. It’s difficult to describe their product well – so I’ll just show you:

![Furhat Robotics](/images/HRI-pics/furhat.png){: .align-center}

Essentially, the robot is a voice assistant with a reconfigurable face. I was shown a demo where the face and voice were quickly shifted between popular celebrities (so I technically got to meet Obama and Arnold Schwarzenegger) and it was pretty cool (although sometimes difficult to identify the celebrities’ faces).  

The robot can track people with a camera, follow their face or voice and hold a conversation (albeit with somewhat weird lip movement and facial expressions). I tried to test the tracking and it was quite impressive, especially given this was in a large hall with lots of background noise.

The most interesting thing about the company though was their customers. There’s a lot of what you might expect: airports or companies wanting something to man the information desk 24/7. But there’s also apparently been a steady demand from HR departments at some large companies. Why? Because Furhat robots can conduct HR training programmes in a completely unbiased way. These robots are designed to interact and respond to language without a single care for factors like age, sex or ethnicity – which is apparently a big draw for companies hoping to institute fairer training programmes and policies. This was a pretty surprising and interesting use-case for social robots.

# Overall Thoughts

Attending this conference was probably one of the best things I’ve done in recent times. I got to meet and interact with so many PhD students doing exciting work and also a few amazing professors (like [Brad Hayes](http://www.bradhayes.info/) and [Heather Knight](http://eecs.oregonstate.edu/people/knight-heather)). I even got to see some superstars that I’d only ever read about like [Sidd Srinivasa](https://goodrobot.ai/) and [Anca Dragan](http://people.eecs.berkeley.edu/~anca/) (it felt like spotting celebrities!).

Perhaps the most significant thing was simply getting to experience what a real large robotics conference is like. Two things that stood out were how large and international the robotics and intelligence community is. It was quite shocking to realize that I was attending a conference on a specific sub-field of robotics (human-robot interaction) and there were more than 1000 other attendees from all around the world. The fact that so many intelligent people from so many backgrounds are putting their careers into the field is incredibly heartening and inspiring. I left Korea more convinced than ever that I want to spend my life working with robots.
