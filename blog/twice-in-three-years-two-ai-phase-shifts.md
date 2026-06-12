# Twice in Three Years: Two AI Phase Shifts

*February 2026* <sub>(updated May 2026)</sub>

In late 2022, when ChatGPT came out, it caught me off-guard. I don't remember what I asked first, but I remember the feeling. I was sitting on the sofa and I was shocked. I had been working in software for years, I knew roughly how neural networks worked, and still I was not prepared for what it felt like to have a computer just... understand what I was saying. Not through commands, not through syntax. Just language.

That was the first shift, and I can name it now in a way I couldn't then. For my whole career the machine had met me through syntax: commands, code, structured input. I translated my intent into its language. ChatGPT removed the translation. The interface stopped being formal and became human. The machine had learned to understand us.

The second time was in late 2025, when I first experimented with Claude Code running Opus 4.5. A different kind of shock, but just as strong. I described what I wanted to build, a system for automating operational records during drilling activities, and the thing came back with a plan and started executing it. With no obvious errors. The steering from my side was minimal. I worked with GitHub Copilot for years, but its "Agent" mode always felt like a distraction: I was quicker just asking questions and integrating the suggestions myself. This time it was quicker to let the agent do the work.

Comprehension was no longer the bottleneck by then. What changed was **agency** - not the will to act, which is still mine, but the execution. I still say what and whether; the machine now handles the how. I give it an under-specified goal and it decomposes, plans, and runs with it, where before I had to drive every step. **The first shift was on the input side, the second on the output side.**

> 2022 → the machine learned to understand us
> 2025 → the machine learned to act for us

Two moments, three years apart, two different abstractions. The capability built gradually in both cases. Language models and agents existed well before I noticed them. What I'm marking isn't the invention, it's the moment each crossed into undeniable. That's what a phase shift is: not a new thing appearing, but an accumulating one crossing a line. And that line is the part most people I talk to (even in tech) don't fully get yet.

Having worked with these models day to day, I knew the limitations. Models hallucinate. They are confidently wrong in ways a human would never be. The deeper problem is that they generalize only *locally*: they interpolate within the distribution of their training data, they don't reason their way to genuinely new situations the way people do. It's why a small rewording can tank an answer.[^chollet] I don't think LLMs will get us to AGI, not in their current form. I'm not alone in doubting it: in a 2025 AAAI survey, 76% of 475 respondents said scaling up current approaches is "unlikely" or "very unlikely" to yield AGI.[^aaai] I believe something different is needed: a new architecture, a new approach, I don't know what. LLMs are not the final thing. They are a stepping stone.

But a stepping stone that already changes the work. The second shift, the machine acting rather than just answering, is where the impact shows up. Things that took my team days take hours now. Unit testing and documentation are trivial. Prototyping is absurdly fast. The distance between having an idea and seeing it running has collapsed.

This is exciting and terrifying. If you're a knowledge worker (and I am one), the tools you use this year will reshape your job within a few years. Not decades. Years.

Nobody knows where this goes - not the people building these systems, and definitely not the people writing posts about them on X. What I know is the pattern: *first the machine learned to understand us, then it learned to act for us.* Two shifts in three years, each collapsing a different distance between intent and result. I expect a third. Probably sooner than I think.

[^chollet]: François Chollet, ["The future of AI," *Deep Learning with Python*](https://deeplearningwithpython.io/chapters/chapter19_future_of_ai/) - on local vs. extreme generalization.
[^aaai]: [AAAI 2025 Presidential Panel Report on the Future of AI Research](https://aaai.org/wp-content/uploads/2025/03/AAAI-2025-PresPanel-Report-FINAL.pdf).
