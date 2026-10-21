# What is LLM?
 - An LLM (Large Language Model) is a type of artificial intelligence trained on vast amounts of text data to understand, summarize, translate, and generate human-like language.
 
# How LLM Works?

 - Tokenization: The model breaks input text into smaller pieces called tokens (words or parts of words).
 - Embeddings: Each token becomes a number code that captures its meaning.

## Example:
When you type "Write a pandas function that removes duplicate car listings and keeps the most recent one", the LLM does not look up a database of pandas solutions. It generates a response token by token, each token being the most statistically likely continuation of everything it has seen so far — including your prompt and its own previous output.

## What LLMs are goot at?
For Python development and data engineering work, LLMs are genuinely strong at:

* Generating structured code — pandas transforms, Streamlit pages, FastAPI endpoints, pytest tests — when given clear context
* Summarising long documents — reading a 30-page data specification or a dealer feed guide and extracting the rules your code must enforce
* Analysing errors and logs — reading a traceback or a pipeline log and identifying the likely root cause and the affected module
Writing and explaining code — generating a groupby with transform, explaining what a SettingWithCopyWarning means, suggesting a fix
* Reasoning through scenarios — given a ticket and acceptance criteria, identifying edge cases a human might miss (nulls, mixed dtypes, UK date formats, timezones)
* Transforming data and code — converting a CSV schema into a Pydantic model, refactoring a notebook into functions, reformatting output for a report
                        

## What LLM cannot What LLMs Cannot Do?
* LLMs have no real-time awareness 
 It does not know which pandas version your project has pinned, what changed on main yesterday, or what failed in last night's pipeline run. You have to tell it — or give it tools that can fetch that information.

* LLMs have no persistent memory by default 

Every new conversation is a blank slate. If you explained your team's logging convention last Tuesday, it has no recollection of that today. This is why tools like Claude Code read project instruction files (such as CLAUDE.md) at the start of each session.
(We will see CLAUDE.md) file in Session 2

* LLMs cannot take actions.

A plain chat LLM can tell you to run pytest. It cannot run it. It can write a parser. It cannot check that the parser works on your real data. The gap between generating output and taking action in the real world is exactly the gap that agentic tools such as Claude Code are designed to close — by giving the model controlled access to your files, terminal and tests, with your approval.

* LLMs hallucinate.

Because they are predicting probable text rather than retrieving verified facts, they can — and do — generate confident, plausible-sounding content that is simply wrong. They may invent a pandas method that does not exist, assume a column name your dataframe does not have, import a package that is not in your requirements.txt, or write a test that passes without actually testing anything.

## How to access LLM?
1. Claude through Claude Code - Terminal or IDE, inside your repo.
2. Claude, through the chat app - Browser or desktop app.
3. Open-source models run locally (e.g. via Ollama) - Runs on your laptop.
4. Other cloud models via API - API key

## Summary:
1. LLM is the Brain the room (reasoning, analysis) power.
2. But on its own, it is completely isolated. It cannot see your repository. It cannot read your test results.
3. It cannot run your pipeline or open a pull request.

An agentic tool like Claude Code changes that. It gives the LLM:

* Eyes -  tools that let it read files, search the codebase, read logs and test output
* Hands -  tools that let it edit files, run commands, run pytest, make commits and prepare pull requests
* Memory  - project instruction files and saved context, so it knows your conventions without being told every time

