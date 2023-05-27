---
title: "Research"
layout: splash
permalink: /research/
---

Welcome to my Research page! I'm currently a 2nd Year Ph.D. student with the [LIS Group](https://lis.csail.mit.edu/) within [MIT CSAIL](https://www.csail.mit.edu/). I'm officially advised by [Leslie Kaelbling](https://www.csail.mit.edu/person/leslie-kaelbling) and [Tomás Lozano-Pérez](https://people.csail.mit.edu/tlp/), though I frequently collaborate with [Dylan Hadfield-Menell](https://scholar.google.com/citations?user=4mVPFQ8AAAAJ&hl=en), [Josh Tenenbaum](http://web.mit.edu/cocosci/josh.html), and many other wonderful people within CSAIL's [Embodied Intelligence Initiative](https://ei.csail.mit.edu/). I also spend time at the [Boston Dynamics AI Institute](https://theaiinstitute.com/) where I primarily work with [Jennifer Barry](https://www.linkedin.com/in/jennifer-barry-742a0799/). I'm extremely grateful for support from the [NSF Graduate Research Fellowship](https://engineering.brown.edu/news/2021-03-29/nsf-graduate-research-award).
{: style="text-align: center;font-size:110%;padding-top:40px"}

[Resume](/misc_files/Nishanth_Resume.pdf) \| [CV](/misc_files/Nishanth_CV.pdf) \| [Google Scholar](https://scholar.google.com/citations?user=FE512o4AAAAJ&hl=en) \| [Bio](/misc_files/njk-bio.txt) \| [GitHub](https://github.com/NishanthJKumar) \| [Twitter](https://twitter.com/nishanthkumar23)
{: style="text-align: center;font-size: 100%"}

## Research Areas
I'm broadly interested in enabling robots to operate robustly in long-horizon, multi-task settings so that they can accomplish tasks like multi-object manipulation, cooking, or even performing household chores. To this end, I'm interested in combining classical AI planning and reasoning approaches with modern machine learning techniques. My research draws on ideas from reinforcement learning, task and motion planning (TAMP), deep learning, and neurosymbolic AI.


## Publications
### Conference Papers
<table style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
    <tbody>
      <tr bgcolor="#ffffd0">
        <td style="padding:20px;width:25%;vertical-align:middle">
          <div>
            <img src='/images/paper-images/predicators-image.png' width="160">
          </div>
        </td>
        <td style="padding:20px;width:75%;vertical-align:middle">
          <p style="font-family:'Lato',Verdana,Helvetica,sans-serif; font-size:14px;font-weight:700">
          Predicate Invention for Bilevel Planning
          </p>
          <a href="https://web.mit.edu/tslvr/www/">Tom Silver*</a>,
          <a href="https://rohanchitnis.com/">Rohan Chitnis*</a>,
          <strong>Nishanth Kumar</strong>,
          <a href="https://wmcclinton.github.io/">Willie McClinton</a>,
          <a href="https://people.csail.mit.edu/tlp/">Tomás Lozano-Pérez</a>,
          <a href="http://people.csail.mit.edu/lpk/">Leslie Pack Kaelbling</a>,
          <a href="http://web.mit.edu/cocosci/josh.html">Joshua Tenenbaum</a>
          <br>
          <em>AAAI</em>, 2023 <p style="color:red;display:inline;">(Oral)</p>. Also appeared at RLDM, 2022 <p style="color:red;display:inline;">(Spotlight Talk)</p>.
          <br>
          <a href="https://arxiv.org/abs/2203.09634">arxiv</a>
          /
          <a href="https://github.com/Learning-and-Intelligent-Systems/predicators/releases/tag/march-2022-experiments">code</a> 
          <br>
          <p>
          Introduces a new, program-synthesis inspired approach for learning neuro-symbolic relational state and action abstractions (predicates and operators) from demonstrations. The abstractions are explicitly optimized for effective and efficient bilevel planning.
          <br>
          [* denotes equal contribution]
          </p>
        </td>
      </tr>
    </tbody>
</table>

<table style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
        <tbody>
          <!-- <tr bgcolor="#ffffd0"> -->
          <tr>
            <td style="padding:20px;width:25%;vertical-align:middle">
              <div>
                <img src='/images/paper-images/active-learning.png' width="160">
              </div>
            </td>
            <td style="padding:20px;width:75%;vertical-align:middle">
              <p style="font-family:'Lato',Verdana,Helvetica,sans-serif; font-size:14px;font-weight:700">
              Just Label What You Need: Fine-Grained Active Selection for Perception and Prediction through Partially Labeled Scenes
              </p>
              <strong>Nishanth Kumar*</strong>,
              <a href="http://www.seansegal.com/">Sean Segal*</a>,
              <a href="http://www.cs.toronto.edu/~sergio/">Sergio Casas</a>,
              <a href="https://www.cs.toronto.edu/~mren/">Mengye Ren</a>,
              <a href="http://www.cs.toronto.edu/~wangjk/">Jingkang Wang</a>,
              <a href="http://www.cs.toronto.edu/~urtasun/">Raquel Urtasun</a>
              <br>
							<em>Conference on Robot Learning (CoRL)</em> poster, 2021.
              <br>
              <a href="https://openreview.net/forum?id=xQ8rr3-zpiH">OpenReview</a>
              /
              <a href="https://arxiv.org/abs/2104.03956">arXiv</a>
              /
              <a href="https://openreview.net/attachment?id=xQ8rr3-zpiH&name=poster">poster</a>
              <br>
              <p>Introduces fine-grained active selection via partial labeling for efficient labeling for perception and prediction. <br>
              [* denotes equal contribution. Work was done while at Uber ATG]
              </p>
            </td>
          </tr>
        </tbody>
</table> 

<table style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
        <tbody>
          <tr>
            <td style="padding:20px;width:25%;vertical-align:middle">
              <div>
                <img src='/images/paper-images/aosm-paper.png' width="160">
              </div>
            </td>
            <td style="padding:20px;width:75%;vertical-align:middle">
              <p style="font-family:'Lato',Verdana,Helvetica,sans-serif; font-size:14px;font-weight:700">
              Building Plannable Representations with Mixed Reality
              </p>
              <a href="http://cs.brown.edu/people/er35/">Eric Rosen</a>,
              <strong>Nishanth Kumar</strong>,
              <a href="https://nakulgopalan.github.io/">Nakul Gopalan</a>,
              <a href="https://scholar.google.com/citations?user=k3Oh9D0AAAAJ&hl=en">Daniel Ullman</a>,
              <a href="https://cs.brown.edu/people/gdk/">George Konidaris</a>,
              <a href="https://cs.brown.edu/people/stellex/">Stefanie Tellex</a>
              <br>
							<em>IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)</em>, 2020.
              <br>
              <a href="https://h2r.cs.brown.edu/wp-content/uploads/rosen20.pdf">paper</a>
              /
              <a href="https://www.youtube.com/watch?v=dcFod--RMSI">video</a>
              <br>
              <p>Introduces Action-Oriented Semantic Maps (AOSM's) and a system to specify these with mixed reality, which robots can use to perform a wide-variety of household tasks.
              </p>
            </td>
          </tr>
        </tbody>
</table> 

<table style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
        <tbody>
          <tr>
            <td style="padding:20px;width:25%;vertical-align:middle">
              <div>
                <img src='/images/paper-images/oopomcp.png' width="160">
              </div>
            </td>
            <td style="padding:20px;width:75%;vertical-align:middle">
              <p style="font-family:'Lato',Verdana,Helvetica,sans-serif; font-size:14px;font-weight:700">
              Multi-Object Search using Object-Oriented POMDPs
              </p>
              <a href="https://scholar.google.com/citations?user=5v2t5L0AAAAJ&hl=en">Arthur Wandzel</a>,
              <a href="https://sites.google.com/view/robots-oh/yoonseon-oh">Yoonseon Oh</a>,
              <a href="https://www.linkedin.com/in/michael-fishman-9a0a11160/">Michael Fishman</a>,
              <strong>Nishanth Kumar</strong>,
              <a href="https://www.khoury.northeastern.edu/people/lawson-wong/">Lawson L.S Wong</a>,
              <a href="https://cs.brown.edu/people/stellex/">Stefanie Tellex</a>
              <br>
							<em>IEEE International Conference on Robotics and Automation (ICRA)</em>, 2019.
              <br>
              <a href="https://h2r.cs.brown.edu/wp-content/uploads/wandzel19.pdf">paper</a>
              /
              <a href="https://www.youtube.com/watch?v=ssmez0rjF1Y">video</a>
              <br>
              <p>Introduces the Object-Oriented Partially Observable Monte-Carlo Planning (OO-POMCP) algorithm for efficiently solving Object-Oriented Partially Observable Markov Decision Processes (OO-POMDPs) and shows how this can enable a robot to efficiently find multiple objects in a home environment.
              </p>
            </td>
          </tr>
        </tbody>
</table>


### Workshop Papers and Extended Abstracts
<table style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
        <tbody>
          <tr>
            <td style="padding:20px;width:25%;vertical-align:middle">
              <div>
                <img src='/images/paper-images/PDDL-with-LLMs.png' width="160">
              </div>
            </td>
            <td style="padding:20px;width:75%;vertical-align:middle">
              <p style="font-family:'Lato',Verdana,Helvetica,sans-serif; font-size:14px;font-weight:700">
              PDDL Planning with Pretrained Large Language Models
              </p>
              <a href="https://web.mit.edu/tslvr/www/">Tom Silver*</a>,
              Varun Hariprasad*,
              <a href="https://www.linkedin.com/in/reece-shuttleworth-8ab69a220/">Reece Shuttleworth*</a>,
              <strong>Nishanth Kumar*</strong>,
              <a href="https://people.csail.mit.edu/tlp/">Tomás Lozano-Pérez</a>,
              <a href="http://people.csail.mit.edu/lpk/">Leslie Pack Kaelbling</a>,          
              <br>
							<em>NeurIPS FMDM Workshop,</em> 2022.
              <br>
              <a href="https://openreview.net/forum?id=1QMMUB4zfl">OpenReview</a>
              <br>
              <p>
              Investigates the extent to which pretrained language models can solve PDDL planning problems on their own, or be used to guide a planner.
              <br>
              [* denotes equal contribution]
              </p>
            </td>
          </tr>
        </tbody>
</table>

<table style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
        <tbody>
          <tr>
            <td style="padding:20px;width:25%;vertical-align:middle">
              <div>
                <img src='/images/paper-images/taxi-scoping.png' width="160">
              </div>
            </td>
            <td style="padding:20px;width:75%;vertical-align:middle">
              <p style="font-family:'Lato',Verdana,Helvetica,sans-serif; font-size:14px;font-weight:700">
              Task Scoping for Efficient Planning in Open Worlds
              </p>
              <strong>Nishanth Kumar*</strong>,
              <a href="https://www.linkedin.com/in/michael-fishman-9a0a11160/">Michael Fishman*</a>,
              <a href="https://scholar.google.com/citations?user=1HIu1uQAAAAJ&hl=en">Natasha Danas</a>,
              <a href="https://www.littmania.com/">Michael Littman</a>,
              <a href="https://cs.brown.edu/people/stellex/">Stefanie Tellex</a>,
              <a href="https://cs.brown.edu/people/gdk/">George Konidaris</a>              
              <br>
							<em>AAAI Conference on Artificial Intelligence, Student Workshop,</em> 2020.
              <br>
              <a href="https://ojs.aaai.org/index.php/AAAI/article/view/7195">paper</a>
              <br>
              <p>
              Introduces high-level ideas for how large Markov Decision Processes (MPDs) might be efficiently pruned to include only states and actions relevant to a particular reward function. This paper is subsumed by our arxiv preprint on task scoping.
              <br>
              [* denotes equal contribution]
              </p>
            </td>
          </tr>
        </tbody>
</table>

<table style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
        <tbody>
          <tr>
            <td style="padding:20px;width:25%;vertical-align:middle">
              <div>
                <img src='/images/paper-images/mr-pick-place.png' width="160">
              </div>
            </td>
            <td style="padding:20px;width:75%;vertical-align:middle">
              <p style="font-family:'Lato',Verdana,Helvetica,sans-serif; font-size:14px;font-weight:700">
              Knowledge Acquisition for Robots through Mixed Reality Head-Mounted Displays
              </p>
              <strong>Nishanth Kumar*</strong>,
              <a href="http://cs.brown.edu/people/er35/">Eric Rosen*</a>,              
              <a href="https://cs.brown.edu/people/stellex/">Stefanie Tellex</a>
              <br>
							<em>The Second International Workshop on Virtual, Augmented and Mixed Reality for Human Robot Interaction</em>, 2019.
              <br>
              <a href="https://ojs.aaai.org/index.php/AAAI/article/view/7195">paper</a>
              <br>
              <p>
              Sketches high level ideas for how a mixed reality system might enable users to specify information for a robot to perform pick-place and other household tasks. This work is subsumed by our AOSM work.
              <br>
              [* denotes equal contribution]
              </p>
            </td>
          </tr>
        </tbody>
</table>

### Preprints
<table style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
    <tbody>
      <tr bgcolor="#ffffd0">
        <td style="padding:20px;width:25%;vertical-align:middle">
          <div>
            <img src='/images/paper-images/ignore_effects.png' width="160">
          </div>
        </td>
        <td style="padding:20px;width:75%;vertical-align:middle">
          <p style="font-family:'Lato',Verdana,Helvetica,sans-serif; font-size:14px;font-weight:700">
          Overcoming the Pitfalls of Prediction Error in Operator Learning for Bilevel Planning
          </p>
          <strong>Nishanth Kumar*</strong>,
          <a href="https://wmcclinton.github.io/">Willie McClinton*</a>,
          <a href="https://rohanchitnis.com/">Rohan Chitnis</a>,
          <a href="https://web.mit.edu/tslvr/www/">Tom Silver</a>,
          <a href="https://people.csail.mit.edu/tlp/">Tomás Lozano-Pérez</a>,
          <a href="http://people.csail.mit.edu/lpk/">Leslie Pack Kaelbling</a>.
          <br>
          <em>arXiv</em>, 2023.
          <br>
          <a href="https://arxiv.org/pdf/2208.07737.pdf">paper</a>
          /
          <a href="http://nishanthjkumar.com/tamp-operator-learning.github.io/">website</a>
          <br>
          <p>
          Shows that existing methods of learning operators for TAMP/bilevel planning struggle in complex environments with large numbers of objects. Introduces a novel operator learning approach based on local search that encourages operators to only model changes *necessary* for high-level search.
          <br>
          [* denotes equal contribution]
          </p>
        </td>
      </tr>
    </tbody>
</table>

<table style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
    <tbody>
      <!-- <tr bgcolor="#ffffd0"> -->
      <tr>
        <td style="padding:20px;width:25%;vertical-align:middle">
          <div>
            <img src='/images/paper-images/task-scoping-image.png' width="160">
          </div>
        </td>
        <td style="padding:20px;width:75%;vertical-align:middle">
          <p style="font-family:'Lato',Verdana,Helvetica,sans-serif; font-size:14px;font-weight:700">
          Task Scoping: Generating Task-Specific Abstractions for Planning in Open-Scope Models
          </p>
          <a href="https://www.linkedin.com/in/michael-fishman-9a0a11160/">Michael Fishman*</a>,
          <strong>Nishanth Kumar*</strong>,
          <a href="https://camallen.net/">Cameron Allen</a>,
          <a href="https://scholar.google.com/citations?user=1HIu1uQAAAAJ&hl=en">Natasha Danas</a>,
          <a href="https://www.littmania.com/">Michael Littman</a>,
          <a href="https://cs.brown.edu/people/stellex/">Stefanie Tellex</a>,
          <a href="https://cs.brown.edu/people/gdk/">George Konidaris</a>
          <br>
          <em>arXiv</em>, 2023.
          <br>
          <a href="https://arxiv.org/pdf/2010.08869">arxiv</a>
          <br>
          <p>
          Introduces a method for how large classical planning problems can be efficiently pruned to exclude states and actions that are irrelevant to a particular goal so that agents can solve very large, 'open-scope' domains that are capable of supporting multiple goals.
          <br>
          [* denotes equal contribution]
          </p>
        </td>
      </tr>
    </tbody>
</table>

<table style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
    <tbody>
      <tr>
      <!-- <tr bgcolor="#ffffd0"> -->
        <td style="padding:20px;width:25%;vertical-align:middle">
          <div>
            <img src='/images/paper-images/pgmax.png' width="160">
          </div>
        </td>
        <td style="padding:20px;width:75%;vertical-align:middle">
          <p style="font-family:'Lato',Verdana,Helvetica,sans-serif; font-size:14px;font-weight:700">
          PGMax: Factor Graphs for Discrete Probabilistic Graphical Models and Loopy Belief Propagation in JAX
          </p>
          <a href="https://stanniszhou.github.io/">Guangyao Zhou*</a>,
          <strong>Nishanth Kumar*</strong>,
          <a href="https://www.linkedin.com/in/miguel-l%C3%A1zaro-gredilla-133759a">Miguel Lázaro-Gredilla</a>,
          <a href="https://scholar.google.com/citations?user=8RYloKYAAAAJ&hl=fr">Shrinu Kushagra</a>,
          <a href="https://www.linkedin.com/in/dileep-george/">Dileep George</a>
          <br>
          <em>arXiv</em>, 2022.
          <br>
          <a href="https://arxiv.org/abs/2202.04110">arxiv</a>
          /
          <a href="https://www.vicarious.com/posts/pgmax-factor-graphs-for-discrete-probabilistic-graphical-models-and-loopy-belief-propagation-in-jax/">blog post</a>
          /
          <a href="https://github.com/vicariousinc/PGMax">code</a>
          <br>
          <p>
          Introduces a new JAX-based framework that aims to make it easy to build and run inference on probabilistic graphical models (PGM's).
          <br>
          [* denotes equal contribution]
          </p>
        </td>
      </tr>
    </tbody>
</table>

<table style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
    <tbody>
      <tr>
        <td style="padding:20px;width:25%;vertical-align:middle">
          <div>
            <img src='/images/paper-images/parameterized-bc.png' width="160">
          </div>
        </td>
        <td style="padding:20px;width:75%;vertical-align:middle">
          <p style="font-family:'Lato',Verdana,Helvetica,sans-serif; font-size:14px;font-weight:700">
          Learning Deep Parameterized Skills from Demonstration for Re-targetable Visuomotor Control
          </p>
          <strong>Nishanth Kumar*</strong>,
          <a href="https://jdchang1.github.io/">Jonathan Chang*</a>,
          <a href="https://scholar.google.com/citations?user=JsWiJPcAAAAJ&hl=en">Sean Hastings</a>,
          <a href="https://skylion007.github.io/">Aaron Gokaslan</a>,
          <a href="https://www.merl.com/people/romeres">Diego Romeres</a>,
          <a href="https://www.merl.com/people/jha">Devesh Jha</a>,
          <a href="https://www.merl.com/people/nikovski">Daniel Nikovski</a>,
          <a href="https://cs.brown.edu/people/gdk/">George Konidaris</a>,
          <a href="https://cs.brown.edu/people/stellex/">Stefanie Tellex</a>
          <br>
          <em>arXiv</em>, 2020.
          <br>
          <a href="https://arxiv.org/abs/1910.10628">arxiv</a>
          <br>
          <p>
          Shows how the generalization capabilities of Behavior Cloning (BC) can be improved by learning a policy parameterized by some input that enables the agent to distinguish different goals (e.g. different buttons to press in a grid). Includes several exhaustive experiments in simulation and on two different robots.
          <br>
          [* denotes equal contribution. Work was done in collaboration with Mitsubishi Electric Research Laboratories]
          </p>
        </td>
      </tr>
    </tbody>
</table>


<!-- ### Theses and Misc. Publications
<table style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
    <tbody>
      <tr>
        <td style="padding:20px;width:25%;vertical-align:middle">
          <div>
            <img src='/images/paper-images/undergrad-thesis-image.png' width="160">
          </div>
        </td>
        <td style="padding:20px;width:75%;vertical-align:middle">
          <p style="font-family:'Lato',Verdana,Helvetica,sans-serif; font-size:14px;font-weight:700">
          You Only Need What’s in Scope: Generating Task-Specific Abstractions for Efficient AI Planning
          </p>
          <strong>Nishanth Kumar</strong>
          <br>
          <em>Undergraduate Honors Thesis, Brown University</em>, 2021.
          <br>
          <a href="/misc_files/Nishanth_Undergrad_Honors_Thesis.pdf">paper</a>
          <br>
          <p>
          Presents a detailed, thesis-style description of my work on Task Scoping. This work is largely subsumed by our 'Task Scoping' preprint.
          <br>
          </p>
        </td>
      </tr>
    </tbody>
</table> -->


## Invited Talks
- Inventing Plannable Abstractions from Demonstrations
<br/> [Brown Robotics Group](http://robotics.cs.brown.edu/). April 28, 2023.
- [Task Scoping: Generating Task-Specific Abstractions for Planning](https://drive.google.com/file/d/1eshvDUiBJJIbLqqRusdgCv5O7wK076f8/view)
<br/> [MIT LIS Group Meeting](https://lis.csail.mit.edu/). February 12, 2021.
- [Let's Talk about AI and Robotics](https://www.youtube.com/watch?v=OOAPni0ZUW8)
<br/> I was interviewed about my work, experiences and advice on research for an episode of the [interSTEM](https://www.youtube.com/channel/UC-qYS_P9NvSRoWYUsV2FmYQ) YouTube channel.
- [Action-Oriented Semantic Maps via Mixed Reality](http://awards.cs.brown.edu/2019/08/13/undergrad-nishanth-kumar-wins-best-plenary-presentation-ilurs/)
<br/> The Second Ivy-League Undergraduate Research Symposuim (ILURS). Best Plenary Presentation Award.
<br/> The University of Pennsylvania. April, 2019.
- [Building intelligent, collaborative robots](https://www.youtube.com/watch?v=FziEfTBAwvg)
<br/> Machine Intelligence Conference 2019
<br/> Boston University. September 2019.


## Mentorship
I love mentoring students and junior researchers with interests related to my own; I find that this not only leads to cool new papers and ideas, but also helps me become a better researcher and teacher!

### Mentees
*Current*
- [Kathryn Le](https://www.linkedin.com/in/kathrynle/) (mentoring jointly with [Willie McClinton](https://wmcclinton.github.io/))(IAP 2023 - Present): working on using Task and Motion Planning to solve tasks from the BEHAVIOR benchmark.


*Past*
- [Anirudh Valiveru](https://www.linkedin.com/in/avaliveru/)(IAP 2023): worked on leveraging Large Language Models (LLM's) for efficient exploration in relational environments; currently continuing undergrad at MIT and pursuing research with a different group.
- Varun Hariprasad (mentored jointly with [Tom Silver](https://web.mit.edu/tslvr/www/))(Summer 2022): high-school student at MIT via the [RSI program](https://www.cee.org/programs/research-science-institute); currently an undergrad at MIT.


## Awards
- [Qualcomm Innovation Fellowship Finalist](https://www.qualcomm.com/research/university-relations/innovation-fellowship/2022-north-america), 2022.
- [NSF GRFP Fellow](https://www.nsfgrfp.org/), 2021.
- [Berkeley Fellowship](https://grad.berkeley.edu/admissions/apply/fellowships-entering/) (declined), 2021.
- [Sigma Xi Inductee](https://www.sigmaxi.org/), 2021.
- [CRA Outstanding Undergraduate Research Award Finalist](http://awards.cs.brown.edu/2020/02/04/bayazit-galgana-kumar-and-safranchik-win-cra-outstanding-undergraduate-researcher-honorable-mentions/), 2021.
- [Tau Beta Pi Inductee](https://www.tbp.org/recruit/recruitHome.cfm), 2020.
- [Heidelberg Laureate](https://www.heidelberg-laureate-forum.org/), 2020.
- [Goldwater Scholarship](https://goldwater.scholarsapply.org/), 2020.
- [CRA Outstanding Undergraduate Research Award Honorable Mention](http://awards.cs.brown.edu/2020/02/04/bayazit-galgana-kumar-and-safranchik-win-cra-outstanding-undergraduate-researcher-honorable-mentions/), 2020.
- [Karen T. Romer Undergraduate Teaching and Research Award](https://www.brown.edu/academics/college/fellowships/utra/named), 2019.
- Best Plenary Presentation, The Second Ivy League Undergraduate Research Symposium, 2019.


## Industry Experience and Research Collaborations
- [The Boston Dynamics AI Institute](https://theaiinstitute.com/), Cambridge, USA. <br/>Working with [Jennifer Barry](https://www.linkedin.com/in/jennifer-barry-742a0799/) and many other wonderful researchers on enabling robots to solve real-world long-horizon tasks. Stay tuned for more on this!
- [Vicarious AI](https://www.vicarious.com/), Union City, USA. <br/>Worked with [Stannis Zhou](https://stanniszhou.github.io/), [Wolfgang Lehrach](https://scholar.google.com/citations?user=0vHt-XYAAAAJ&hl=en), and [Miguel Lázaro-Gredilla](https://www.linkedin.com/in/miguel-l%C3%A1zaro-gredilla-133759a) on developing [PGMax](https://pgmax.readthedocs.io/) - an open-source framework for ML with PGM's.
- [MERL](https://www.merl.com/research/), Cambridge, USA. <br/>Worked with [Diego Romeres](https://www.merl.com/people/romeres), [Devesh Jha](https://www.merl.com/people/jha) and [Daniel Nikovski](https://www.merl.com/people/nikovski) on furthering Learning from Demonstration for industrial robots.
- [Uber ATG Research](https://www.uber.com/us/en/atg/research-and-development/), Toronto, Canada.
<br/>Worked with [Sean Segal](https://www.uber.com/us/en/atg/research-and-development/researchers/sean-segal/), [Sergio Casas](https://www.uber.com/us/en/atg/research-and-development/researchers/sergio-casas/), [Wenyuan Zeng](https://www.uber.com/us/en/atg/research-and-development/researchers/wenyuan-zeng/), [Jingkang Wang](http://www.cs.toronto.edu/~wangjk/), [Mengye Ren](https://www.cs.toronto.edu/~mren/) and others on a project exploring Active Learning for Self-Driving Vehicles that lead to a paper (read it [here](https://arxiv.org/abs/2104.03956)!). I had the honor of being advised by [Prof. Raquel Urtasun](http://www.cs.toronto.edu/~urtasun/).


## Teaching
- **Head Teaching Assistant**, [CSCI 2951-F: Learning and Sequential Decision Making](http://cs.brown.edu/courses/cs2951f/)
<br/> Brown University, Fall 2019
- **Teaching Assistant**, [ENGN 0031: Honors Intro to Engineering](https://selfservice.brown.edu/ss/bwckctlg.p_disp_course_detail?cat_term_in=201610&subj_code_in=ENGN&crse_numb_in=0031)
<br/> Brown University School of Engineering, Fall 2018


## Selected Press Coverage
- [Engineering’s Dwyer, Dastin-van Rijn and Kumar Selected as NSF Graduate Research Fellows](https://engineering.brown.edu/news/2021-03-29/nsf-graduate-research-award)
- [Bawabe, Kumar, Sam, And Walke Receive CRA Outstanding Undergraduate Researcher Honors](https://cs.brown.edu/news/2021/01/13/bawabe-kumar-sam-walker-receive-cra-undergraduate-outstanding-researcher-honors/)
- [Nishanth Kumar named 2020 Barry M. Goldwater Scholar](https://engineering.brown.edu/news/2020-04-15/student-awards)
- [2020 Barry Goldwater Scholars Include Many Impressive Indian American Researchers ](https://www.indiawest.com/news/global_indian/2020-barry-goldwater-scholars-include-many-impressive-indian-american-researchers/article_38eaa6d6-88bd-11ea-842a-b3d73797025a.html)
- [Undergrad Nishanth Kumar Wins Best Plenary Presentation At ILURS](https://cs.brown.edu/news/2019/08/13/undergrad-nishanth-kumar-wins-best-plenary-presentation-ilurs/)
- [Bayazit, Galgana, Kumar, And Safranchik Win CRA Outstanding Undergraduate Researcher Honorable Mentions ](http://cs.brown.edu/news/2020/02/04/bayazit-galgana-kumar-and-safranchik-win-cra-outstanding-undergraduate-researcher-honorable-mentions/)
