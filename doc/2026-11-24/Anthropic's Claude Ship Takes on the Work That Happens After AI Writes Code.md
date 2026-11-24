# Anthropic's Claude Ship Takes on the Work That Happens After AI Writes Code

- 来源: 未知
- 发布时间(UTC): 2026-11-24 02:15:00
- 原文链接: https://www.ciol.com/news/anthropic-claude-ship-automates-software-code-reviews-12837750

----

Title: Anthropic's Claude Ship Takes On The Work That Happens After AI Writes Code

URL Source: http://www.ciol.com/news/anthropic-claude-ship-automates-software-code-reviews-12837750

Final URL: https://www.ciol.com/news/anthropic-claude-ship-automates-software-code-reviews-12837750

Published Time: 2026-11-24T15:46:24+05:30

Markdown Content:
A developer finishes writing code, submits it for review and moves on to the next task. Then the feedback arrives. There are bugs to fix, tests that have failed and changes to make before the code can be merged. The developer has to return to the earlier task, make corrections and wait for another review.

Anthropic wants to automate much of this back-and-forth with Claude Ship, a new AI-powered workflow that can review pull requests, address coding issues and determine whether changes meet a team's approval rules.

Announced on November 23, Claude Ship brings together three capabilities: Code Review, PR Steward and Claude Approvals. The aim is to reduce the manual work involved in moving software changes from development to deployment.

A pull request (PR) is a proposal to add or modify code in a shared software project. Before the changes become part of the main codebase, developers typically review them, check for errors and obtain approval from designated team members.

Claude Ship divides this process into three stages.

## Finding problems before code is merged

The first component, Code Review, examines pull requests against the existing codebase to identify potential problems. It checks changes from multiple perspectives, verifies its findings and categorises issues before posting feedback.

Developers can choose between Quick, Standard and Deep review levels depending on the requirements of their projects. Code Review is already generally available.

## Fixing issues without repeated developer intervention

The second component, PR Steward, takes over some of the follow-up work. If a continuous integration (CI) check fails, a merge conflict appears or a reviewer requests changes, the agent can investigate and work on the fixes.CI checks are automated tests that run when developers modify code to ensure that new changes do not break existing functionality.

PR Steward also explains what it has changed and how developers can undo those changes. Importantly, it is designed to fix pull requests, not approve or merge them.

## Deciding which changes need human approval

The third component, Claude Approvals, applies approval rules defined by engineering teams. It can approve routine changes when they meet the specified policies, while requiring human sign-off for sensitive or complex modifications.

Anthropic recommends that organisations initially run this feature in an observation-only mode. This allows teams to assess its decisions before allowing it to participate in their repository's branch protection rules, which determine what checks must pass before code can be merged.

Developers can start the workflow using the `/ship` command in Claude Code. Engineering administrators can also enable it across individual GitHub repositories, configure review levels and set spending limits.

Claude Ship is available to customers on Claude Team and Enterprise plans for GitHub repositories. While Code Review is generally available, PR Steward and Claude Approvals are in beta.

The service is billed based on token usage, with costs depending on the number and size of pull requests, review depth and the amount of work required to fix issues.

The launch reflects a broader shift in AI-assisted software development. As developers increasingly use coding agents to generate software, the next challenge is handling everything that follows: testing, reviewing, correcting and approving the code before it reaches production.