# Briefing Document: Optimizing Claude Code Usage Through Manual Model Selection

**Main Topics and Key Ideas:**

This document examines the key aspects of using Claude Code, focusing on its default model selection behavior and strategies for optimizing cost and efficiency.

**1. Drawbacks of Claude Code's Default Settings:**

* **Lack of intelligent model selection by default:** Claude Code always directs requests through its most powerful and expensive model—Opus 4. As noted, "by default, Claude code always routes your request through Anthropic's most powerful model, Opus 4." This occurs regardless of the request's complexity.
* **High cost of Opus 4:** Opus 4 is five times more expensive than Sonnet 4. "Opus 4 is five times more costly than Sonnet 4." This leads to significant token overspending and reaching usage limits quickly.
* **Reactive model switching:** Claude Code only switches to Sonnet 4 when "your usage approaches 20% of your allocated quota." This switch is not strategic but merely reactive, occurring when the user is "running out of capacity." This switching threshold has changed (from 100% to 50%, and then to 20%), indicating Anthropic's attempts to find a balance.
* **Comparison with other tools:** Unlike Claude Code, "other tools, such as Cursor, offer intelligent model switching by default," optimizing performance and cost.

**2. Demonstration of Default Settings' Inefficiency:**

* An experiment conducted with a simple query "what is 1 + 1" showed a significant cost difference:
    * Using Opus 4 (default): 25 cents.
    * Using Sonnet 4 (manual selection): 5 cents.
* **Key takeaway:** "there is no added value in using Opus 4 for this type of task. The answer is the same, and the complexity is minimal." This highlights that an "Opus 4 run is about five times more expensive than a Sonnet 4 run" but does not provide better results for simple tasks.

**3. Importance of Manual Model Selection:**

* **Cost optimization:** Manual model selection allows you to "get more from your usage" and "avoid wasting tokens."
* **Matching the model to the task:** It allows you to use the "right level of performance for your task without burning tokens unnecessarily."

**4. How to Choose a Model Effectively:**

* **General rule:**
    * **Opus 4:** Use for tasks requiring "reasoning, problem-solving, or anything that would make you stop and think." Examples: complex algorithm design, debugging difficult trace issues, architectural planning, code optimization, significant refactoring.
    * **Sonnet 4 (or older models):** Use for more "procedural" tasks where the model just needs to "follow clear instructions." Examples: simple implementation, code generation from a clear plan, writing documentation and comments, fixing minor syntax and formatting errors.
* **The paradoxical effect of powerful models:** "Ironically, using a more powerful model does not always mean better results." For simple tasks, Opus 4 might "over-analyze the request," looking for depth that isn't there, which can lead to "overly complex, overly abstract, or even just plain wrong solutions." A lighter model like Sonnet 4 "will give you cleaner, more direct answers."

**5. Common Concerns and Strategies to Address Them:**

* **"This adds an extra step to my workflow":** It's a trade-off: "you are trading a bit of your time to save a significant number of tokens." If you frequently hit your limits, manual selection is worth it.
* **"Sonnet 4 doesn't understand my codebase as well as Opus 4":** While Opus 4 is better at handling complex logic and large codebases, Sonnet 4 can still be used effectively with a few strategies:
    * **Thinking mode:** Prompt Sonnet 4 to enter "thinking mode" by literally typing "think hard" in the prompt. This encourages the model to "think through the problem more thoroughly."
    * **More precise model guidance:** Be specific in your requests. Specify files/functions to focus on, and provide examples to follow. Structure requests around "one clearly defined and independent part of the codebase."
    * **Hybrid approach: Opus 4 for planning, Sonnet 4 for execution:**
        * **Planning with Opus 4:** Use Opus 4 for complex reasoning, such as understanding the codebase, designing system architecture, creating an implementation plan, developing a testing strategy, identifying edge cases, and compiling a task list.
        * **Execution with Sonnet 4:** For each item in the plan, switch to a new chat with Sonnet 4, copy the relevant context (implementation plan, system design, specific task), and use Sonnet 4 to perform that part of the work. Once completed, clear the context and repeat for the next task. This approach "gives you the best of both worlds."

**Key Conclusions:**

* The current default behavior of Claude Code leads to significant and unnecessary token costs due to the constant use of the expensive Opus 4 model, even for simple tasks.
* Anthropic will likely introduce a more intelligent model selection system in the future, but for now, this feature is absent.
* Active manual model selection (Opus 4 for complex reasoning, Sonnet 4 for procedural tasks) is the best way to optimize workflow, save costs, and get the most out of Claude Code.
* Even for complex tasks, Sonnet 4 can be used effectively through strategies like thinking mode, more precise instructions, and a hybrid approach with Opus 4 for planning.