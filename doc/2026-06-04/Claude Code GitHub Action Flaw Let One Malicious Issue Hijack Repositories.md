# Claude Code GitHub Action Flaw Let One Malicious Issue Hijack Repositories

- 来源: 未知
- 发布时间(UTC): 2026-06-04 12:32:00
- 原文链接: https://thehackernews.com/2026/06/claude-code-github-action-flaw-let-one.html

----

Title: Claude Code GitHub Action Flaw Let One Malicious Issue Hijack Repositories

URL Source: http://thehackernews.com/2026/06/claude-code-github-action-flaw-let-one.html

Published Time: Fri, 05 Jun 2026 04:59:34 GMT

Markdown Content:
__ Swati Khandelwal __ Jun 04, 2026 Vulnerability / AI Security

[![Image 1](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhiaBF9jAklPh1ncr_eVPGnV229BSTNgAjkScVm-yTXAn4IcBjjZoLIglasRdu1XEPafCxJhqVZrC3zkNWilyAhN-6Ox8z2HBRjNg2D4aqJsDiRDg02BgAy4zgwU2100ZLIO8yTOtarI0Vxa3AGUQk0GZq1_zKSFQOhNiNoyVsP2AldJZoW8ZJ1rY936ZI/s1700-e365/claude-code-hack.jpg)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhiaBF9jAklPh1ncr_eVPGnV229BSTNgAjkScVm-yTXAn4IcBjjZoLIglasRdu1XEPafCxJhqVZrC3zkNWilyAhN-6Ox8z2HBRjNg2D4aqJsDiRDg02BgAy4zgwU2100ZLIO8yTOtarI0Vxa3AGUQk0GZq1_zKSFQOhNiNoyVsP2AldJZoW8ZJ1rY936ZI/s1700-e365/claude-code-hack.jpg)

A security researcher found a flaw in Anthropic's Claude Code GitHub Action that let an attacker take over vulnerable public repositories running it, with nothing more than a single opened GitHub issue. Because Anthropic's own action repo used the same workflow, a working attack could have pushed malicious code into the action itself and onto the projects downstream that pull it.

RyotaK of GMO Flatt Security [reported](https://flatt.tech/research/posts/poisoning-claude-code-one-github-issue-to-break-the-supply-chain/) the core bypass to Anthropic in January, and Anthropic [fixed it within four days](https://github.com/anthropics/claude-code-action/commit/1bbc9e7ff7d48e1299f7fa9698273d248e0cafea), with further hardening through the spring; the fixes are in claude-code-action v1.0.94. Anthropic rated the issues 7.8 under CVSS v4.0 and paid a bug bounty.

Claude Code GitHub Actions drops Claude into CI/CD pipelines to triage issues, slap on labels, review pull requests, or run slash commands. By default, the workflow gets read and write access to a repo's code, issues, pull requests, discussions, and workflow files. Because those permissions are broad, the action is supposed to be picky about who can trigger it: only users with write access.

[![Image 2: Cybersecurity](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjPEV6-530TOlxG6PjrmdlY623wpBwduZ7t1HV6flcmO5R4q4AmfixDUzW0CrhlvMVNWbhvOIso-UDNTka4W_W9Chrdj_dglwBZwi7DuePM2IMIl-hfUYVIqBXgfpr_2619K8Gptb4LzwJ6gUbi7lWl2M8AFQJsHEaw63Q7tZ6708YGruiHrr0Y2W9YYxLQ/s728-e100/ThreatLocker-d.png)](https://thehackernews.uk/ai-cant-stop-d)

The trigger check had a hole. It waved through any actor whose name ended in [bot], on the assumption that GitHub Apps are trusted things admins install. Trouble is, anyone can register a GitHub App, install it on a repo they own, and use its token to open an issue or pull request on any public repository. The action saw "a bot" and let the attacker's content through. Tag mode had an extra check to confirm the actor was a real human; agent mode didn't, which left it open.

From there, the attacker leans on indirect prompt injection, the trick of planting instructions inside content that an AI reads so the model follows them instead of its actual task. RyotaK wrote an issue whose body looked like an error message, then refined the prompt until Claude would "recover" by running the commands buried in it. The target is /proc/self/environ, the Linux file that holds a process's environment variables, secrets included. Claude Code blocks naive reads, but RyotaK bypasses the guard anyway and gets Claude to write the values back into the issue, where the attacker can grab them.

The real prize in those variables is the credential pair GitHub Actions uses to request an OIDC token, a signed token that proves "I'm this workflow running in this repo." Claude Code trades that token with Anthropic's backend for a Claude GitHub App installation token with write access. Steal those credentials, replay the exchange, and you hold write access to the target's code, issues, and workflows. Aim it at the claude-code-action repo itself, and you could poison the action that downstream projects pull.

[![Image 3](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg0a4Sshmuk29x9oSZTeqY5EJjEq0PRomnobviF3VoxBTB3Rk7h733vM1jKWZ95FN6GFJKbSzXaLsTOmE_HouZXbJStg9RhOAlM8D6sPFf3ZoDsWobpxPJ02VdIWVkXLqkb2uDeqV_lTSKJRCCoZZeGRw_A2zQYDeT99xQZtCBZIVYh6sI3Iw1y4p6vY40/s1700-e365/claude-github-action.jpg)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg0a4Sshmuk29x9oSZTeqY5EJjEq0PRomnobviF3VoxBTB3Rk7h733vM1jKWZ95FN6GFJKbSzXaLsTOmE_HouZXbJStg9RhOAlM8D6sPFf3ZoDsWobpxPJ02VdIWVkXLqkb2uDeqV_lTSKJRCCoZZeGRw_A2zQYDeT99xQZtCBZIVYh6sI3Iw1y4p6vY40/s1700-e365/claude-github-action.jpg)

RyotaK also flagged a softer route that skipped the bot trick entirely. Anthropic's own example issue-triage workflow shipped with allowed_non_write_users: "*", which lets anyone trigger it, a setting Anthropic's docs already flag as risky. Worse, Claude was posting task summaries to the workflow run's publicly visible summary panel, a ready-made way to leak data out. Plenty of repos copied that example and inherited the hole.

There's also a path for an attacker who can edit issues but can't trigger Claude on their own: edit a trusted user's issue after it has fired the workflow, but before Claude reads it, and the payload rides in as "trusted" input.

What to do? Update to claude-code-action v1.0.94 or later. Then audit any workflow that lets users without write access, or bots, trigger Claude: if it is taking untrusted input, don't feed it any secret beyond the Anthropic API key and GITHUB_TOKEN, and remove tools and permissions that can be used for exfiltration.

[![Image 4: Cybersecurity](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhFlTC7RrRZGiFAgASS0noWSL0qsQGFVp8-Hvuw9yp3X3VKRuTcb5SsPX09wJzrdIM6pu1_5lS4EeZp7Sx4iYBpNJkrGnpr08yyaS1HQ5_5TxaCsP6O0OtHNuOkesn6CbNjao1GPulCJk-uljYMSfMZfBYNrngpe669t7jlRn1FqiEnXhsFD1WVkpaYIVgh/s728-e100/ai-d.jpg)](https://thehackernews.uk/vpn-threat-report-m)

None of this is theoretical. The same setup, an AI issue-triager plus broad permissions plus prompt injection, already caused a real supply-chain hit:

*   In February, a prompt-injected issue title against Cline's claude-code-action triage workflow let attackers steal an npm publish token and push an unauthorized [cline@2.3.0](https://thehackernews.com/2026/02/cline-cli-230-supply-chain-attack.html). The rogue version only force-installed a separate, non-malicious AI agent and was pulled about eight hours later, but the same chain could just as easily have shipped real malware to everyone who updated.
*   The autonomous "HackerBot-Claw" bot then spent late February [probing GitHub Actions misconfigurations](https://thehackernews.com/2026/03/five-malicious-rust-crates-and-ai-bot.html) at Microsoft, Datadog, CNCF projects, and others, though when it tried to prompt-inject a Claude-based reviewer through a poisoned config file, Claude caught it and refused.

There's no public sign of this exact path, the one that poisons Anthropic's own action, was used against a live target; RyotaK proved it only in his own test repos, and he's careful to separate that from the variants above that did get exploited.

RyotaK says he has now reported around 50 separate ways to bypass Claude Code's permission system and run commands, part of a steady run of [prompt-injection flaws in AI coding agents](https://thehackernews.com/2026/04/google-patches-antigravity-ide-flaw.html). Prompt injection still isn't solved, and an agent with real tools and real tokens can be pushed as far as its permissions allow.

Found this article interesting? Follow us on [Google News](https://news.google.com/publications/CAAqLQgKIidDQklTRndnTWFoTUtFWFJvWldoaFkydGxjbTVsZDNNdVkyOXRLQUFQAQ), [Twitter](https://twitter.com/thehackersnews) and [LinkedIn](https://www.linkedin.com/company/thehackernews/) to read more exclusive content we post.