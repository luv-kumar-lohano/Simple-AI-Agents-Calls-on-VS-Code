# How to make AI Agent Calls on VS Code

This repo contains two cleaned-up Jupyter notebooks that showcase:

- `agents_main.ipynb`: a simple “agentic research” flow using an `agents` module (expects `Agent`, `Runner`, and `trace`).
- `langchain_main.ipynb`: making calls to Google Gemini via LangChain using a free API key from Google AI Studio.

## Quick Start

- Python 3.10+ recommended.
- Create and activate a virtual environment.
- Install dependencies:

```
pip install -r requirements.txt
```

## Environment Variables

- Copy `.env.example` to `.env` and fill in your values. The `.env` file is ignored by Git.

```
cp .env.example .env
```

- Required for `langchain_main.ipynb`:
  - `GOOGLE_API_KEY`: your key from Google AI Studio.

## Notebooks

### `agents_main.ipynb`
- Purpose: Run an agent given a topic and produce a concise summary.
- Requirements: an `agents` module that exposes `Agent`, `Runner`, and `trace`.
- Notes:
  - The notebook uses top‑level `await`. If unsupported, wrap the run in an async function and call it via `asyncio.run(...)`.
  - Ensure `.env` exists if your agent requires API keys.

### `langchain_main.ipynb`
- Purpose: Call Gemini models through LangChain, plus an optional cell to list available models via the REST API.
- Steps:
  1. Optionally run the install cell if needed.
  2. Ensure `.env` contains `GOOGLE_API_KEY`.
  3. Run the setup cell to create the `llm` client.
  4. Run the quick call cell and (optionally) the list‑models cell.

## Pushing to GitHub Without Leaking Secrets

- `.env` is already ignored via `.gitignore`.
- Commit a non‑secret `.env.example` to document required variables.


## Troubleshooting

- ImportError in `agents_main.ipynb`: ensure the `agents` package/module is installed or available in the workspace.
- 401/403 from Gemini: verify `GOOGLE_API_KEY` and model name spelling.
- After installing new packages in a notebook cell, restart the kernel.

