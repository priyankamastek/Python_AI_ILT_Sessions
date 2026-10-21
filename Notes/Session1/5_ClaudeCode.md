# What is Claude code?
Claude Code is an agentic coding tool that reads your codebase, edits files, runs commands, and integrates with your development tools. 

Available in your terminal, IDE, desktop app, and browser.

Claude Code is an AI-powered coding assistant that helps you build features, fix bugs, and automate development tasks. It understands your entire codebase and can work across multiple files and tools to get things done.

# Claude Common commands
To check yours, run /model to see the active model and /context to see the window size and what is filling it.

# What is Context Window?
* What it is: 
everything the model can hold at once, measured in tokens, including your prompts, the files it reads, command output and its own replies. A token is roughly three-quarters of a word.

* How big: 
commonly 200K tokens. Some models and plans in Claude Code offer up to 1M, and you can check theirs with /model.

* How to see it: 
/context shows the tokens used, the window size and what is using the space, for example 33.3k of 1M.

* Your pointer: 
 A bigger window doesn't mean you can stop managing context. Quality can still degrade at very high token counts, and you pay for every token in the window on each request.
