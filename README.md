# AI Website Summarizer

A small Gradio app that fetches website content and returns a short, friendly summary using a Llama-family model via a Groq/OpenAI-compatible client.

## Features
- Scrapes and extracts main text from a webpage
- Sends content to a chat-capable model (e.g. `llama-3.3-70b-versatile`) for summarization
- Web UI powered by Gradio for quick local testing and demos

## Requirements
- Python 3.10+
- Packages: `gradio`, `openai`, `python-dotenv`, `requests`, `beautifulsoup4`

Install dependencies:

```bash
python -m venv .venv
.venv\Scripts\activate    # Windows
pip install -r requirements.txt
```

If you don't have a `requirements.txt`, install directly:

```bash
pip install gradio openai python-dotenv requests beautifulsoup4
```

## Configuration
Create a `.env` file in the project folder with your API key. This project expects a Groq-compatible endpoint by default. Example:

```
GROQ_API_KEY=your_groq_api_key_here
```

If you want to call OpenAI directly, set `OPENAI_API_KEY` and remove or adjust the `base_url` override in `summarizer.py`.

## Run
Start the Gradio app:

```bash
python app.py
```

The terminal will show a local URL (and a public `share=True` link if enabled) to open the UI.

## Key Files
- `app.py` — Gradio frontend that calls the summarizer.
- `summarizer.py` — Builds the chat request to the model and returns the summary.
- `scraper.py` — Fetches and extracts website text for summarization.

## Usage
Open the Gradio link shown in the terminal, paste a website URL, and click to generate a short markdown summary.

## Notes
- The default model name in this repo (`llama-3.3-70b-versatile`) is available via Groq — ensure your API key and `base_url` match the provider you use.
- For production use, consider adding input validation, caching, rate limiting, and error handling.

## Contributing
Improvements, bug fixes, and model-switching PRs are welcome.
