# The 'Design Document' I First Give to Claude and My Workflow for Making Games

- 来源: 未知
- 发布时间(UTC): 2026-10-22 22:56:00
- 原文链接: https://note.com/aigamelab/n/n53c1939eedf9?hl=en

----

Title: The 'Design Document' I First Give to Claude and My Workflow for Making Games

URL Source: http://note.com/aigamelab/n/n53c1939eedf9?hl=en

Published Time: 2026-10-23T12:40:21.000+09:00

Markdown Content:
## Introduction

Thank you to everyone who read my previous article.

In the comments, people touched on the story about 'fixing the last sound five times' and the idea of 'lining up sound candidates to choose from.' I was happy to learn that writing about failures, including how I realized them, really gets the message across.

Since then, I've made one more, bringing the total number of games I've created to **17**.

This time, as I promised in the last article, I will write about **how I actually make them**.

1.   **How to write a design document** (The document I first give to Claude)

2.   **How to proceed with the work** (How to divide phases and when to play and verify)

3.   **Saving usage** (Tips for not hitting the limit during long tasks)

This time, too, I will write not only the steps but also the failures I encountered before arriving at each method. At the end, I have also included a 'way to ask' that you can use directly with Claude.

## 1. How to write a design document

### I gave the design document, and it started making it right away

This is a story from when I started making 'Elevator Attendant,' a game where you just press buttons, but the customers' orders get increasingly troublesome.

I wrote the design document as usual and gave it to Claude. Then, after reading the document, Claude **started making it, going straight to the implementation of the first phase.**

As I wrote in the previous article, I use different models for the 'thinking role' and the 'making role.' The thinking role reads and organizes the design document, and the making role handles implementation. However, it proceeded to implementation while still in the thinking role.

Since then, when I give a design document, I make sure to clearly say, **'Stop after saving.'**

### I compile the design document while consulting with the AI

I compile the design document **while consulting with the AI.**

I talk about my vague idea of 'I want to make a game like this,' and have the AI ask me questions or suggest ideas. However, **I am the one who decides what to make.** I have the AI help me put that into words.

The design document for Elevator Attendant was about 5,700 characters in total, with 24 items. From those, I will introduce the **items that were particularly effective to write down.**

[![Image 1: 画像](https://assets.st-note.com/img/1792725469-H56SMwALdfrKk3ul9De0ETzQ.jpg?width=1200)](https://assets.st-note.com/img/1792725469-H56SMwALdfrKk3ul9De0ETzQ.jpg?width=1200)

Elevator Attendant. The design document was about 5,700 characters in total, with 24 items

### Effective Item 1: In a nutshell

> A game where you just press elevator buttons, but the customers' orders get increasingly troublesome

By writing this in one line at the beginning, both the AI and I can return to it whenever we get lost.

### Effective Item 2: Design Policy

> Don't make the controls difficult; make the situation difficult

In the elevator operator game, the controls remain 'press the button for the correct floor' until the end. Instead, the target floor might change mid-way, or you might be asked for a floor that doesn't exist.

If I don't write this down, the AI tends to add time limits or complex controls to 'make it difficult'.

### Effective Item 3: What to exclude

> Character growth, item collection, long-term prerequisites, complex stories, complex controls, massive assets, external 3D models, online features

The AI kindly adds features for me. However, there are things I don't want added. **By writing down 'what to exclude,' the scope doesn't expand too much.**

### Effective Item 4: What I want the player to think at the end

> It was just an elevator game at first, so why did it end up like this? lol

I believe this is the most important item. When I'm unsure about minor decisions, I can decide based on whether it brings the game closer to this sentiment.

### Effective Item 5: Phasing

I write out the contents of the phases from the beginning. For the elevator operator game, I divided it like this.

・Phase 1: Elevator space, floor buttons, moving between floors with buttons, simple passengers  
・Phase 2: Passenger target floors, judging correct answers, score, next passenger  
・Phase 3: Increasing difficulty, changing orders, multiple passengers, strange orders  
・Phase 4: Absurdist game development, non-existent floors, late-game events, ending  
・Phase 5: Visual and control adjustments, effects, bug fixes, tempo adjustments

I will write about how to proceed with the phases in the next chapter.

### Have the AI ask questions about anything it doesn't understand first

When I hand over the setting documentation, I add, **'If there are any points you don't understand or any contradictions, please ask me before you start building.'**

In the horror game 'The Way Home,' where you walk home at night, in the documentation I wrote, **the way the route was described and the flow of the story were inconsistent.** Claude pointed this out to me beforehand, so I was able to fix it before I started building. If I had built it as is, I think it would have resulted in a major rework later.

### Setting Document Template

I have turned the items I use into a template. You don't need to fill in everything. Having items 1, 5, 6, 7, and 8 in particular will help keep things consistent.

1.   In a nutshell (1 line)

2.   Playing environment (PC/smartphone, portrait/landscape, browser/Unity, etc.)

3.   Basic flow (what happens when you play once)

4.   Core fun/design policy

5.   Things to exclude

6.   What you want the player to think at the end

7.   Phase breakdown (contents of Phase 1 to N)

8.   Completion criteria (what constitutes a finished product)

The **completion criteria** for item 8 were not written in the elevator operator document. If you don't write them down, you'll want to keep fixing things forever. I will write about this in the next chapter as well.

### How to make requests

> 'Please stop after saving this setting document. If there are any points you don't understand or any contradictions, please ask questions before you start implementation.'

## 2. How to proceed with the work

The overall flow is as follows.

[![Image 2: 画像](https://assets.st-note.com/img/1792725478-LSak7qubQgBVz0EPfOxIvhRF.png?width=1200)](https://assets.st-note.com/img/1792725478-LSak7qubQgBVz0EPfOxIvhRF.png?width=1200)

My workflow. I play through each phase myself to give the OK, and then fix everything together at the very end.

I wrote a little about this last time, but this time I will write the reasons for each.

### Always play through it yourself at the end of a Phase

When a Phase ends, **I play it myself and give the OK before moving on to the next one.**

As I wrote in Pitfall 4 last time, in the 3D escape puzzle 'The Last School,' the AI's review found 7 bugs. However, when I played it, there were **4 issues that the review did not find**. All of them were things that 'worked in the code' but were clearly wrong when played.

AI can verify if something 'works correctly.' But only the player can know 'how it feels to play.' That is why I set aside time to play during each phase.

### Don't stop for minor details. Have them reported in batches.

When I first started building, every time Claude came up with a minor improvement idea, it would stop the work to confirm it with me. I appreciate it, but **having it stop to confirm every time was a hassle**. Besides, the more back-and-forth there is, the more usage increases (I will write about this in Chapter 3).

Now, I ask it to do this:

・**Only things that need immediate attention** should be reported by stopping the work  
・Bugs that prevent moving forward  
・Design issues that will affect later phases  
・Things that significantly deviate from the setting documentation  
・**Everything else** (minor visual adjustments, etc.) should be recorded and reported in a batch at the end of the phase

### Once the completion criteria are met, don't over-polish.

Finally, I play through the whole thing, and any problems I find are **fixed all at once in one go.** If the completion criteria are met, then it is finished.

Any ideas I come up with along the way like 'it would be better if I did this' are not added this time, but are just **written down in a 'for next time' memo.**

There is a reason I do this.

**Even if I fix things that bother me, other people might not care about them. Conversely, things that don't bother me might bother other people.**

As the creator, I play the same game dozens of times, so I start to notice minor details more and more. However, I don't know if those things are important to the player. That is why **I wait until I hear other people's opinions before doing any polishing or minor fixes.**

### Have it keep records.

I have Claude write a record every time it works. **It writes not only what was fixed, but also why it was that way in the first place.**

With this record, even if I start a new conversation, I can resume from where I left off. This also leads to savings in the next chapter.

### How to ask

> 'Please build only Phase 1. When finished, briefly report what was built, remaining issues, and the impact on the next phase, then stop. For minor visual improvement ideas, just record them without stopping the work.'

## 3. Saving on usage

### First, two definitions of terms

・**Conversation length (context)**: The amount the AI remembers within that conversation. Every time the AI replies, it re-reads the entire conversation up to that point. Therefore, **the longer the conversation, the more usage is consumed in a single interaction.**  
・**Usage limits**: The upper limit of the amount that can be used in a certain period of time. If you hit the limit, you have no choice but to wait until time passes.

### Hit the limit and work stopped

While making games, I hit the usage limit many times. I wanted to continue, but I had no choice but to wait. **It was frustrating that my work would come to a halt.**

So, **I asked Claude how to save on usage and gradually adjusted my methods.** When I had it analyze the records of my past work, the cause became clear.

**Bomb Valley**  
・I had stacked 45 requests into a single conversation  
・Every time I tested, the 'thinker' role (a higher-end model) would take screenshots of the screen to verify it itself  
・As a result, the conversation ballooned to **about 780,000 tokens** and hit the limit

(Tokens are the unit for the amount of text the AI reads. Think of it as 'conversation length' here)

**BULLET TIME**  
・The conversation for the 'thinker' role stayed within about 200,000 tokens  
・However, I was reusing **just one 'worker' role (a different AI responsible for implementation) 12 times**  
・The conversation for the worker role had ballooned to **about 690,000 tokens**

**The Last School**  
・I broke the work down into small pieces and mechanically repeated 'implementation -> review' each time  
・**The 'reviewer' role hit the limit, and the review failed** (This is a continuation of Pitfall 4 from last time)

All of these were failures where 'each individual instance was no big deal, but they piled up and expanded.'

### What I am doing now (5 points)

**1. Separate the thinker role from the creator role**  
I leave design and reviews to the higher-end model, and implementation to the lighter model. I don't do reviews every time, only for parts with significant impact.

**2. Call a new worker role for each task**  
If you reuse the same worker role, that worker's conversation gets longer and longer. Once one task is finished, I ask a new worker role for the next one.

**3. Reduce screen captures**  
Screen images are much heavier than text. I have the AI verify the game state with text instead of images. I leave testing to the worker role and have it return results briefly as just 'OK/NG + cause'.

**4. Move to a new conversation at break points**  
When a conversation exceeds about 200,000 tokens, I move to a new conversation at a Phase break. Since I have the records written in Chapter 2, I can continue from where I left off even in a new conversation.

**5. Don't stop for minor things**  
It's the same as the 'batch reporting' in Chapter 2. The number of exchanges themselves decreases.

### How to make requests

> 'Leave testing to a separate worker role, and report the results briefly as just 'OK/NG + cause'. Only take screenshots when it's necessary to check the appearance.'

> 'When this conversation gets long, please suggest moving to a new conversation at a Phase break.'

## Conclusion

What all three stories have in common is **clearly writing down the boundary that 'I am the one who decides, and the AI is the one who does the work' at the beginning.**

・What to make, what not to include -> Write in the setting documentation  
・When to stop, what to report -> Write in the request instructions  
・How much to use -> Decide on roles and break points

By writing down the boundaries, the AI can proceed without hesitation, and I can focus on 'playing,' 'choosing,' and 'deciding'.

Next time, I plan to write about **the pitfalls of browser games**. I will summarize the issues I encountered when creating games playable in a browser, such as how they look when holding a smartphone vertically and the fact that sound won't play unless you tap the screen first.

At the AI Game Lab, I share game introductions and the development process.

・X: https://x.com/AIGameLabJP  
・YouTube: https://www.youtube.com/@AIGameLabJP-q9s  
・Play games: https://fish-suika.github.io/games/