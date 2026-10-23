# Claude Code's creator says better prompts need just 3 things, so I tested his approach

- 来源: 未知
- 发布时间(UTC): 2026-10-22 11:00:00
- 原文链接: https://www.xda-developers.com/claude-codes-creator-says-better-prompts-need-just-3-things/

----

Title: Claude Code's creator says better prompts need just 3 things, so I tested his approach

URL Source: http://www.xda-developers.com/claude-codes-creator-says-better-prompts-need-just-3-things/

Published Time: 2026-10-22T18:00:21Z

Markdown Content:
[![Image 1: 4](https://static0.xdaimages.com/wordpress%2Fwp-content%2Fauthors%2F67e4210ca43aa-6651085319557-IMG_3196.jpeg?fit=crop&w=90&h=90)](http://www.xda-developers.com/author/mahnoor-faisal/)

Published Oct 22, 2026, 2:00 PM EDT

Mahnoor Faisal is a tech journalist covering AI and productivity tools with bylines at [XDA](https://www.xda-developers.com/author/mahnoor-faisal/), [SlashGear](https://www.slashgear.com/author/mahnoorfaisal/), [MakeUseOf](https://www.makeuseof.com/author/mahnoor-faisal/), [Laptop Mag](https://www.laptopmag.com/author/mahnoor-faisal), and[Android Police](https://www.androidpolice.com/author/mahnoor-faisal/).

She's been writing professionally since she was sixteen, and has since penned hundreds of articles. This includes in-depth coverage of AI tools like NotebookLM to breaking news across the AI space. Her passion for technology started when she received her first iPod Touch (4th generation) on her 8th birthday, and she's been deep in the tech world ever since.

Currently pursuing a degree in computer science, Mahnoor brings both a journalist's eye and a technical foundation to her coverage of how AI is reshaping the way we work and learn.

We've successfully reached the stage where every other person has an opinion on how you should be prompting AI. In the same week, you'll hear one person tell you to [feed as much context as you possibly can into a prompt](https://www.xda-developers.com/dismissed-this-hyped-ai-app-for-months-now-use-it-for-every-claude-chatgpt-prompt/), be vague, and let the LLM figure out the details on its own. Then, you'll come across someone else telling you to do the exact opposite: [keep your prompts short](https://www.xda-developers.com/stripped-my-prompts-down-after-openais-new-guide/), be ridiculously specific about what you want, and leave absolutely nothing up to the AI's interpretation.

That's exactly why a recent post from Boris Cherny, the creator of Claude Code, caught my attention. Rather than sharing some shiny new, elaborate prompting framework or a ridiculously long template you need to follow, he says a good prompt just needs three things.

## Boris Cherny says there's no secret to prompting

### Three tips, no magic formula

*   ![Image 2: Claude Code v2.1.269 startup screen in Terminal after an update](https://static0.xdaimages.com/wordpress/wp-content/uploads/wm/2026/09/claude-code-v2-1-269-startup-screen-in-terminal-after-an-update.jpeg?q=49&fit=contain&w=750&h=422&dpr=2)

*   ![Image 3: Claude Code v2.1.269 startup screen in Terminal after an update](https://static0.xdaimages.com/wordpress/wp-content/uploads/wm/2026/09/claude-code-v2-1-269-startup-screen-in-terminal-after-an-update.jpeg?q=49&fit=contain&w=4617&h=3078&dpr=2)

*   ![Image 4: MacBook Air under orange lamp light showing Claude Code and the Still pomodoro summary](https://static0.xdaimages.com/wordpress/wp-content/uploads/wm/2026/10/macbook-air-under-orange-lamp-light-showing-claude-code-and-the-still-pomodoro-summary.jpeg?q=49&fit=contain&w=4032&h=2688&dpr=2)

*   ![Image 5: Antigravity created a website and Claude Code redesigned it](https://static0.xdaimages.com/wordpress/wp-content/uploads/wm/2026/10/antigravity-vs-claude-code.jpg?q=49&fit=contain&w=4000&h=2252&dpr=2)

*   ![Image 6: iPad with ChatGPT's sidebar open beside the Claude Code page on claude.com](https://static0.xdaimages.com/wordpress/wp-content/uploads/wm/2026/10/ipad-with-chatgpt-s-sidebar-open-beside-the-claude-code-page-on-claude-com.jpeg?q=49&fit=contain&w=4032&h=2688&dpr=2)

*   ![Image 7: claude code open on a laptop screen](https://static0.xdaimages.com/wordpress/wp-content/uploads/wm/2026/08/claude-code-opus-laptop-2.jpg?q=49&fit=contain&w=5228&h=3485&dpr=2)

Once he shared the prompt, users were surprised by just how simple and conversational it was. There were no elaborate instructions, complicated prompting frameworks, or special tricks involved. He was essentially talking to Claude the way you'd talk to a coworker, which led quite a few people to realize they'd been prompting their AI tools in a similar way all along.

The reactions eventually prompted Cherny to elaborate on his approach to prompting, and that's when he explained that there's really no secret to it. According to him, a good prompt comes down to just three things.

Something Anthropic's been pushing a lot lately is [giving users more control over how much time and computational effort a model spends working through a task](https://www.xda-developers.com/changed-one-setting-in-claude-code-token-burn-dropped/), which is referred to as effort. The idea is pretty straightforward: not every task requires the same amount of thinking. You wouldn't necessarily want Claude to spend several minutes reasoning through a simple question, but for something considerably more complicated, giving it more room to think could make a difference. That's essentially what Cherny's second tip boils down to: communicate exactly how much effort you want the AI to put into the task.

## Cherny's own prompt is an almost perfect example of his advice

### He practices (almost) what he preaches

![Image 8: terminal window showing claude code editor with syntax highlighting on a tablet device](https://static0.xdaimages.com/wordpress/wp-content/uploads/wm/2026/05/terminal-window-showing-claude-code-editor-with-syntax-highlighting-on-a-tablet-device.jpg?q=49&fit=crop&w=825&dpr=2)

> The latest acquired Home Depot episode is really amazing. I want you to make an artifact that narrates the entire episode. Make it beautiful and interactive and focus on communicating the nugggets of business wisdom throughout the episode. Make it really good, use lots of tokens and iterate till you're proud of it. Maybe add watercolor illustrations and historical photos throughout, aim for New Yorker or nytimes data viz vibes but better. I think you can use OpenCV for water color images

What's interesting is that he doesn't tell Claude exactly how to build the artifact. He explains what he wants the final result to look like and leaves the finer details up to the model. The second tip is even easier to spot. Cherny explicitly tells Claude to "use lots of tokens" and keep iterating until it's proud of the result. He's essentially telling the model that he wants it to put considerable effort into the task rather than rushing through it.

Now, the third tip is where things get a little interesting. While Cherny does ask Claude to keep iterating until it's satisfied with the result, he doesn't actually give it a concrete way to verify its work. There are no instructions to run tests or check the final artifact against a specific set of requirements. Instead, he's relying on Claude to evaluate and improve the quality of its own output.

After testing his approach out over the past few days, I've realized that there's a lot of truth to what Cherny is saying. Rather than spending ages trying to craft the perfect prompt or following some elaborate framework I came across online, I've been focusing on clearly communicating what I want, how much effort I expect the AI to put in, and how it should check its work. So far, I've found that this simple approach works surprisingly well, regardless of which AI model I'm using.

## The problem with prompting advice is that it doesn't age well

### Prompting advice has a surprisingly short shelf life

![Image 9: Claude models displayed within Claude Code CLI window](https://static0.xdaimages.com/wordpress/wp-content/uploads/wm/2026/07/claude-models-displayed-within-claude-code-cli-window.jpeg?q=49&fit=crop&w=825&dpr=2)

If you've been following the pace of these AI companies since the day OpenAI dropped its first model publicly, you might've noticed that they're showing no signs of slowing down. A new model seems to drop practically every other week (or at least that's what it feels like), and the entire point of these releases is to improve upon what came before them. Naturally, that also means the way we interact with these models is constantly changing.

What worked brilliantly with one model might not necessarily work as well with the next, and prompting advice that was considered gospel just a few months ago might already be outdated. To add to that, every AI provider's LLMs are different. A prompting technique that works wonders with Claude might not necessarily produce the same results with ChatGPT or Gemini, even if you're asking all three models to perform the exact same task.

So, between the constant stream of new model releases and the differences between models from competing AI companies, it's no surprise that everyone's constantly trying to figure out the next big prompting trick.

### These three tips aren't just for Claude

Ultimately, these aren't complicated prompting tricks that depend on a specific model or tool, but rather simple principles that can be applied to just about any AI assistant!