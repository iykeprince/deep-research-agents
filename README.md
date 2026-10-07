# Deep Research

Deep Research is a multi-agent AI research assistant built with Python, Gradio, and the OpenAI Agents SDK. It takes a user query, plans a set of targeted web searches, synthesizes findings into a detailed report, and delivers the result through a simple web interface or email.

## Features

- Multi-step research workflow with dedicated agents for planning, searching, and writing
- Web search-driven investigation using OpenAI Agents and web search tools
- Long-form markdown report generation tailored to the user's question
- Built-in Gradio UI for quick interactive use
- Email delivery of the final report via SMTP
- Optional push fallback when email is disabled

## How it works

The workflow is orchestrated by the research manager:

1. The planner agent creates a list of targeted search queries.
2. The search agent runs those searches and summarizes the results.
3. The writer agent synthesizes the findings into a detailed markdown report.
4. The email agent formats and sends the report by email.

This is implemented in [research_manager.py](research_manager.py), with the agent definitions in [planner_agent.py](planner_agent.py), [search_agent.py](search_agent.py), [writer_agent.py](writer_agent.py), and [email_agent.py](email_agent.py).

## Tech stack

- Python
- Gradio
- OpenAI Agents SDK
- Pydantic
- Python-dotenv
- SMTP email delivery

## Project structure

- [app.py](app.py) — Gradio app entry point
- [simple.py](simple.py) — simplified Gradio version of the app
- [research_manager.py](research_manager.py) — orchestrates the research workflow
- [planner_agent.py](planner_agent.py) — generates search tasks
- [search_agent.py](search_agent.py) — performs and summarizes web searches
- [writer_agent.py](writer_agent.py) — produces the final markdown report
- [email_agent.py](email_agent.py) — sends the report by email
- [messenger.py](messenger.py) — email and push notification helpers
- [style.py](style.py) — UI styling and examples
- [requirements.txt](requirements.txt) — Python dependencies

## Requirements

- Python 3.10+
- An OpenAI API key
- Optional SMTP credentials if you want the email workflow enabled

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/deep-research-agents.git
   cd deep-research-agents
   ```

2. Create and activate a virtual environment:

   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file in the project root with the required environment variables:

   ```env
   OPENAI_API_KEY=your_openai_api_key
   DEFAULT_MODEL_NAME=gpt-5.4-mini
   HOW_MANY_SEARCHES=5
   USE_EMAIL=true

   EMAIL_ADDRESS=you@example.com
   EMAIL_SMTP_SERVER=smtp.example.com
   EMAIL_APP_PASSWORD=your_app_password

   PUSHOVER_USER=your_pushover_user
   PUSHOVER_TOKEN=your_pushover_token
   ```

   If you do not want to send email, set `USE_EMAIL=false`.

## Running the app

Start the Gradio interface:

```bash
python app.py
```

Then open the local Gradio URL that appears in the terminal.

## Example usage

Enter a research question such as:

- "What are the most important trends in AI agents in 2026?"
- "Compare the leading open-source LLM frameworks"
- "Summarize the latest developments in robotics for healthcare"

The app will plan a set of searches, gather relevant information, produce a long-form report, and send it by email.

## Notes

- This project relies on the OpenAI Agents SDK and web search tooling.
- Email delivery is optional; if disabled, the app falls back to a push-style output mock in the terminal.
- The output quality depends on the model selected in `DEFAULT_MODEL_NAME` and the reliability of web search results.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
