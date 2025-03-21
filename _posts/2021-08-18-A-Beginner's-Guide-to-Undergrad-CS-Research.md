---
layout: default
title: A Beginner's Guide to Undergrad CS Research
date: 2021-08-18 00:00:01
---

Computer Science has become quite the popular field these days, [especially amongst undergraduates](https://cra.org/wp-content/uploads/2017/02/Generation-CS.pdf). As a result, there are a *lot* more CS-related resources now than there ever were before. There are tons of books, lecture videos, guides, articles, and even memes about everything from understanding difficult CS concepts for coursework, to 'cracking' technical interviews, to applying to CS grad school. However, one aspect of an undergrad CS education that often gets left a bit in the dark is research [1]. While most University undergrads are probably aware that undergrad research opportunities exist, a surprising amount don't *really* know (1) what undergrad research entails, (2) why they should care/potentially try to get involved, and (3) how to actually get a research opportunity. This is unfortunate because there's been an overwhelming recent interest from students in going to CS graduate school or pursuing research-related jobs in industry, which both increasingly require at least *some* undergrad research experience.

In my own case, at the start of my freshman year, I had a pretty good idea of what coursework I'd need to do to get a CS degree, and quickly found out the why and how of recruiting for various summer internships. However, I knew next-to-nothing about undergrad research. I didn't know - for instance - that most Professors' primary responsibility is to do research, that being a "researcher" is a legitimate career option, or that research experience is important for grad school applications. Fortunately for me, I stumbled into some incredible undergrad research opportunities by happy accident. Research changed my life; I loved (and still love!) it so much that I spent my senior year working to [promote undergrad research opportunities within Brown's CS department](http://ur.cs.brown.edu/about/) so that more students get to take advantage of the opportunities I'd gotten. One of the most common things I heard from students and peers is that they wished they had known more about research and gotten involved sooner. This post is an attempt to address that, as well as share some lessons I've learned as an undergrad researcher, by trying to answer three common, big-picture questions about undergrad research: what, why and how?

<!-- vscode-markdown-toc -->
**Table of Contents**

* [What the heck is Undergrad CS Research?](#WhattheheckisUndergradCSResearch)
* [Why should I care?](#WhyshouldIcare)
* [How should I get involved?](#HowshouldIgetinvolved)
* [Some tips and advice](#Sometipsandadvice)
	* [Some Do's and Dont's of Undergrad Research](#SomeDosandDontsofUndergradResearch)
	* [Some Important Things to Keep in Mind](#SomeImportantThingstoKeepinMind)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->


##  1. <a name='WhattheheckisUndergradCSResearch'></a>What the heck is Undergrad CS Research?
CS research basically involves trying to push the boundaries of CS as a field and discover new knowledge about computers. If that sounds like a vague, fairly generic description, that's because it is. One of the cool things about CS research is that it is really broad and hard to draw a precise box around. There are researchers working on everything from [AI to predict protein folding](https://www.nature.com/articles/d41586-020-03348-4) to [proving things quantum computers won't be able to do](https://www.cs.virginia.edu/~robins/The_Limits_of_Quantum_Computers.pdf). Pretty much every cool CS-related invention - from Object-Oriented Programming to web search and the protocols of the Internet - started out as a project in a research lab.

This is all well and good, but it says nothing about what *undergrad* CS research involves. What does an undergrad researcher do on a daily basis? The answer is that, just like the content of CS research itself, it varies. However, there is some general structure in what to expect. 

If you join a lab as an undergrad, you'll probably be mentored by a grad-student (generally, someone working towards their PhD) or post-doc (someone who's finished their PhD) directly, with occasional meetings with one or more Professors. You'll get to work on a project that's directly related to one of the lab's research directions in a very specific sub-field of CS. Especially in the beginning, you'll likely spend a good amount of time reading academic papers and getting yourself acquainted with the lab's work (which can take anywhere from a week to a few months). You may also be asked to work on a "starter project", like implementing an existing paper or solving a problem-set from a related class, to get you up to speed and give you a taste of the kind of work you'll be doing [2]. 

Soon enough, you'll probably be tasked with working on some relatively well scoped-out part of an existing project. Most of the time, this means designing/implementing some code as part of a larger codebase, or implementing a novel algorithm someone on the project has come up with, or designing and running one or more experiments. More rarely (but common with theoretical CS research), you'll be asked to help prove a theorem or do something else that's rather math-heavy like derive the worst-case runtime of a new algorithm. Eventually, you might be asked to help write up the part you worked on as part of an academic paper. What's common between these different tasks is that they're usually fairly concrete: someone's sketched out what needs to be done in broad strokes and your job is to figure out all the details of actually doing it. In this way, these aspects of research are not unlike what a traditional software engineer does.

After working on a few projects, you'll probably have the opportunity to lead your own project, which will pretty-much simulate what being a grad student or professional researcher would be like. Unlike before, this will involve much less concrete things, like finding an interesting problem to work on and designing a completely novel solution for it. On a day-to-day basis, this will likely involve reading lots of papers (a core activity for a researcher at any stage of their career!), having research-related discussions with your mentors/advisors/collaborators and spending a significant amount of time just thinking. These aspects of research are rather significantly different from software engineering because there are no descriptions of what you need to produce, and it could very well be that *no one* has done something similar enough before. This means you're not even really sure where to get started or what sort of tools/frameworks to use. Generally, if you find that you enjoy these rather unstructured, less-concrete parts of research, then it's a pretty strong sign that you'll enjoy being a researcher.

Aside from these technical aspects of actually doing your research, you'll also likely spend time communicating your research by giving talks or poster presentations and attending conferences. However, these commitments are generally few and far between for undergrads when compared to the other aspects of research.

##  2. <a name='WhyshouldIcare'></a>Why should I care?
From the above description of CS research, hopefully it's clear that research offers you the opportunity to (a) pursue an interest in a sub-topic of CS, and (b) learn a lot of interesting/useful skills/knowledge. This is great, but there are also so many other things - like working on a side-project, trying to start a startup, or doing web-dev for that cool new club - that you could do to reap similar benefits. Given this, here are a few benefits that are fairly unique to research:

1. **This is (probably) the best chance you'll get to try it**
    
    Believe it or not, it's exceptionally difficult to get involved with research if you're not at a University. I've met quite a few people who became interested in research *after* graduation and their number one regret is that they didn't take advantage of research opportunities while they were still doing their degree programs. In fact, gaining research experience is one of the most-common reasons that people decide to pursue Master's degrees. Given that it'll probably never be as easy to get involved with research as it is for you right now, you should probably at least give it a try.

1. **You'll figure out if you want to be a researcher or not** 

    It's possible to split all CS-related career paths you could possibly choose to pursue into 2 categories: research (becoming a research scientist, research engineer, professor, etc.) and not-research (software engineering, product management, consulting, tech entrepreneurship, etc.). The general rule I've been told by internship mentors, grad students and Professors is that it is much easier to switch from research to not-research than the other way around. Given this, and the point above, it's incredibly useful to know if a research career is appealing to you or not. There's no better way to figure this out for yourself than to get involved with research and seeing if you like it.

1. **You'll *massively* strengthen grad-school applications (should you choose to apply)** 

    Gaining research experience is probably the single best thing you can do to strengthen a grad school application (especially for PhD programs!) [3]. So if you're at all considering going to grad school, getting involved with research is a very good thing to do. If you're not sure about grad school (like most people are), then it's still useful to get some research experience because it leaves that door open for you to decide later. It's much better to have the experience and decide not to apply to grad school than to not have the experience and want to apply. Additionally, as mentioned above, doing undergrad research will essentially simulate what a PhD program program will be like, which will help you decide whether or not you'd even like to apply to grad school in the first place. 

1. **You'll get to form strong relationships with a Professor**

    Professors are generally extremely cool, intelligent and experienced people who can (and want to) be incredible mentors to your career and life. They can give you valuable advice on everything from what classes to take to how to think about what kind of person you want to be. They can also open doors to cool opportunities (internships, grad-schools, etc.) with strong letters of recommendation and/or connecting you with people they know in academia and industry (and most CS Professors know *a lot* of interesting people!). In my own case, my undergrad research advisors are the best mentors I've had so far, and their advice changed my life and career trajectory; so I'd definitely *highly* recommend getting to know your Professors better. While you *could* do this through other avenues (TA'ing, going to a lot of their office hours, etc.) there's nothing as direct as doing research with them.

1. **You'll strengthen job/internship applications**

    Research projects - especially ones that are  relevant to roles you might be looking for - are appealing to potential employers. This is especially true if you're interested in research-adjacent roles (e.g. "research intern", "research engineer", "machine learning engineer", etc.). What's more, letters of recommendation from a professor can open up opportunities that might not be otherwise available (both the industry internships I did during my undergrad years were roles that I was only able to interview for on recommendation from a Professor). Having said this, I want to make clear that doing research is *rarely* the best use of your time if getting an industry internship/job is your primary goal; you'd be better off spending time on interview prep, side-projects, open-source contributions, etc.).

##  3. <a name='HowshouldIgetinvolved'></a>How should I get involved?
Hopefully at this point, you're considering trying out this research thing for yourself. So how exactly do you go about getting involved? Fortunately, there are a lot of great existing articles and resources on this. Some posts I've found particularly helpful are [this one from Cornell CS](https://medium.com/@researchconnectcu/cornell-cs-research-readme-381206eaabcb) and [this one from UNC Chapel Hill](https://cs.unc.edu/academics/undergraduate/how-to-undergraduate-research/). While these articles include some school-specific information, the general process is roughly the same at any institution. Spend some time searching for information specific to your department and the various labs within it (if you happen to be a Brown student, check out [this website](http://ur.cs.brown.edu/) and get in touch with the [MURA's](http://ur.cs.brown.edu/about/)!). If you can't seem to find much, then don't hesitate to talk to/email a Professor directly. Overall, taking initiative and showing enthusiasm for research opportunities can go a long way towards getting them!

Now, what should you do if there aren't that many relevant/exciting research opportunities within your school's CS department? If you're a citizen or permanent resident of the US, the NSF funds a "Research Experiences for Undergraduates" (REU) program with a bunch of exciting, paid research opportunities in a variety of different topics all across the world. You can find a list of these opportunities [here](https://www.nsf.gov/crssprgm/reu/list_result.jsp?unitid=5049). If this doesn't apply to you, or none of these opportunities stand out to you, then I'd encourage you to try to find research opportunities through industry internships (e.g. an [AI Residency Program](https://github.com/dangkhoasdc/awesome-ai-residency)), virtual mentorships from established researchers (e.g. [this one](https://blog.evjang.com/2020/06/free-office-hours-for-non-traditional.html)) or try cold-emailing professors or graduate students at nearby institutions ([here](https://www.mtu.edu/biological/research/undergraduate/pdfs/mentor-email-guidelines.pdf) are some generally helpful guidelines for writing such an email that's likely to get a response). If none of that works and you still have the urge to do research, then go for it and forge your own path. Read papers, try to come up with an idea, and start working on it! This will certainly be difficult, but no one is stopping you. Plenty of people (like [Tim Dettmers](https://timdettmers.com/2020/03/10/how-to-pick-your-grad-school/) or [Andreas Madsen](https://andreas-madsen.medium.com/becoming-an-independent-researcher-and-getting-published-in-iclr-with-spotlight-c93ef0b39b8b)) have successfully pursued "independent" research ([there's even an organization that helps foster this](https://mlcollective.org/)!). Again, I'd highly recommend taking initiative and showing enthusiasm: these are often the most important traits of a researcher and will significantly improve your chances of independent success or getting noticed.

##  4. <a name='Sometipsandadvice'></a>Some tips and advice
Now that we've covered the basics of what, why, and how, let me share some tips and advice that I've gotten over the years and wish I'd known when I started as a bright-eyed bushy-tailed undergrad researcher.

###  4.1. <a name='SomeDosandDontsofUndergradResearch'></a>Some Do's and Dont's of Undergrad Research
**Do's**
1. **Work towards a paper**

    If you had to sum up a software engineer's job in 3 words, "produce good code" would be a fairly apt description. If you had to do a similar thing for a researcher "produce good papers" would be it. Papers are the bread-and-butter of a researcher; pretty much all research projects aim to publish a paper in some capacity. Given this, if you want to get a true taste of what it's like to be a researcher, you should work towards publishing a paper. Not doing so would be like trying to experience what it's like to be a software engineer without working on a significant software project! By working towards a paper, you'll not only get a real sampling of what it'd be like to be a professional researcher, but you'll also have something tangible to show for it. 

    Now, to be clear, I'm not suggesting that you should only work on projects where you'll be first-author on a paper that's published at one of the top conferences or journals. I'm also not suggesting that you don't work on projects whose outcome might *not* be a traditional conference or journal paper - producing things like technical reports, posters or even deep-dive blog posts can often be just as useful of a learning experience as a traditional paper. It also takes time to practice and develop the various skills that go into good research, and it's a good idea to start out by doing a small, unpublished starter project, or working on an existing codebase, or by joining a project led by someone more experienced. However, if you want to experience what research is *really* like (which you should!), you need to be part of at least one project that eventually publishes a paper (or something with similar qualities like a technical report, deep-dive blog post, poster, etc.). 
    
    If you work on any other project (a code release for an existing paper, setting up infrastructure for experimentation, etc.), even if it's within a research lab, be well-aware that what you're experiencing isn't fully representative of the research process, and that the fact that you enjoy this project doesn't mean you'd enjoy being a professional researcher.

1. **Ask for help and advice frequently**

    Before I actually got involved with research, I imagined that researchers generally sat alone thinking about problems for long periods of time before having a "eureka" moment and writing some crazy important paper (a la Isaac Newton). I chuckled when I wrote that last sentence because this is actually pretty far from the truth: most research is extremely collaborative (notice how almost every paper you'll read has more than one author). Sure, it's sometimes useful to sit and think about a problem alone, but there's no point banging your head against it repeatedly when you're stuck: it's not useful to you or anyone you might be working with. 

    Don't be afraid to ask for help and collaborate with others when you think they can help you get unstuck; discussing problems and brainstorming ideas can be one of the most enjoyable parts of research (it certainly is for me!).

1. **Set reasonable expectations with your advisor**

    Most undergrads feel the need to impress their advisor, especially when they first start out with research. As a result, it can be tempting to propose ridiculously hard-to-meet deadlines. Avoid doing this; the clearer you are about your time commitments, the easier it'll be for your advisor to set expectations, and the more likely you'll be to see your project through to completion instead of burning out and bowing out. Also, in general, it's better to underpromise and overdeliver on deadlines than the other way around.

**Dont's**
1. **Flake**

    This is unfortunately one of the most-common thing that happens with undergraduate researchers (and why some labs are hesitant to take any at all). Abandoning a research project suddenly and calling it quits is not only a letdown to the researchers you're working with, but it also prevents you from getting a full taste of research and having something to show for it. Of course, if you truly can't handle the workload, or actively hate what you're working on, or aren't getting enough time, help or guidance from the people you're working with, then it can be a good idea to call it quits. However, undergrads often flake for simpler, more benign reasons: getting overwhelmed with other commitments and/or feeling stuck and not asking for help. 

    Overall, I'd recommend that you stick with a research project to see it through, even if (more likely *when*) it gets difficult, annoying or uninteresting, because some of the best parts come *after* the worst ones. Also, sticking with a project will give you a true taste for the entire research process, and leave you with something to show for all your efforts at the end.

1. **Feel too bad about not making much progress** 

    Research is *hard*, and this is especially true when you're just starting out. One of the things that makes it so hard is that research progress if often highly non-linear. It's possible (and somewhat common) to make very little progress on a project despite putting in effort. Projects also fail entirely from time to time. In this way, research is very much unlike course work or personal projects, and often much more frustrating for undergrads used to relatively linear payouts for work put in. 

    However, it's important to realize this *isn't* just happening to you: all researchers get stuck on problems and feel frustrated [4], but it *does* get better with time and experience. As an undergrad, you can try to mitigate the frustration that comes from a lack-of-progress by leaning on your mentors and collaborators more, focusing on what you can control (the time and effort you're putting in), and even potentially joining multiple projects so that you can switch gears to another project whenever you're feeling stuck. However, it's also important to pay attention to your feelings: if you're finding that you *really* don't like the frustration of being stuck, and would much prefer to make more linear progress on your work, then that's a strong and useful signal that you probably won't be very happy as a researcher.

1. **Assume a Professor's research is just like that course you took with them**

    While Professors generally teach classes that are at least tangentially related to their research, this is not necessarily the case. Also, even if their research does cover the exact topic from a class you took with them, there is usually a big difference between learning material/doing class assignments and doing research. Try to do some of your own research on a lab's recent work before trying to join it: skim some recent papers and maybe even go to a lab meeting (you'll usually be welcome!). If you'd like to get a taste for the research process, see if your Professor teaches a seminar or graduate class related to their research and see if you can enroll in it.


###  4.2. <a name='SomeImportantThingstoKeepinMind'></a>Some Important Things to Keep in Mind
- **It's okay to feel like you don't know what you're doing**

    It's easy to feel lost and overwhelmed when trying to do research, especially as an undergrad. This is okay. In fact, it's normal and believe it or not, most senior researchers feel like they don't know what they're doing quite often. This isn't too surprising when you really think about it: research *literally* involves straying beyond the boundaries of the field into the unknown. If you know exactly what you're doing all the time, you're probably not exploring far enough. One of the most significant and sobering things my undergrad research advisor told me is that the feeling of not knowing what you're doing doesn't really ever go away, even as a Professor. The best researchers learn to accept this and operate well despite not truly knowing how exactly things will pan out.

- **You're probably not bothering/annoying them**
    
    Professors and grad students are often incredibly busy juggling a jaw-dropping number of tasks. As a result, it's easy to feel like emailing them or asking for a meeting when you're stuck/need help is bothersome and annoying. It's usually not - especially if you're blocked/stuck on something where a quick email/meeting could save you hours (and a significant amount of headache). That being said, it's probably not a good idea to email out a cry for help for every problem you encounter without first trying to solve it. 
    
    In general, a good rule of thumb is that you should have exhausted all the *reasonable* options you can think of for solving whatever problem you're confronted with before asking for help. This will not only often help you resolve most problems/develop a better problem-solving intuition, but also will enable you to ask much better questions by describing what you've already done and your thoughts on why they didn't work. An email saying "Stuck on `problem x` and have no clue what's going on pls HALP!" is much less productive than one saying "I've tried solution attempt `a, b, and c` to solve problem `x` and this is what happened in each of the cases, any thoughts on how to proceed?". If you're looking for more detailed guidelines on when and how to ask good questions, check out this [StackOverflow post](https://stackoverflow.com/help/how-to-ask).

- **You're a valuable asset to your research group**

    As an undergrad, it's easy to look at the incredibly smart and productive grad students and Professor(s) in your group and feel like your contributions aren't particularly important or valuable to the group. While you might not be producing as much as a grad student or Professor, that certainly does not mean you aren't valuable (if that were the case, then the group wouldn't have hired you and wouldn't be interested in keeping you around!). In fact, aside from their direct contributions to projects, undergrads can prove valuable in some non-obvious ways. For instance, having an interested undergrad ask basic questions about a project or paper can often force people who've been working on the project for a while to rethink some fundamental assumptions and ultimately come up with better ideas (I've seen this happen; never hesitate to ask basic questions!). Additionally, working with undergrads helps grad students/post-docs acquire valuable collaboration and mentorship skills, which are part of the reason they chose their jobs in the first place. All in all, your work and presence as an undergrad are often much more valuable than you realize.

- **Being an undergrad and doing research is hard: it's okay to ask for extensions/take some time off.** 

    Being an undergrad means having a significant course load *and* a bunch of external commitments to clubs, part-time jobs, etc. Research will always have to be done on top of all this, which is hard to say the least. There will be some weeks when all your commitments overwhelm you and make it hard to get much research work done. This is fine. Grad students and Professors understand this (all of them were once undergrads and many of them likely know what it's like to be in your shoes). And more often than not, they're more than willing to accommodate you if you need to push back some deadlines, etc. That being said, it's useful to try to plan in advance, set reasonable deadlines and expectations for how much time you can commit to research in any given semester, and avoid over-promising.

- **Persistence goes a long way**

    Research is very much a skill and, like all other skills, takes time and practice to develop. Research also has a long learning curve: it's difficult to 'teach' someone how to do good research with a couple lectures. Rather, ideas, concepts and a [good taste for problems](http://joschu.net/blog/opinionated-guide-ml-research.html) tend to sink in with experience over time. So don't be surprised if you feel like you're not getting much better at research in the beginning. If you choose to stay at it, you'll find yourself improving slowly and rather unnoticeably to you, till some day you give a talk or mentor new undergrads yourself and realize how far you've come.

---

That's it! Hopefully that's enough to give you an idea of what undergrad research is, why you might want to get involved and how to actually do it, plus some tips and advice that I wish I'd been given when I started out. I hope some of this has been informative, and even convinced you to give undergrad research a try. 

Good luck - I can't wait to hear about what you build :).

---


[1] As an example, the only substantive guide to undergrad research I've been able to find online is [this Reddit AMA](https://www.reddit.com/r/cscareerquestions/comments/cv8o3t/iama_cs_researcher_let_me_tell_you_about/)

[2] If you're working on a starter project and get stuck, don't hesitate to reach out to a lab member to ask for help! Contrary to what it might seem like, asking for help will usually be taken as a positive sign that you're really interested in the work and excited to learn. Far too many undergrads give up after getting stuck on a starter project without even asking for help - so avoid this mistake if you can.

[3] See [here](https://timdettmers.com/2018/11/26/phd-applications/), [here](https://da-data.blogspot.com/2015/03/reflecting-on-cs-graduate-admissions.html), and [here](http://www.cs.cmu.edu/~harchol/gradschooltalk.pdf).

[4] [There's a famous story](https://www.bloomberg.com/news/videos/2017-12-01/the-godfather-of-ai-was-almost-a-carpenter-video) about how Geoffrey Hinton - a "godfather" of AI, inventor of Deep Learning and giant in the field of CS as a whole - got so frustrated with not being able to come to a satisfying understanding of how the brain works as an undergrad that he gave up on science and research entirely to become a carpenter for a year.

Thanks to [Dylan Sam](https://dsam99.github.io/), [Roma Patel](http://cs.brown.edu/people/rpatel59/), and [Anna Wei](https://qiuhongannawei.me/) for providing comments and feedback on a draft of this post.