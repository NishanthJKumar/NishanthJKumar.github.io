---
layout: default
title: Tackling Robotics with (V)LM Agents
date: 2026-09-20 00:00:01
excerpt_separator: <!--more-->
---

Recently, there have been some interesting new results showing that some of the latest large-scale VLMs (Vision-Language Models) can directly control robots to solve a variety of real-world tasks.
This has led to some claims and excitement that progress in robotics might happen as an emergent effect of scaling current multi-modal models instead of training different robotics-specific models.
As someone who's been doing research in the field for a few years now, I decided to dive into trying to understand these results and sort through the various potential implications and future directions.
<!--more-->

# What are the new results?
One [widely-circulated result](https://openai.robocurve.org/gpt-6-astra/) that also has a clear description of the testing protocol is from [Robocurve](https://bounty.robocurve.org/).
Researchers asked a few recent frontier VLMs (Claude Fable 5, Claude Fable 5.1, GPT-6 Astra) to perform some simple tasks (placing a block into a bowl, placing a puzzle piece into a groove) by controlling some [YAM arms](https://i2rt.com/).
The model takes the task description and camera images (and a history of previous images and actions if available) and outputs end-effector positions and orientation for each end-effector[^1].
Another related result is from the [RoboDojo team](https://robodojo-benchmark.com/report/gpt-6-astra-eval)[^robodojo], who ran GPT-6 Astra and GPT-5.5 through much the same kind of interface on their official simulation benchmark: 42 tasks, 50 episodes each, ranked against the 40 policies on their public leaderboard.
Here, Astra placed first, ahead of every learned policy on the board.
In both cases there is no other learned policy anywhere between the model and the robot.

The full reported results are worth looking at because they yield at least two useful trends:


| | Robocurve (real arms, 20 trials/task) | RoboDojo (simulation, 42 tasks × 50 episodes) |
|---|---|---|
| Overall | — | Astra 28.97, 1st of 43; best learned policy DM0.5 24.90, [π0.5](https://www.pi.website/blog/pi05)[^pi05] 11.41 |
| [Geometry and semantics](https://openai.robocurve.org/gpt-6-astra/)[^rcastra] | 95% Astra, 40% Fable 5.1, 5% Fable 5 | Generalization 33.36 and Open 34.36, both 1st (next best 23.54 and 6.50) |
| [Precision and contact](https://anthropic.robocurve.org/fable-5.1/)[^rcfable] | 10% Astra, 10% Fable 5.1, 0% Fable 5 | Precision 12.65 (4.0% SR) against 28.25 for the best VLA |
| Long-horizon | not evaluated | 21.45 (8.25% SR) against 44.12 for the best VLA |

<br>

The first thing is the trend line across model generations on the easy task(s): (e.g. 5% → 40% → 95% from Robocurve's results), over models released within about a year of each other, none of which was built with these specific robot arms in mind.
RoboDojo's results show that GPT-5.5 and Astra scored 1.13 and 28.97 respectively on the same set of tasks with the same harness, which suggests the improvement is directly due to capability improvements in the underlying model.
The second thing is that this trend does not seem to manifest on the harder task, where the newest and by far the strongest model does no better than one two generations older.
In Robocurve's testing of a contact-rich puzzle-piece insertion task, both models get the puzzle piece to the groove and then stall at the insertion — the part that requires reacting to contact rather than reasoning about geometry.
RoboDojo's per-axis scores show the same split, and show it more starkly: Astra places first overall only by dominating the generalization and open-instruction axes, and is beaten on precision (12.65 against 28.25) and long-horizon execution (21.45 against 44.12) by policies it otherwise outranks.
Its success rate on the precision tasks is 4%.[^6]

There have been a handful of more anecdotal results. [One X user](https://x.com/aryanmadhaverma/status/2096904943471145041?s=20) found that GPT-6 Astra is able to solve a range of tasks much more quickly (in terms of number of turns) and successfully than other recent frontier VLMs. However, they allowed the model to write functions and use helper tools (e.g. SAM for perception) instead of directly having it output end-effector commands. 
A number of other users demonstrated Astra performing a variety of other impressive real-world tasks (e.g. [painting the golden-gate bridge](https://x.com/cdngdev/status/2097339677128982873?s=20), [setting up a MuJoCo simulation and drawing a dove inside it](https://x.com/dimentary/status/2097141042214797801?s=20), [training a dexterous pen-spinning behavior](https://x.com/walterzhu8/status/2100212420840989112), [maneuvering complex interlocking puzzle pieces to be unstuck](https://x.com/qineng_wang/status/2099893504658866561?s=20), or [turning the knob on a real-world washing machine](https://x.com/ARXrobotics/status/2096328304794210604?s=20)).
However, these were largely demonstrations lacking thorough empirical results, comparisons to baselines, or clarity on the robot's exact I/O specification or prompting setup.


It is important for context to note that this is not the first time that VLMs or LLMs have been used to directly control robots.
There are a number of research works dating back to at least 2022 ([SayCan](https://say-can.github.io/)[^saycan], [Code as Policies](https://code-as-policies.github.io/)[^cap], [ProgPrompt](https://progprompt.github.io/)[^progprompt], [Inner Monologue](https://innermonologue.github.io/)[^innermono]) that explore this idea, and it remains an extremely active area of investigation (e.g. [this](https://research.nvidia.com/labs/gear/aspire/)[^aspire], or [this](https://capgym.github.io/)[^capx]).
Anthropic has even studied their latest models' capabilities on robotics tasks for the past year or so ([Project Fetch](https://www.anthropic.com/research/project-fetch-robot-dog)[^fetch], and more recently [an evaluation across quadrupeds, humanoids, and arms](https://www.anthropic.com/research/claude-plays-robotics)[^claudebots]).
What is noteworthy about these new results though is that the VLM is controlling the robot at a fairly low-level (end-effector targets) instead of via an intricate harness or a number of purpose-built tools, and that performance seems to have improved somewhat dramatically with recent improved model releases.

# Why are these results exciting?
[^2] Recent prevailing wisdom in robotics has been that robotics fundamentally requires capabilities that VLMs and LLMs cannot possess because of their [structure](https://www.youtube.com/watch?v=5PQtJxd4U0M), [training data](https://drfeifei.substack.com/p/from-words-to-worlds-spatial-intelligence)[^feifei], and/or training objectives.
The vast majority of recent state-of-the-art robotics demos (e.g. [this](https://www.pi.website/blog/pi07), or [this](https://generalistai.com/blog/towards-machines-with-a-thousand-hands)[^generalist], or [this](https://deepmind.google/blog/gemini-robotics-2-brings-whole-body-intelligence-to-robots/)[^gr2]) have come from training models on robotics data that are specialized to robotics.
However, these new results and demos referenced above illustrate that VLMs might possess sparks of embodied intelligence and robotic control despite not being explicitly trained for these things.
Moreover, it seems that newer generations of models are increasingly capable at these tasks.
Given this, perhaps scaling up existing models and training techniques will lead to models that can do ever more complex robotics tasks.
Thus, perhaps progress in robotics could happen as a by-product of large-scale foundation model training instead of requiring purpose-built robotics-specific models.

This is quite significant if true, and could have several important implications for current directions in the field. 
1. *Perhaps very little robotics data will be required*. Many recent results have been built atop extremely large-scale, often proprietary, data-collection efforts, and there is significant interest and effort being expended to obtain the largest useful robotics dataset ([RealOmni-Open](https://www.genrobot.ai/data/open-dataset)[^realomni], [Index](https://www.figure.ai/news/introducing-index)[^index]). However, if VLMs can learn to do well on robotics tasks from being trained (largely) on internet text, image, and coding data, then perhaps we don't need much robotics data and these data collection efforts  are unnecessary. 
1. *Transferring across embodiments might not be hard*. A frequent challenge for robotics models has been having the same model control a variety of different robot hardware form-factors. There is significant effort (e.g. described [here](https://deepmind.google/blog/scaling-up-learning-across-many-different-robot-types/)[^rtx], or [here](https://arxiv.org/abs/2510.03342)[^gr15]) required to train models to exhibit cross-embodiment generalization. If VLMs are able to solve robotics problems by writing programs or outputting controls specific to the problem and environment, then perhaps cross-embodiment generalization emerges without any significant or explicit attempts to train for it.
1. *Harnesses and tools might be invaluable*. A significant enabler for VLMs to be useful at coding has been good tooling and harnesses for developers (e.g. [Claude Code](https://www.claude.com/product/claude-code)). Indeed, research in leveraging such models for robotics (which has been ongoing for a number of years) has had similar findings ([Code as Policies](https://code-as-policies.github.io/), [CaP-X](https://capgym.github.io/)[^capx], [Waddle](https://www.waddlelabs.ai/research/introducing-waddle)[^waddle]): building the right tools and abstractions around the model might determine success or failure for end-to-end robot behavior.

## A related thought experiment
In some sense, building a general-purpose robot by training a model to be extremely good at programming and physical reasoning is not an altogether surprising strategy. 
We've known for a long time that it's possible to program any specific robot to do any specific task.
Assuming the environment is roughly static, and given enough time to think through the specific motions and measure out the relevant distances, a skilled robot programmer or [automation integrator](https://en.wikipedia.org/wiki/Automation_integrator) can write out a program that performs that specific task in that specific environment.
This is, in fact, most of what industrial robotics *is*: the integration, programming and commissioning work wrapped around an arm [routinely costs as much as the arm itself or more](https://standardbots.com/blog/how-much-do-robots-cost), and it has to be redone for every new robot and environment.
The trouble has been generalizing the program to produce the correct motion in new tasks and environments.

Imagine for a moment a future where a general-purpose robot is widely and easily available. From any customer's point of view, they can simply buy a robot, bring it to their environment of choice (e.g. a home, cafe, factory, etc.) and just ask it to start doing useful tasks. However, unbeknownst to the customer, each robot has a little (and invisible) elf that operates it. Whenever a human asks the robot to do something, the elf quickly runs around with a measuring tape and then writes out the precise program that generates the motions that accomplish that specific task in that environment.

This is an admittedly contrived setup, but I believe it is a useful lens for thinking about a particular approach to building such a general-purpose robot. Instead of trying to mimic/automate human brains (i.e., training a robotics-specific model) by having a model go directly from pixels to torques, we have a model that automates the *programmer* of robots, which is able to achieve tasks in a fully general way by writing hyper-specific programs for each task and environment it encounters.


# What's missing?
While current results and what they promise are certainly exciting, there are several important and substantial hurdles to be cleared before it is clearly practical to build and deply general-purpose robots by scaling VLMs.


### Thorough experimentation and (strong) evidence of generalization
The bulk of current evidence is either a demonstration with no quantitative results, or a set of preliminary quantitative results that lacks scale and statistical rigor (i.e., hundreds or more trials with results over several random seeeds). 
Moreover, many of them do not directly compare against established baselines from the research literature: [Code as Policies](https://code-as-policies.github.io/) or [more recent improvements](https://capgym.github.io/)[^capx] run on the same frontier models, recent VLAs like [π0.7](https://www.pi.website/blog/pi07)[^pi07], [MolmoAct2](https://arxiv.org/abs/2605.02881)[^molmo] or [GR00T N1.5](https://research.nvidia.com/labs/gear/gr00t-n1_5/)[^groot15], and recent WAMs like [DreamZero](https://arxiv.org/abs/2602.15922)[^dreamzero].
These are currently far from the type of thorough result that could be published in a robotics research paper that would be accepted at a top conference or journal.

Additionally, a significant part of the excitement around these results comes from the idea that the underlying models were trained on a very small amount (if any) of robotics data.
If in fact they were trained on large quantities of relevant robotics data (perhaps even on the tested embodiments) [^4], then these results do not really demonstrate that physical commonsense is coming as an emergent phenomenon of large-scale training on non-robotics data.
Even if they were not trained on robotics data, it is not guaranteed that performance on robotics tasks will continue to scale with training in any meaningful way (i.e., the [scaling laws](https://arxiv.org/pdf/2001.08361)[^kaplan] of these models on robotics tasks are entirely unclear).
Thorough experimentation and some insight into the training data for these latest frontier models would help determine the extent to which there is substantial evidence of [physical commonsense](https://generalistai.com/blog/physical-commonsense)[^commonsense] emerging from scaling these models.


### Task complexity
Current results demonstrate behavior on relatively simple, often short-horizon tasks with limited contact and physical interaction. 
However, a significant challenge in robotics is solving long-horizon, contact-rich tasks that require significant dexterity — [folding laundry out of a dryer](https://www.pi.website/blog/pi0)[^pi0], [assembling and packing deformable goods](https://generalistai.com/blog/towards-machines-with-a-thousand-hands), [making a bed or a coffee end-to-end](https://www.sunday.ai/blog/act-2-preview), or [cracking + beating eggs and using them to make an omelette](https://x.com/deepakpathak/status/2041939631860482211?s=20).
There is, as of yet, limited evidence that VLMs will be able to solve such tasks on robots directly[^3].
Indeed, VLMs - even augmented with tools and harnesses - might be simply incapable of solving certain tasks.
In the above-discussed thought experiment of the elf, it is possible that even an extremely competent elf would be unable to write the correct program without precisely measuring distances involved, or without a sense of touch, which could be impossible for a VLM operating just from robot cameras without any additional sensors.
However, several research works have demonstrated that such models are able to leverage tools or ML (e.g. [Eureka](https://eureka-research.github.io/)[^eureka], [DrEureka](https://eureka-research.github.io/dr-eureka/)[^dreureka]) to perform dexterous behavior, so perhaps this could be a feasible path forward.

<!-- ========== SUGGESTION (Claude, Sep 16) — S5 · NEW SUBSECTION. Your post currently has no reliability/safety failure mode, and this is the sharpest sim-doesn't-transfer evidence available. Order it wherever it fits best.
     Not your words. Rewrite, trim, or delete the whole block. ========== -->
### Reliability and safety on real hardware
There is much evidence that current models are not particularly safe or reliable at executing useful behavior on real robots.
Robodojo's results show that Astra solves their tasks with an average success rate of 28.97%, which is far from reliable completion.
Moroever, the RoboDojo team [had to hald their real-robot campaign for safety](https://robodojo-benchmark.com/report/gpt-6-astra-eval) after Astra repeatedly issued physically unreasonable or unsafe actions, including incidents that damaged hardware.
Robocurve [found that several recent VLMs will execute harmful and dangerous tasks](https://robocurve.org/roboharm/) on real hardware without refusal.
Model alignment [remains a challenging problems even for disembodied VLMs](https://openai.com/index/hugging-face-incident-and-the-road-ahead/): ensuring models will safely execute actions on hardware could be even more challenging.

<!-- ========== END SUGGESTION ========== -->
### Speed and cost in deployment
One issue noted as part of all the recent results is speed.
Frontier VLMs take on the order of seconds (at best) to produce a turn of output.
However, some tasks - such as walking even a quadruped robot - require commands to be output at a much higher frequency (e.g. [50 Hz](https://arxiv.org/pdf/2211.07638)[^legged]).
This control frequency is not feasible for modern large frontier VLMs [^5], and it is unclear that it will ever be.
A related issue is the current paradigm for querying large models: it may not be feasible for every robot to assume constant connection to a large centralized model server simply because wifi might have too much latency or too little bandwidth to be reliable.

Related to the issue of speed is that of cost.
Each of the trials in Robocurve's results cost between $0.94 and $2.69 in API calls for a single pick-and-place.
If frequency issues are resolved, then robots might be querying models at 50 Hz for commands, and any useful physical task might involve tens of millions of queries.
At current rates, the end-user cost of doing this is likely infeasible.

It is worth noting though that inference speeds and costs for VLMs are improving.
Robocurve notes that ["LLM token output speed increases by 2-7x per year"](https://x.com/chooi_jeq/status/2090453423682633891?s=20), and projects that VLMs could potentially control robots at the required control frequency by the end of this year, or by 2029.
Costs are falling on a [similar kind of curve](https://epoch.ai/data-insights/llm-inference-price-trends)[^epoch].
Both of these concerns could additionally be addressed by distilling large models into smaller ones that can be run locally.
ßHowever, it is unclear whether these trends will continue to hold in the coming months and years.


# Conclusion
Recent results and demonstrations show that frontier VLMs are surprisingly capable at solving tasks on robot hardware despite seemingly not having been trained to do so.
If these results and demonstrations are early sparks of physical intelligence emerging from large-scale foundation-model training, then progress in robotics might happen in a different and perhaps faster way than is currently projected.
However, there is a lot of additional work to be done before this path of scaling VLMs can feasibly be used to power and ship general-purpose robots.

While this post has generally contrasted scaling VLMs for robotics against training and developing robotics-specific models, there is no reason why these approaches cannot be combined.
Indeed, [several](https://www.anthropic.com/research/claude-plays-robotics) [recent results](https://anonymous-report-421.github.io/public-website/?lang=en&view=1) demonstrate that combining frontier VLMs with VLAs outperforms either approach individually.
Indeed, several robotics researchers argue that arming these models with models trained specifically for robots, as well as tools and techniques from classical robotics, is a promising path forward. [^8]

---

*Thanks to [Ryan Hoque](https://ryanhoque.github.io/), [Zachary Siegel](https://www.zacharysiegel.org/), and [Lucas Manuelli](https://lucasmanuelli.com/) for helpful comments on draft versions of this post, and to Chao Chen, [Jonathan Tompson](https://jonathantompson.github.io/), and [Sangbae Kim](https://meche.mit.edu/people/faculty/SANGBAE@MIT.EDU) for helpful discussion on the ideas it contains.*

## Citation

If you found this post useful in your own work or writing, please feel free to cite it. You can use the BibTeX below, or just link to the post directly.

<div class="cite-box">
  <button type="button" class="cite-copy" onclick="copyCite(this)" aria-label="Copy BibTeX citation to clipboard">Copy BibTeX</button>
  <pre class="cite-pre"><code id="cite-bibtex">@misc{kumar2026vlmagents,
  title        = {Tackling Robotics with (V)LM Agents},
  author       = {Kumar, Nishanth},
  year         = {2026},
  month        = {September},
  howpublished = {Blog post},
  url          = {https://nishanthjkumar.com/blog/2026/Tackling-Robotics-with-VLM-Agents/}
}</code></pre>
</div>

<style>
.cite-box{position:relative;margin:1.5em 0}
.cite-box .cite-pre{overflow-x:auto;padding:1em 1em 1em 1.1em;border:1px solid rgba(128,128,128,.35);border-radius:4px;font-size:.85em;line-height:1.5;margin:0}
.cite-box .cite-pre code{white-space:pre;background:none;padding:0;border:0;font-size:inherit}
.cite-copy{position:absolute;top:.6em;right:.6em;z-index:1;font:inherit;font-size:.78em;line-height:1;padding:.45em .7em;cursor:pointer;color:inherit;background:transparent;border:1px solid rgba(128,128,128,.5);border-radius:3px;opacity:.75;transition:opacity .15s ease}
.cite-copy:hover,.cite-copy:focus-visible{opacity:1}
.cite-copy[data-done="1"]{opacity:1;border-color:currentColor}
@media (prefers-reduced-motion:reduce){.cite-copy{transition:none}}
</style>

<script>
function copyCite(btn){
  var el = document.getElementById('cite-bibtex');
  if(!el) return;
  var text = el.innerText;
  var done = function(){
    var old = btn.textContent;
    btn.textContent = 'Copied';
    btn.setAttribute('data-done','1');
    setTimeout(function(){ btn.textContent = old; btn.removeAttribute('data-done'); }, 1800);
  };
  if(navigator.clipboard && navigator.clipboard.writeText){
    navigator.clipboard.writeText(text).then(done, function(){ fallback(text, done); });
  } else { fallback(text, done); }
  function fallback(t, cb){
    var ta = document.createElement('textarea');
    ta.value = t; ta.setAttribute('readonly','');
    ta.style.position = 'absolute'; ta.style.left = '-9999px';
    document.body.appendChild(ta); ta.select();
    try { document.execCommand('copy'); cb(); } catch(e) {}
    document.body.removeChild(ta);
  }
}
</script>


---

[^1]: This is a pretty low-level way to control a robot (though there are a few services - such as [Inverse Kinematics (IK)](https://en.wikipedia.org/wiki/Inverse_kinematics) - that still need to run between the model's outputs and the actual motors for this to be viable) and could translate to any other robot arm setup in theory.

[^2]: Prof. Phillip Isola at MIT articulated these points very well in a [recent blog post](https://web.mit.edu/phillipi/www/writing/robot-use-agents.html).

[^3]: Prof. Jitendra Malik raised exactly this point in a [recent tweet](https://x.com/JitendraMalikCV/status/2097173961264284039?s=20) in response to some of the above-mentioned results.

[^4]: There appears to be some [early evidence](https://x.com/DJiafei/status/2098681827703808480?s=20) that GPT-6 Astra may have been trained on open-source robotics data.

[^6]: New [results from robocurve](https://openai.robocurve.org/stationerybench/) show Astra outscoring the open-source [MolmoAct2](https://arxiv.org/abs/2605.02881) VLA on a few relatively complex manipulation tasks.

[^5]: The gap, from [Anthropic's own robotics evals](https://www.anthropic.com/research/claude-plays-robotics): current non-reasoning inference runs at **~0.2–0.4 Hz**, against the **~83 Hz** needed for real-time quadruped control — "roughly two orders of magnitude."

[^8]: See [this article](https://x.com/GeorgiaChal/article/2101335513558929868) from Georgia Chalvatzaki, and [this one](https://x.com/Ken_Goldberg/status/2100986412762087909) from Ken Goldberg. 

[^saycan]: Ahn, M. et al. (2022). [Do As I Can, Not As I Say: Grounding Language in Robotic Affordances](https://arxiv.org/abs/2204.01691).
[^cap]: Liang, J. et al. (2022). [Code as Policies: Language Model Programs for Embodied Control](https://arxiv.org/abs/2209.07753).
[^progprompt]: Singh, I. et al. (2022). [ProgPrompt: Generating Situated Robot Task Plans using Large Language Models](https://arxiv.org/abs/2209.11302).
[^innermono]: Huang, W. et al. (2022). [Inner Monologue: Embodied Reasoning through Planning with Language Models](https://arxiv.org/abs/2207.05608).
[^aspire]: Lu, R. et al. (2026). [ASPIRE: Agentic Skills Discovery for Robotics](https://arxiv.org/abs/2607.00272).
[^capx]: CaP-X (2026). [CaP-X: Benchmarking Coding Agents for Robot Manipulation](https://capgym.github.io/).
[^waddle]: Waddle Labs (2026). [Introducing Waddle: agents that control robots](https://www.waddlelabs.ai/research/introducing-waddle).
[^realomni]: GenRobot AI (2025). [10Kh RealOmni-Open Dataset](https://www.genrobot.ai/data/open-dataset).
[^rtx]: Google DeepMind (2023). [Scaling up learning across many different robot types](https://deepmind.google/blog/scaling-up-learning-across-many-different-robot-types/).
[^gr15]: Gemini Robotics Team (2025). [Gemini Robotics 1.5: Pushing the Frontier of Generalist Robots with Advanced Embodied Reasoning, Thinking, and Motion Transfer](https://arxiv.org/abs/2510.03342).
[^gr2]: Google DeepMind (2026). [Gemini Robotics 2 brings whole body intelligence to robots](https://deepmind.google/blog/gemini-robotics-2-brings-whole-body-intelligence-to-robots/).
[^pi0]: Black, K. et al. (2024). [π₀: A Vision-Language-Action Flow Model for General Robot Control](https://arxiv.org/abs/2410.24164).
[^pi05]: Physical Intelligence et al. (2025). [π₀.₅: a Vision-Language-Action Model with Open-World Generalization](https://arxiv.org/abs/2504.16054).
[^pi07]: Physical Intelligence (2026). [π₀.₇](https://www.pi.website/blog/pi07).
[^generalist]: Generalist AI (2026). [Towards machines with a thousand hands](https://generalistai.com/blog/towards-machines-with-a-thousand-hands).
[^commonsense]: Generalist AI (2026). [Physical commonsense](https://generalistai.com/blog/physical-commonsense).
[^rhoda]: Rhoda AI (2026). [FutureVision](https://www.rhoda.ai/).
[^dreamzero]: Ye, S. et al. (2026). [World Action Models are Zero-shot Policies](https://arxiv.org/abs/2602.15922).

[^index]: Figure AI (2026). [Index: the largest useful robot training dataset in the world](https://www.figure.ai/news/introducing-index).
[^eureka]: Ma, Y. J. et al. (2023). [Eureka: Human-Level Reward Design via Coding Large Language Models](https://arxiv.org/abs/2310.12931).
[^dreureka]: Ma, Y. J. et al. (2024). [DrEureka: Language Model Guided Sim-To-Real Transfer](https://arxiv.org/abs/2406.01967).
[^molmo]: Fang, H. et al. (2026). [MolmoAct2: Action Reasoning Models for Real-world Deployment](https://arxiv.org/abs/2605.02881).

[^groot15]: NVIDIA GEAR (2025). [GR00T N1.5: An Improved Open Foundation Model for Generalist Humanoid Robots](https://research.nvidia.com/labs/gear/gr00t-n1_5/).
[^smolvla]: Shukor, M. et al. (2025). [SmolVLA: A Vision-Language-Action Model for Affordable and Efficient Robotics](https://arxiv.org/abs/2506.01844).
[^tinyvla]: Wen, J. et al. (2024). [TinyVLA: Towards Fast, Data-Efficient Vision-Language-Action Models for Robotic Manipulation](https://arxiv.org/abs/2409.12514).
[^nanovla]: Chen, J. et al. (2025). [NanoVLA: Routing Decoupled Vision-Language Understanding for Nano-sized Generalist Robotic Policies](https://arxiv.org/abs/2510.25122).
[^kaplan]: Kaplan, J. et al. (2020). [Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361).
[^legged]: Agarwal, A. et al. (2022). [Legged Locomotion in Challenging Terrains using Egocentric Vision](https://arxiv.org/abs/2211.07638).
[^robodojo]: Zhang, W. et al. (2026). [An Unexpected Robot Policy: Early Evaluations of GPT-6 Astra on RoboDojo and Beyond](https://robodojo-benchmark.com/report/gpt-6-astra-eval). See also Chen, T. et al. (2026). [RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies](https://arxiv.org/abs/2607.04434).
[^rcastra]: Robocurve (2026). [GPT-6 Astra on robot arms](https://openai.robocurve.org/gpt-6-astra/).
[^rcfable]: Robocurve (2026). [Fable 5.1 on robot arms](https://anthropic.robocurve.org/fable-5.1/).
[^fetch]: Anthropic (2025). [Project Fetch: Can Claude train a robot dog?](https://www.anthropic.com/research/project-fetch-robot-dog).
[^claudebots]: Anthropic (2026). [How Claude performs on robotics tasks](https://www.anthropic.com/research/claude-plays-robotics).
[^feifei]: Li, F.-F. (2025). [From Words to Worlds: Spatial Intelligence is AI's Next Frontier](https://drfeifei.substack.com/p/from-words-to-worlds-spatial-intelligence).
[^epoch]: Epoch AI (2025). [LLM inference prices have fallen rapidly but unequally across tasks](https://epoch.ai/data-insights/llm-inference-price-trends).
