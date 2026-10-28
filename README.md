# 🤖 AI Agents with Tool Calling – Real Estate Assistant

An AI assistant that uses tools to give exact, data-based answers: it searches property listings, calculates rental yields, and completes multi-step tasks on its own – with safety guardrails.

## Notebook
[Tool_calling_agent.ipynb](Tool_calling_agent.ipynb)

## The problem
LLMs are great with language but unreliable for exact calculations, and they cannot see a company's own data. Tool calling fixes this: the AI decides which tool to use, and Python does the real work.

## What it does
1. **Yield calculator tool** – exact gross and net rental yield calculations
2. **Property search tool** – filters a property table (area, price, bedrooms) from a plain-English question
3. **Tool selection** – the AI picks the right tool for each question, or no tool for small talk
4. **Agent** – completes multi-step tasks on its own, e.g. "Find 2-bed flats in JVC under 1M and tell me which has the best yield" (search → calculate for each → compare)

## Safety guardrails
- **Input validation** inside tools (e.g. price must be positive)
- **Human approval** for risky actions – removal requests are never executed automatically
- **Step limit** – maximum number of tool calls per task
- Safety rules are enforced in code, not only in the prompt

## How it works
1. Tools are normal Python functions with clear descriptions and type hints
2. The functions are passed to Gemini as tools
3. The model decides which tool to call and with which values
4. Python runs the tool, the result goes back to the model, and it writes the final answer

## Tech stack
Python · Google Gemini API (function calling) · pandas · Google Colab

## Related projects
- [Lease Reader](https://github.com/fatemarampurawalaa-sudo/Lease_reader) – live RAG app for lease contracts
- [LLM Practice](https://github.com/fatemarampurawalaa-sudo/LLM-practice) – Gemini API, prompts, structured output, embeddings, RAG
