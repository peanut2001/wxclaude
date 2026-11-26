# Testing Claude Ship's "/ship" on a Real-World Project of About 10,000 Lines: Strengths and Limitations Revealed in Comparison with Copilot

- 来源: 未知
- 发布时间(UTC): 2026-11-26 01:21:00
- 原文链接: https://note.com/moto_solo_works/n/nb31a922f0944?hl=en

----

Title: Testing Claude Ship's "/ship" on a Real-World Project of About 10,000 Lines: Strengths and Limitations Revealed in Comparison with Copilot

URL Source: http://note.com/moto_solo_works/n/nb31a922f0944?hl=en

Final URL: https://note.com/moto_solo_works/n/nb31a922f0944?hl=en

Published Time: 2026-11-26T14:41:14.000+09:00

Markdown Content:
Code review, automated fixes, push, and PR monitoring—how much can we actually leave to AI?

On November 23, 2026, Anthropic announced "Claude Ship."

The development workflow—where we previously had AI write code, another AI review it, and then had AI fix those issues again—is about to become even more automated.

This time, what caught my attention was the /ship command added to Claude Code.

I immediately tested it on changes involving 79 files and roughly 10,000 lines of additions in a business system I am currently developing.

Furthermore, I had GitHub Copilot and Claude's standard code review features examine the exact same changes to compare the results.

In this test, I was able to incorporate six fixes automatically resolved by /ship directly into actual product development.

On the other hand, there were also issues that /ship alone could not catch.

In this article, beyond just introducing the new feature, I will discuss the strengths and limitations of /ship discovered through hands-on use, as well as how I plan to incorporate it into my development workflow going forward.

## From code reviews and fixes to PR monitoring: "/ship" arrives in Claude Code

Throughout this code review series, we have explored whether humans really need to read all AI-written code and what kind of review mechanisms are necessary.

Last time, I actually used GitHub Copilot's code review to examine its feedback and associated costs.

AI has dramatically increased coding speed. However, that does not mean the work after writing code has disappeared.

Checking review results, assessing feedback, requesting fixes, and running tests. If issues arise, fixing them once more.

When developing multiple systems on your own like I do, repeating this cycle becomes a substantial burden.

Even if you start another task while the AI handles development, once review results come back, you have to switch back to the original task.

The newly introduced /ship is a command designed to delegate this series of post-development tasks to AI.

The scope of AI's responsibilities has expanded—not just to writing code, but to the entire process of getting that code ready to be integrated into the system.

## What is Claude Ship? And what does "/ship" do within it?

[![Image 1: Image](https://assets.st-note.com/img/1795670655-mSjOptd3zlIQ9ao7qDUi0VET.png?width=1200)](https://assets.st-note.com/img/1795670655-mSjOptd3zlIQ9ao7qDUi0VET.png?width=1200)

Claude Ship is a system that automates the workflow on GitHub from code review to fixes and approvals.

First, let's briefly explain the term PR (Pull Request).

A PR is essentially a request asking for developed features or modified code to be incorporated into the system's official codebase.

Checking the details of that request is called a code review, and incorporating it into the official codebase is called "merging."

Claude Ship divides the tasks for this PR across three AI agents.

[![Image 2: Image](https://assets.st-note.com/img/1795670628-hOb8mAL265NpDKfYijQUcBFE.png?width=1200)](https://assets.st-note.com/img/1795670628-hOb8mAL265NpDKfYijQUcBFE.png?width=1200)

Code Review is a feature already generally available, while PR Steward and Claude Approvals are available in beta.

And the star of the show this time, /ship, is a command developers run themselves from Claude Code to kick off this sequence of tasks.

Basically, you run the following once your development is complete:

/ship

Claude reviews the changes and proceeds as needed with creating a commit history, pushing to GitHub, creating a PR, conducting code reviews, making fixes, and running various checks.

Furthermore, it is designed to monitor the PR and handle new review comments or check failures.

However, running /ship does not mean the code will be unconditionally approved and merged into the system. Whether it can ultimately be merged also depends on permissions and settings on the GitHub side.

[Official Anthropic Announcement: Introducing Claude Ship](https://claude.com/resources/articles/introducing-claude-ship)

## Differences Between Individual and Team Plans

Seeing the announcement of Claude Ship, some might have thought it wasn't available on individual plans.

This part is a bit confusing.

You need to consider the /ship command and the Claude Ship framework used across an entire team separately.

[![Image 3: Image](https://assets.st-note.com/img/1795670711-e0HpMAsZgRov4FyXduwUq5VE.png?width=1200)](https://assets.st-note.com/img/1795670711-e0HpMAsZgRov4FyXduwUq5VE.png?width=1200)

*This summary is based on information available as of November 26, 2026.

/ship and /steward are commands executed within your own Claude Code session. There is no confirmed mention of the commands themselves having different functionality between individual and team plans.

On the other hand, with the Team plan, administrators can configure settings on a per-repository basis (the location where code and change history are managed), allowing tasks to start in the cloud automatically when a PR is created, without developers having to run a command.

The pricing structures also differ. While /ship consumes your standard Claude Code usage allowance, the cloud features for teams incur usage-based billing.

This means that even a solopreneur like me can test the review and automated remediation capabilities of /ship on an individual plan.

## 79 files, about 10,000 lines added: Running "/ship" on a real-world development project

The subject of this test is "smartCC," a multi-channel CRM system I am developing.

Since I was developing a feature to manage and publish release information for each product, I chose that PR as the test subject.

### The test subject this time

[![Image 4: Image](https://assets.st-note.com/img/1795670886-EmBuSqJk8MWfKhXFbiToRD02.png?width=1200)](https://assets.st-note.com/img/1795670886-EmBuSqJk8MWfKhXFbiToRD02.png?width=1200)

Note that this PR also included changes from another PR that had not yet been formally merged.

Rather than creating a small program specifically for testing, this was a verification on an actual business system under active development.

### Wait, it ended with just a review?

I went ahead and ran /ship right away.

However, the expected automated remediation and PR monitoring did not happen, and the process finished after only performing a code review.

Claude explained that because the GitHub integration feature could not handle this PR, it would only perform a review.

I checked my GitHub login status and the command execution environment, but found no particular issues.

That's when I noticed the repository name.

The repository name this time started with a leading hyphen (-).

Tools that execute commands sometimes treat a leading hyphen as an option flag. I suspected this might be the cause.

### Re-testing after changing the repository name

I prepared a small test repository and compared how /ship behaved when the name was changed.

[![Image 5: Image](https://assets.st-note.com/img/1795670936-V0gQtHAPf8O31eTnqB6zSi52.png?width=1200)](https://assets.st-note.com/img/1795670936-V0gQtHAPf8O31eTnqB6zSi52.png?width=1200)

Sure enough, only when there was a leading hyphen did it switch to review-only mode.

While I haven't confirmed this as an official specification, it was a reproducible behavior in my environment.

Changing an existing repository name could also affect related development environments and systems.

Therefore, I decided to create a private duplicate repository containing the exact same changes as the actual PR and run /ship once again.

This time, the process was able to proceed beyond just the review to include automated remediation, pushing updates to GitHub, and monitoring the PR.

## How Capable Is "/ship" at Code Review? Comparing Four Reviews by Copilot and Claude

To evaluate the review capabilities of /ship, I ran a total of four reviews on the changes in that same PR.

The tools compared were GitHub Copilot, Claude Code's /code-review high, and two runs of /ship.

### Comparison of Review Results

[![Image 6: Image](https://assets.st-note.com/img/1795671103-lGb6AUtjZhgSE07NWkvp4z3s.png?width=1200)](https://assets.st-note.com/img/1795671103-lGb6AUtjZhgSE07NWkvp4z3s.png?width=1200)

*Copilot had 1 comment whose adoption depended on requirements. The second /ship run verified the validity of the 6 resolved issues, but not all comments were aggregated using identical criteria. Additionally, whether an issue was deemed valid was determined by cross-checking the code against the specifications, and not all issues were actively reproduced in practice.

Looking only at the numbers, Claude might appear to be superior.

However, what caught my attention in these results was not the sheer volume of comments.

**It was the fact that each review uncovered entirely different issues.**

### Issues Claude Found and Copilot Missed

Particularly crucial this time was feedback regarding publication permissions.

It was pointed out that release information meant to be password-protected could potentially become publicly accessible to anyone under specific editing actions.

This was not a simple display bug, but rather an issue concerning information disclosure permissions.

Both Claude's standard code review and /ship flagged this issue.

On the other hand, Copilot failed to point this out.

### Issues Copilot Found and Claude Missed

Conversely, there were issues that only Copilot flagged.

This was an issue noting a lack of concurrency control to maintain data integrity when multiple users perform operations simultaneously.

Concurrency control is a mechanism designed to prevent data conflicts and inconsistencies when multiple operations run at the same time.

Even if there are no problems during normal operation, bugs can occur when the timing of operations overlaps.

Claude was unable to point out this issue during this review.

### Review Results Differ Even with the Same Claude

What was even more interesting was that the results differed even when using the same Claude.

In the standard code review, it pointed out the possibility of accidental update conflicts occurring after saving.

On the other hand, the first /ship pointed out a lack of permission checks during new creation, while the second /ship pointed out an issue that could lead to unintentional redirection to external sites.

Across these four reviews, only a single issue was consistently pointed out by all of them.

Moreover, each AI has false positives and missed issues.

It is impossible to definitively determine which tool is best based solely on this verification. The number of runs differed, and the required time and usage costs were not measured under identical conditions.

However, at least from these results, I felt that **you cannot say code review is sufficient just by picking a single superior AI**.

## "/ship" Doesn't Just Point Out Issues: From Automatic Remediation to Push and Monitoring

This is the part I was looking forward to the most in this verification of /ship.

In a standard code review, after the AI points out an issue, developers must review the details and make the fixes themselves.

However, /ship doesn't just point out issues; it actually proceeds with the remediation work.

The results of running it in a cloned repository are as follows.

[![Image 7: Image](https://assets.st-note.com/img/1795671268-nDVTb48eHSJajQBxAZlKPXMf.png?width=1200)](https://assets.st-note.com/img/1795671268-nDVTb48eHSJajQBxAZlKPXMf.png?width=1200)

The automatically fixed items included deficiencies in publication permissions, issues leading to redirection to external sites, and problems where parts of the information were missing on list screens.

Furthermore, it didn't just fix the bugs; it also added test code to prevent the same issues from recurring.

### It Did Not Proceed Arbitrarily When Unable to Run Checks

What I appreciated this time wasn't just its fixing capabilities.

There was a scenario where the necessary external libraries were not prepared in the development environment, making it impossible to check the fixes afterward.

Additionally, because we use a paid icon library, an issue arose where the necessary library could not be fetched without authentication credentials.

At this point, Claude did not arbitrarily push unverified changes to GitHub; instead, it paused the process and asked for my judgment.

After I set up the necessary environment, it ran type checks, static code analysis, and tests, pushing the changes to GitHub only after they all passed.

The operation of sending changes to GitHub is called a push.

After that, it left comments on the PR detailing the fixes and continued monitoring.

The final merge was left to me and was not executed automatically.

### Adopting the Auto-Repaired Code into the Actual Product

I reviewed the two commit histories created by /ship.

As a result, I determined that all the changes were appropriate and merged them into the actual smartCC development repository.

In the tests run after merging, all 29 server-side processes, 9 admin screen items, and 14 public screen items passed.

A major takeaway from this experience was not just that the AI was able to fix the code, but that its fixes could actually be adopted into real product development.

## The Strengths and Limitations of "/ship" Discovered Through Real-World Use

[![Image 8: Image](https://assets.st-note.com/img/1795671470-JcxHnGVSs2arjO03Zw5TNzu1.png?width=1200)](https://assets.st-note.com/img/1795671470-JcxHnGVSs2arjO03Zw5TNzu1.png?width=1200)

Through this trial, the practical utility of /ship in day-to-day operations was clearly evident.

The entire series of tasks—reviewing, fixing, checking, pushing to GitHub, and reporting on the changes made—can proceed without having to guide the AI step-by-step yourself.

On the other hand, several limitations also became apparent.

First, for the AI to proceed with fixes, a development environment capable of running tests must be prepared beforehand.

No matter how capable the AI is, without an environment and tests for verification, confirming whether its fixes are correct becomes difficult.

Second is the issue of missed review points.

While the six items fixed by /ship this time were valid, some of the issues flagged in other reviews remained unfixed.

Just because the tests pass does not mean that every problem has been resolved.

In addition, because the cloned repository used this time did not have CI (a system that automatically runs tests and other checks when code changes), how it handles CI errors remains untested. Actual operational checks on screens involving browser interactions were also not included in the scope of this automatic remediation.

Furthermore, this series of automatic remediation tests was conducted only once. It does not guarantee that fixes will be provided with the same quality every time.

I think it is important to use it while understanding these limitations.

## How I Would Integrate /ship into the Development Workflow

I handle everything from system design, development, and quality assurance to operations on my own.

Therefore, being able to reduce the time spent on code reviews and addressing revisions is a major advantage for moving forward with tasks other than development.

Based on this evaluation, I would like to try the following development flow going forward:

1.   Proceed with development alongside AI

2.   Have GitHub Copilot review the code as well

3.   Proceed with code reviews and fixes using /ship

4.   Have a human check unaddressed feedback and the content of fixes

5.   Perform necessary operational checks, and have a human make the final decision to merge

Basically, the idea is to place /ship at the core of review and remediation, using Copilot in a supplementary reviewer role.

[![Image 9: Image](https://assets.st-note.com/img/1795671512-stMq5dYADmQPIfwN73OUyrX2.png?width=1200)](https://assets.st-note.com/img/1795671512-stMq5dYADmQPIfwN73OUyrX2.png?width=1200)

The reason for having different AIs review the code is not simply to increase the number of checks.

It is to reduce issues that a single AI might overlook by reviewing the code from different perspectives.

This time, issues that Claude itself had overlooked during its review after writing the code were pointed out by Copilot, which prompted me to rethink the importance of this approach.

Additionally, in team development, you can use Claude Approvals to set up approval rules based on the nature of the changes.

Leave changes with limited impact, such as documentation updates, to the AI. On the other hand, have humans check critical changes related to authentication, permissions, billing, and the database.

By establishing rules like these, there is potential to advance automation even further.

However, acceptable risk levels also differ between in-house products and systems entrusted to us by clients.

Rather than applying the same rules to every system, I want to determine the scope delegated to AI according to the characteristics of each system.

## "/ship" Handles Everything from Review to Fixes: Who Makes the Final Decision?

Having used /ship on an actual development project this time, I feel that I want to actively incorporate it into my future development workflows.

The AI points out issues, fixes them, runs tests, and reports the results.

Until now, these were tasks I had to instruct step by step.

If I can delegate that entire series of tasks to /ship, I can spend that time on designing other features, making proposals to clients, planning new products, and more.

Of course, AI reviews do miss things. The fixes made are not always correct, either.

That is precisely why the answer is not to avoid using AI, but rather to build a framework that guarantees quality by combining multiple AIs, testing, and development rules.

My development style, which began with having AI write code, moved on to having AI review code, and is now advancing to the stage of delegating the entire process from review to fixes.

**Delegate the tasks to AI. Take responsibility yourself for the framework that guarantees quality and for making the final decisions.**

That is my current approach to working with /ship.

[![Image 10: Image](https://assets.st-note.com/img/1795671622-Ubt3ZeSM15h07aIFciOxoK2k.png?width=1200)](https://assets.st-note.com/img/1795671622-Ubt3ZeSM15h07aIFciOxoK2k.png?width=1200)

* * *

Thank you very much for reading to the end.

To what extent do all of you incorporate AI-driven code reviews and automated fixes into your development?

I would be glad if this article serves as an opportunity for you to reflect on AI-powered development and system quality control.

[![Image 11: Image](https://assets.st-note.com/img/1795671564-8Vp9agdzyi1o76bjUBWYK0FD.png?width=1200)](https://assets.st-note.com/img/1795671564-8Vp9agdzyi1o76bjUBWYK0FD.png?width=1200)

Code Review Serial by an AI Solopreneur

*   [#01 Should You Read All Code Written by AI?](https://note.com/moto_solo_works/n/n337c130b4f5f)

*   [#02 Code Review in Contract Development vs. Personal Development](https://note.com/moto_solo_works/n/n2645831f0dc6)

*   [#03 My Own Code Review Practices](https://note.com/moto_solo_works/n/n26bb753471c6)

*   [#04 Testing Code Reviews with Claude Team](https://note.com/moto_solo_works/n/ne15baf43c973)

*   [#05 Field Testing GitHub Copilot's Code Reviews](https://note.com/moto_solo_works/n/nc533768678a6)

### Reference Sites

*   [Official Anthropic: Introducing Claude Ship](https://claude.com/resources/articles/introducing-claude-ship)

*   [Claude Ship Official Product Page](https://claude.com/product/claude-ship)

*   [Claude Ship Documentation](https://code.claude.com/docs/en/claude-ship)

*   [/ship Command Documentation](https://code.claude.com/docs/en/ship-command)

[![Image 12: Image](https://assets.st-note.com/img/1795671586-I2PvVsDUTx9bKnq7lEQozwLN.png?width=1200)](https://assets.st-note.com/img/1795671586-I2PvVsDUTx9bKnq7lEQozwLN.png?width=1200)