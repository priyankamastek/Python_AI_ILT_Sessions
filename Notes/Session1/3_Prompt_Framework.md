1. Open project on terminal, run claude 
This start the claude on terminal within the project.

2. Write a vague prompt: Write some test data.

when a prompt is vague -  generic code, missing data columns, invented column names.

Check the tokens consumed. You understand the cost.

--------------------------------------------------------
# A prompt framework:
 is a reusable checklist of what to put in a prompt, such as goal, context, format and examples. 
 It saves you starting from a blank box and keeps results consistent across a team.
 Anthropic, Microsoft and GitHub each publish guidance.

# A generic prompt framework should have 5 parts:
1. ROLE
2. CONTEXT
3. TASK
4. CONSTRAINT
5. FORMAT

### Refer diagram: Generic Prompt Framwork.png

-------------------------------------------------
There is a framework I use for every engineering prompt I write. It has three parts. I call them the 3 C's - Context, Constraints, and Clarity.

1. C1 ( Context )

Context is the answer to the question: does the LLM know enough about the situation to give a useful response?

## The first layer is role context. 

Tell the LLM who it is. Not because the LLM has an identity crisis, but because the role shapes the tone, depth, and focus of the output.

## Compare these two openings:

"Write a function to clean the listings data."

VS

"You are a senior Python data engineer with expertise in pandas pipelines. Your job is to write a function that cleans raw used-car listings before they reach a Streamlit dashboard."

## The second layer is situational context. 

Tell the LLM what it is working with. Paste in the ticket. Include the acceptance criteria. Mention the Python and pandas versions. Describe the columns. 

In Claude Code, point at the files that matter using an @ reference, for example @pipeline/transforms.py or @tests/test_transforms.py, instead of pasting them.

Example: "follow the pattern in @pipeline/parsers.py, use the shared logger, the DataFrame has these columns" . it writes a function that drops straight into your codebase.

2. C2  ( Constraints )

Constraints are the answer to the question: does the LLM know what it must NOT do, and what boundaries it must stay within?

Constraints come in three forms.
1. Format constraints.
2. Scope constraints.
3. Quality constraints.

## Format Constraints

Format constraints. Tell the LLM exactly how you want the output structured. If you want a function with a specific signature, give the signature. If you want results as JSON, say so. If you want a summary of changes at the end, define its fields.

For example:

"Implement clean_listings(df: pd.DataFrame) -> tuple[pd.DataFrame, pd.DataFrame]. Use type hints and a Google-style docstring. When you finish, report only: files changed, tests run, and the test result."

## Scope constraints. 
Tell the LLM what is in scope and what is out of scope. If you only want changes in pipeline/transforms.py, say so. If it must not add new dependencies, say so. If it should only handle the rules in the ticket and not invent extra validation, say so.

## Quality constraints. Set the bar. 
Tell the LLM what "done" looks like: type hints on every function, tests for every rule, ruff clean, no print statements, no inplace=True. Tell it to flag any acceptance criterion that is ambiguous rather than making an assumption.


3. C3  ( Clarity )

Clarity is the answer to the question: is there any ambiguity in what I am asking for?

Ambiguous instructions produce inconsistent outputs. And inconsistent outputs in a workflow that runs repeatedly means you get a different quality of result every time.

Here is an example of an ambiguous instruction:

"Make the function robust."

What does robust mean? The LLM will decide. Sometimes it wraps everything in try/except Exception. Sometimes it adds input validation nobody asked for. Sometimes it adds retries. You have no control.

Here is the same instruction made clear:

"If price cannot be parsed, do not raise. Move the row to the rejected DataFrame with reject_reason = 'unparseable_price'. If the input DataFrame is missing any of the required columns, raise a ValueError that lists the missing column names. Do not catch bare Exception."

Now there is no ambiguity. The result is the same behaviour every time.


### Refer Diagram: The 3C's Prompt Framework Example.png

----------------------------------------------------------
 # Anthropic (Claude)

Anthropic doesn’t publish a named acronym framework. Its prompting best-practices guide is a set of techniques for clear instructions, effective examples, XML structuring, thinking and agentic systems. 

https://code.claude.com/docs/en/best-practices


