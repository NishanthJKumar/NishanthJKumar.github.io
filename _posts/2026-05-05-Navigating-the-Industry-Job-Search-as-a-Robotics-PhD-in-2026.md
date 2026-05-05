---
layout: default
title: Navigating the Industry Job Search as a Robotics PhD in 2026.
date: 2026-05-05 00:00:01
excerpt_separator: <!--more-->
---

After having decided to wrap up my PhD and graduate, I recently found myself having to go through the actual industry job search process. Fortunately for me, a number of other people have written useful guides and advice on how to effectively search for a research-adjacent job in AI (see [this](https://twopug.com/interview-prep/), [this](https://mimansajaiswal.github.io/posts/llm-ml-job-interviews-fall-2024-process/), [this](https://careerservices.fas.harvard.edu/resources/rora-technical-interview-guide-for-research-scientists/), and [this](https://natolambert.com/writing/ai-phd-job-hunt)). However, my experience looking for jobs in robotics ended up being different enough that I thought it might be useful for me to write up. So here is my contribution to the "job search advice for PhD's" genre.

<!--more-->

Obligatory disclaimers: this is heavily geared to robotics/embodied AI-adjacent PhD students or new grads looking for research scientist and research engineer roles at tech companies. It is also heavily biased to my particular experience on the market between November 2025 and March 2026. Take it with an appropriately-sized grain-of-salt depending on how different your context is from mine.

# Timelines
The rough process for signing an offer at a company in industry is this:

1. The pre-interview phase
    a. Reach out, network, and try to get the attention of as many places of interest.
    b. Prep interview materials and start seriously studying for your upcoming interviews
2. Go through interview processes at all the different choices: line up offers
3. Negotiate and sign an offer

Step 1 is often the longest part of the process because it's the one that is least in your control (you never know how long it might take to get a particular company/recruiter/hiring manager's attention; more advice on doing this below). Once you're there, going through step 2 is much more in your control: you can often work with the company or recruiter to speed-up or slow-down processes given a valid reason (e.g. slowing down because you need more time to prepare properly, speeding up because you're at more advanced stages already with other companies and anticipate deadlines). 

As you've probably heard before, it tends to be most productive to be at stage 3 simultaneously with multiple different companies (this lets you know what all your options are, and makes it easier for companies to calibrate their own offers and pitches to you based on the other options you have). Given this, here's the rough timeline I followed for my job search.

I took between 1 and 2 months for stage 1 (November and December), 2 months for stage 2 (January and February) and 3 ish weeks for stage 3 (in March). As a rule of thumb, I think it's helpful to plan to start Stage 1 around 4-5 months before you intend to graduate, though I haven't seen much downside in starting earlier.

In general, I'd recommend budgeting 1-2 months for prep, 1-2 months for actual interviews. I wouldn't worry too much about the time taken for stage 3: that tends to vary significantly based on your situation and the specific companies you're talking to.


# Getting interviews
- Reach out and talk to as many people as possible
    - Don't be too shy/think that a connection is too weak. One of the most exciting offers I ended up getting came from a Twitter DM for instance.
    - It's also a good idea to do this to get a sense for interviews + what rough ballparks for salaries are (especially from friends who might be willing to talk about this).
    - In general, especially for competitive roles at well-known companies, I found that it was much much easier to get foot in the door with a referral/if you know someone.
- Protect your time: it's surprisingly easy to find yourself having days and days where you just talk to recruiters and headhunters about fit. It's good to book a lot of these in the beginning, but you probably want to taper off over time and only seriously pursue opportunitites you're interested in.
    - I also found that scheduling a lot of these initial chats can start taking away from your time to do research/prep for other interviews. I found it useful to set aside 1-2 days a week in which I would schedule these chats (e.g. Mondays and Tuesdays) and leave all other days open to protect my time.
- Apply broadly: you very likely have more broad experience than you might think (e.g. I've worked with LLMs and VLMs, agents, CV, NLP, genai, etc. in the context of robotics). This often means you will be a surprisingly good fit for roles you didn't expect to be a fit for (e.g. I ended up successfully recruiting for several LLM-posttraining roles despite predominantly having robotics experience). I found it very useful to explore my options broadly and learn about what different teams and orgs are working on or looking for. In general, I found that most companies and teams did not care too much that I hadn't previously worked directly on or published in their area of interest (e.g. LLMs and RL for coding), but rather that I had some relevant experience (e.g. I'd worked with LLMs before and had done RL on them for one reason or another) and was willing to learn.

# Interview Prep
In general, I'd recommend asking recruiters (or whoever you're talking to at the company) to give you as much information as possible about what to expect from each interview.
I found that there are several situations where recruiters are allowed to give out more information on a call, but not over email, so it is often useful to ask for a brief call to discuss interview information.
In addition to the prep described below, I would almost always use an LLM to give me mock problems based on all the information I was given by a recruiter or hiring manager. I'd do as many of these problems as seemed relevant in an effort to practice as much as possible.

## Numpy + Pytorch Coding Interviews (50% of all interviews I took)
The vast majority of interviews I had to take (across all roles I had to apply for) ended up being some form of ML or tensor manipulation problem in Numpy or PyTorch (Jax was also an option, but I never used it). 
These interviews tend to be hard because they require broad conceptual ML knowledge (e.g. remembering the k-means algorithm, knowing how to implement RoPE for an LLM) as well as intuition for tensor manipulation helpers and library functions in numpy/torch.
Put simply: you need to have a lot of concepts and programming knowledge *at your fingertips*: most of these intervies are 45 mins or less and you simply don't have time to spend time remembering how an algorithm works or re-discovering how basic numpy or torch operations work.
I found personally (and heard from several friends) that these interviews deserve their own focused prep, even if you are an ML researcher/practitioner (because many of them will test concepts + tricks you won't likely be encountering day-to-day).

So what exactly should you study, and how should you practice? I found it very useful to pick a concept and have an LLM (e.g. ChatGPT) generate me a stub file + some test cases simulating an interview. I'd then fill in the stub with a solution and ask the LLM to critique it. If I couldn't implement it, I'd ask the LLM to give me hints/help me along. I'd repeat this process with spaced-repetition until I felt I could do all the problems I expected to encounter well within an interview time limit. I've also included a link for each section to an online course/resource that I used that might be helpful.

Based on the interviews I had, I'd recommend the following curriculum:
0. As [Jenya says here](https://twopug.com/interview-prep-ml-grind/): get really good at [einsum](https://numpy.org/doc/stable/reference/generated/numpy.einsum.html) and adopt Noam Shazeer's [shape suffixes for variable naming](https://twopug.com/interview-prep-ml-grind/). These will come in extremely handy for everything that comes after.
1. Get very comfortable with tensor manipulation and writing vectorized code (e.g. how do you compute the distances between every pair of points in a (N x 3) array?)
    1. Resource: [Sasha Rush's Tensor Puzzlers](https://github.com/srush/Tensor-Puzzles) - these are pretty illuminating to do; though you don't need to do them all in a single line.
    1. K-means clustering
    1. K-NN classifier
2. Work on implementing various neural network layers from scratch (both forward and backward passes).
    1. Resource: [CS 231N](https://cs231n.stanford.edu/assignments.html); I'd recommend doing all the assignments in particular.
    1. Logistic regression
    1. MLP with softmax
    1. MLP with MSE
    1. 2D convolution layer (for looping is okay for stride, but everything else should be vectorized)
    1. A simple ViT layer
3. Understand LLMs in-and-out (basically [hw1](https://github.com/stanford-cs336/assignment1-basics/tree/main) from this)
    1. Resource: [CS 336](https://cs336.stanford.edu/); I'd recommend doing homeworks 1 and 2 thoroughly, and skimming/being familiar with the rest.
    1. Single-headed attention (forward and backward without autograd)
    1. Multi-headed attention (forward only should suffice)
    1. Byte-pair encoding (BPE) and how to write simple tokenizers from scratch
    1. Embedding layer
    1. A full transformer block as found in a modern LLM
    1. KV-caching
    1. (Challenge) simple LLM from scratch: start with some simple text and then implement all the necessary components (tokenization, embedding, transformer blocks, output projection, mapping back to vocab, kv-caching) from scratch in a single python file. See if you can implement everything with no hints/guidance in ~1 hour, and test that you can train and then run inference on the final model!

## ML System Design Interviews (15% of all interviews I took)
These tended to be quite varied and dependent on the team I was interviewing for; the topic was often closely related to the team I was interviewing for (e.g. at self-driving car companies, I was asked to design some sub-components of an ML pipeline for driving vs. at home robotics startups, I was asked to design end-to-end manipulation systems).
I don't have too much preparation advice for these interviews aside from (1) knowing your own research very well, and (2) making sure to spend time catching up on state-of-the-art approaches that might be relevant to the team/role you're interviewing for. In several of these interviews, I was asked to either explain how one of my own papers might be applied to solve a particular design question, or explain how a popular technique from the literature might apply. For example, one interview asked me something along the lines of: "say we want to build a system that can learn to fold laundry from human demonstrations — walk me through how you'd design the data collection pipeline, what policy architecture you'd use, and how you'd improve the success rate online." This then naturally led into a discussion about tradeoffs between different policy representations (e.g. diffusion policy vs. action chunking with transformers), how much real-world data you'd actually need, and where sim-to-real transfer tends to break down for deformable objects. Similar to the ML/coding interviews above, I often practiced for these by asking LLMs to simulate example interviews and then critique my responses.

From the feedback I was given, my sense was that the main thing interviewers were looking for was a good high-level understanding of different approaches and their particular tradeoffs. For this reason, I think it's useful to spend some time in the beginning structuring your answer, and also to make sure you start each section by clearly stating your high-level approach and reasoning before diving into the details. Interviewers want to see that you can think about systems at the right level of abstraction and make reasonable design decisions under uncertainty — not that you have every implementation detail memorized.

A few other things I found helpful:
- **Start by clarifying the problem.** Ask questions about the constraints: what's the latency budget? How much data do we have? Is this online or offline? What are the failure modes we care most about? This both buys you thinking time and shows you know that design decisions depend heavily on context.
- **Draw out a clear pipeline early.** Sketching out (even with words) the major components and data flow at the start gives you and the interviewer a shared reference point. It also makes it much easier to zoom in on any particular component when they inevitably ask you to go deeper. The structure of overview-first then dive into details sworked quite well for me in most of these interviews.
- **Know the landscape of approaches for your area.** For instance, if you're interviewing at a robotics company, you should be able to speak fluently about the tradeoffs between behavior cloning vs. RL, diffusion policies vs. autoregressive action prediction, end-to-end vs. modular pipelines, etc. You don't need to have implemented all of these, but you should be able to articulate when you'd reach for one over the other and why.
- **Be honest about what you don't know.** I found that interviewers responded well when I said something like "I haven't worked with X directly, but my understanding is that it works by doing Y, and I'd want to validate that assumption by doing Z." This came across much better than trying to bluff through a topic I wasn't confident about.


## Conceptual (verbal) interviews (15% of all interviews I took)
One of the downsides of AI and robotics being so broad is that the concepts you might be expected to know are also quite broad.
Here is a (non-exhaustive) list of areas I had to know:
- General ML
    - Generative vs. discriminative models
    - Bias vs. Variance
    - Overfitting vs. Underfitting
    - L1 vs. L2 regularization; other forms of regularization
    - Common functions and knowing their gradients
        - Sigmoid
        - BCE
        - Softmax
        - NLL
        - Batchnorm
        - Layernorm
        - Groupnorm
        - Precision, Recall, F1
        - Logistic regression
        - K-means
        - KNN
        - Entropy
        - Cross-entropy
        - KL Divergence
- Reinforcement Learning
    - Policy gradient vs. value function methods
    - On-policy vs off-policy methods
    - Planning methods: Value Iteration and Policy Iteration (be able to write up and explain the the bellman backup)
    - Advantage and baselines
    - Q-learning (know the learning update; understand tabular vs. deep network case)
    - PPO (be able to write out and explain objective)
    - GRPO (and how is it bettter than PPO + where does it fail)
- Diffusion models, flow-matching (know updates equations, where to use each, time embedding, how to use in robotics via diffusion policy, etc.)
- Optimization
    - SGD
    - Momentum
    - RMSProp
    - Adam
    - AdamW
    - Learning rate scheduling approaches (cosine scheduling)
- Foundation models
    - Everything about LLMs
        - Tokenization, embedding layers, architecture design, MoE design, training tricks (the first couple lectures of [CS 336](https://cs336.stanford.edu/) are very useful)
    - How to get to VLMs (conceptually) from LLMs
    - Quantization
- Robotics
    - Robot learning
        - VLAs
            - Popular VLA network architectures such as those used by Physical Intelligence and NVIDIA (in detail), using video model backbones
            - Action chunking and how it is used
        - Diffusion Policy and Flow Matching
        - Data collection + systems setup
        - sim2real RL and associated tooling
    - Controls
        - How does a simple PID controller work? (useful to know how to implement)
        - Impedance control (useful to know how to implement)
        - Operational-space control
    - SLAM
    - Classical robotics
        - FK and IK
        - Motion Planning, RRTs and PRMs
        - TAMP
    - Sensors, Vision and Data Collection
        - Some popular ways to collect data for robot policy learning (UMI, real-to-sim, VR)
        - Common sensors on a robot and what you can do with them (tradeoffs of depth/IR cameras vs. stereo vision, etc.)
        - Data collection and cleaning pipelines

## Research interviews (10% of all interviews I took)
These interviews come in two flavors:
1. A 'fit' interview with the hiring manager where they ask you about your work and discuss your interest in the role
1. A full-fledged research presentation, followed by Q&A

Of these, the former was much more common than the latter. My biggest recommendation is to prepare several slide decks ranging from 5 - 20 mins long that provide increasingly detailed overviews of your PhD research. Before each fit chat, you can also add a slide at the end about your current interests + what kind of things you'd like to work at if you take the role you're being considered for.

I don't have much advice for research talks aside from recommending that you deliberately keep it short. Instead of presenting multiple projects, just give a broad overview of your research at the start and then zoom into one. Often, companies don't care that much about the overall arc of your PhD (in the way that academia might), but rather more about your specific technical skills. They will ask you a lot of questions and really try to understand what you're saying. I got the sense that it is much stronger to present one thing well and have your interviewers come away with the belief that you really understand it, over presenting multiple things at a high-level. Also, make sure to talk about how your work is relevant/useful to the role: running out of time before you get to this is common and unfortunate.

## Behavioral interviews (10% of all interviews I took)
These are fairly straightforward: make sure to use the [STAR method](https://capd.mit.edu/resources/the-star-method-for-behavioral-interviews/), and consider augmenting to STAR-L (add on a 'learning' at the end of your answer and talk about how that leadning has helped you since).
I'd also recommend researching the interviewer + the company's latest work. I had several interviews where I mentioned something about the interviewer/company's work that was relevant to the conversation and I was told afterwards that this left them with a strongly positive impression about my genuine interest.

# The mental game
Probably the hardest part of interviewing for me was playing the "mental game" of interviewing well: coping with the stress, anxiety, and comparison that comes part and parcel with the process. Here are some tips from my experience, in the hope that they will help you play the game better than I did.

**Expect to get rejected — a lot.** Companies receive far more applicants than they can possibly hire and interviewers will deliberately probe the edges of your knowledge. You will likely bomb an interview at at least one company, and walk out knowing you could have nailed it with one more week of prep. That sting is real. I was rejected after at least one interview from about 50% of the companies I seriously pursued, and colleagues told me that was a pretty good ratio given their own experiences. I think [this speech](https://youtu.be/pqWUuYTcG-o?si=UjZ5wu5lZfS9V3B9&t=794) from Roger Federer (my favorite tennis player!) captures a useful mindset: "When you're playing a point, it has to be the most important thing in the world, and it is. But when it's behind you, it's behind you... The best in the world are not the best because they win every point. It's because they know they'll lose again and again, and have learned how to deal with it."

**Treat interviewing as a full-time job, and pace yourself accordingly.** Between the interviews themselves and the reading, slide prep, and background research each one requires, it is very hard to seriously work on anything else. Ideally, by the time you start interviewing, you'd be mostly done with your research rather than pushing toward a first-author deadline. I made the mistake of scheduling interviews back-to-back with no breathing room, and burned out quickly. Build in recovery days, and make it a priority to protect time for things that have nothing to do with interviewing.

**Don't compare outcomes.** If you're a PhD student in AI or robotics right now, you almost certainly know people who landed eye-popping offers or unusually impressive titles. It is very hard not to use those as your benchmark. I spent more time than I'd like to admit refreshing compensation-sharing threads and mentally measuring my offers against numbers I'd heard secondhand from friends. This was not productive. The reality is that there is a lot of randomness in this process that has nothing to do with how good you are: companies have sudden hiring freezes, another candidate happens to know someone on the team, the role you were perfect for gets restructured the week before your final round. You can do everything right and still not get the outcome you wanted. Try to evaluate your offers on their own terms — does this role excite you, will you learn, does the idea of working with your teammates sound fun — rather than against someone else's outcome that came from a completely different set of circumstances. And remember that careers are long: not landing your dream role this cycle doesn't close the door. Perhaps this outcome [was the right path for you at this time](https://mitadmissions.org/blogs/entry/choosing-to-become-yourself/), and even if not, you can always try again in the future when your experience is deeper and circumstances line up better.

**Focus on the conversations, not the verdicts.** A mentor of mine gave me a helpful way of looking at interviewing in general: in every round, you get thirty to sixty minutes with a smart person who works in roughly your area and is genuinely curious about you and your work. When I stopped thinking of interviews as judgment and started treating them as conversations, I relaxed, asked better questions, and — ironically — performed better. Even the rounds that went poorly left me with something: a paper I hadn't read, a new way of thinking about a problem, or just a clearer picture of what I know and don't know. Treating interviews as just conversations/learning opportunities is certainly hard to keep up, especially when you know you're being explicitly evaluated, but it helped take away quite a bit of my stress both during the interview itself. It also helped me keep my head up after several rejections.


---

That's all I have. If any of this has been helpful, or if you have additional suggestions or thoughts you'd like to share about interviewing based on your experience, feel free to [email me](https://nishanthjkumar.com/contact-me/): I'd love to hear from you. Best of luck with your interviews!

*Thanks to [Sahit Chintalapudi](https://sahitc.com/), [Will Shen](https://shen.nz/), [Aidan Curtis](https://aidanreececurtis.com/) and [Rohan Chitnis](https://rohanchitnis.com/) for reviewing early drafts of this post and providing helpful feedback.*