# Anthropic brings Skills over MCP to Claude and Claude Code in public beta

- 来源: 未知
- 发布时间(UTC): 2026-11-25 15:07:00
- 原文链接: https://cryptobriefing.com/anthropic-skills-over-mcp-claude-beta/

----

Title: Anthropic brings Skills over MCP to Claude and Claude Code in public beta

URL Source: http://cryptobriefing.com/anthropic-skills-over-mcp-claude-beta/

Final URL: https://cryptobriefing.com/anthropic-skills-over-mcp-claude-beta/

Published Time: 2026-11-25T23:08:49+00:00

Markdown Content:
A benchmark built from real physics projects finds AI agents mostly fail on reasoning and intuition, not textbook knowledge

AI models have passed plenty of exams. FrontierPhysics asks a harder question: can they do physics research?

For now, the answer is mostly no. Even the leader passes only about a third of the time. A post on X put Anthropic’s Claude Fable 5.2 at a score of 32%, six points ahead of OpenAI’s GPT-6.2 Astra.

The benchmark’s leaderboard, as of November 23, 2026, lists Claude Fable 5.2 at a 33.3% pass rate, the best of the AI agents tested. Human experts pass around 96% of the tasks.

## What FrontierPhysics actually measures

FrontierPhysics was released through an arXiv preprint on November 4-5, 2026. It tests AI agents on physics research work rather than quiz-style problems.

The preprint describes 56 tasks taken from the real projects of 42 physicists. Those researchers come from 26 institutions and work across nine subfields of physics, including condensed matter, AMO (atomic, molecular and optical physics), astrophysics and fluid dynamics.

Each task takes an agent through the full research loop. It has to review the literature and plan an experiment or simulation. Then it must run that work inside a sandboxed environment and deliver a structured output that ends in a scientific manuscript.

Grading uses two methods. Deterministic checks verify outputs that can be confirmed automatically. Expert-written scoring rubrics handle the rest, and those rubrics include “blocker” criteria.

A blocker is a dealbreaker. If an agent’s work violates a core requirement of scientific validity, a polished manuscript will not save the result. The benchmark also weights reproducibility.

## The leaderboard and the failure data

On the November 23 leaderboard, Claude Fable 5.2 is clearly in front at 33.3%. Other Claude variants follow at 27.4%. GPT-6.2 Astra is fourth at 26.8%.

The error analysis says more. Among the top agents’ failures, insufficient rigorous reasoning accounts for 48% of errors. A lack of expert intuition accounts for another 34%.

Gaps in physics knowledge explain only 11% of failures. The models generally know the material. They stumble when applying it with the care and instinct a working physicist brings to a project.

## Who built it

The project is led by BenchFlow, which was founded by Xiangyi Li. Bingran You of UC Berkeley is lead, and the author list runs past 71 co-authors.

Contributors include researchers from Caltech, Harvard and Stanford, among other institutions. FrontierPhysics builds on the team’s earlier work, called SkillsBench.

The group does not consider the current version final. It plans to grow the benchmark to 100 tasks, with a potential submission to Nature targeted for late 2026.

## What this means

For AI labs, FrontierPhysics is a new kind of scoreboard. On a test where the best agent passes roughly one task in three and human experts clear about 96%, there is plenty of room to separate the models.

The failure breakdown also gives developers a clearer target. If nearly half of errors come from sloppy reasoning and about a third from missing intuition, progress probably depends on how agents check their own work.

Tasks come from real projects by working physicists, and blocker criteria penalize scientifically invalid work. That makes the benchmark harder to game than tests built around multiple-choice answers or a single numeric output.

The task set is still fairly small, and the team plans to expand it. Scores on a 56-task benchmark can shift as new tasks are added and new models are submitted, so early rankings are a snapshot, not a verdict.

**Disclosure:** This article was edited by Diego Almada Lopez. For more information on how we create and review content, see our [Editorial Policy](https://cryptobriefing.com/editorial-policy/).