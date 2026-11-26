# To Those Paying for Claude but Only Getting Shallow Answers | 5 Things to Fix Before Writing Your Prompt, Learned from the Official Guide

- 来源: 未知
- 发布时间(UTC): 2026-11-25 22:31:00
- 原文链接: https://note.com/noted_gerbil9067/n/n216ecd389a29?hl=en

----

Title: To Those Paying for Claude but Only Getting Shallow Answers | 5 Things to Fix Before Writing Your Prompt, Learned from the Official Guide

URL Source: http://note.com/noted_gerbil9067/n/n216ecd389a29?hl=en

Final URL: https://note.com/noted_gerbil9067/n/n216ecd389a29?hl=en

Published Time: 2026-11-26T15:31:58.000+09:00

Markdown Content:
You subscribed to a paid AI plan, but the answers you get somehow feel shallow.

They are full of generic platitudes you feel like you have seen somewhere before.

In times like that, it's tempting to tweak the wording of how you ask, isn't it?

However, reading the official guide from the company that makes Claude reveals that the wording isn't what needs fixing.

**Answers become shallow because the "materials" you give the AI are either insufficient or disorganized.** The official guide outlines five ways to fix this.

In this article, I read Anthropic's (the company that makes Claude) official document "Prompting best practices" and summarized it into a format anyone can use right away.

## Answers Are Shallow Because You Aren't Asking Like You Would a New Hire

The official guide uses an analogy like this:

Claude is like a "brilliant new hire who has just joined the company."

While smart, it doesn't know your company's procedures or your usual preferences.

That is why asking it merely to "summarize this nicely" results in a safe, generic answer that could apply to anyone.

It's just like how a new hire would be at a loss if you simply told them to do it "nicely."

The guide also explained how to test this.

**Try showing the prompt you wrote to a coworker who doesn't know the context.** If the coworker is confused, Claude will be confused too.

[![Image 1: Image](https://assets.st-note.com/img/1795674678-krCNHP1AD4nV02tG3KieZxOo.png?width=1200)](https://assets.st-note.com/img/1795674678-krCNHP1AD4nV02tG3KieZxOo.png?width=1200)

## 1. Clearly and Specifically State What You Want Done

The first point is the most fundamental.

*   **Decide on the format**: 5 bullet points, around 300 words, in a table, etc.

*   **Specify conditions**: For internal use, no technical jargon, polite tone, etc.

*   **Number steps if the order matters**: "1. First... 2. Next..."

The guide also states, "If you want more than the bare minimum, ask for it clearly."

In other words, you can't always count on AI to be considerate enough to anticipate what you haven't explicitly said.

## 2. Include "why you want it done that way"

The second point is to include your reasoning.

The example in the guide was very clear, so let's translate it into Japanese.

*   **Weak prompt**: "Never use ... (ellipses)."

*   **Strong prompt**: "This text will be read aloud by text-to-speech software, so do not use ellipses. The software does not know how to read them."

It notes that when Claude understands the reason, it can extrapolate and think beyond that specific instruction.

For example, if it knows the text will be "read aloud," it will also avoid hard-to-read symbols and brackets on its own.

## 3. Provide 3 to 5 examples

The third point is examples.

According to the guide, examples are one of the most reliable ways to align the output's format, tone, and structure.

The recommended amount is **3 to 5 examples**. There are 3 key tips when providing examples:

*   **Relevant**: Make the examples closely match what you actually want to achieve

*   **Diverse**: If they are too similar, even unwanted quirks might be imitated

*   **Clearly separated**: Distinctly separate them from your instructions so it is obvious they are examples

Rather than just showing a single example and saying "like this," providing three slightly different examples conveys your intent much better.

## 4. Separate content into "boxes" before passing it over

The fourth point is how to organize your materials.

If instructions, context, examples, and reference materials are all jumbled together in your prompt, the AI gets confused about which part is the actual instruction.

In the guide, it is recommended to **wrap each piece of content with name labels called tags**, such as <instructions> (directions), <context> (background), and <input> (materials to provide).

You can name the tags whatever you like, but the trick is to use the same names every time.

It's just like writing "Kitchen" or "Books" on moving boxes so the person unpacking won't get confused.

## 5. Put Long Documents First, Questions Last

The fifth point is the order when providing long documents.

According to the guide, it is best to place long documents **near the top** of the prompt, and write questions or instructions **at the very end**.

It also noted that in complex situations with lots of reference materials, putting the question at the end improved response quality by up to 30% in tests.

Another tip is to **have it extract relevant parts from the materials before answering**.

Having it extract them first makes it less likely to be swayed by irrelevant details.

## What I Learned

What I realized from reading it was that in many cases, whether an answer is shallow is determined more by "how you provide it" than by the "AI's brain."

Before upgrading to a higher plan, try just one of these five tips first.

My top recommendation is the second one: "Include your reasoning." You can do it simply by adding a single line to your usual prompt.

I also wrote an article compiling what you can do with Claude Code into a quick reference chart based on the official page. Feel free to check that out as well.

[What You Can Do with Claude Code: A Quick Reference Chart of 9 Official Features](https://note.com/noted_gerbil9067/n/nbedaf18f4673)

## What I'd Like to Ask Everyone

When you feel an AI's answer is "shallow," what do you usually do?

Rephrase your request, ask a different AI, give up...? I'd love it if you let me know in the comments.

Liking and following really motivates me to write my next article.

## References

*   Anthropic: "Prompting best practices"[https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices)

*   Anthropic: "Prompt engineering overview"[https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/overview](https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/overview)