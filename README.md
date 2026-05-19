# 🤖 AI-Powered Company Brochure Generator

Automatically generate polished company brochures using OpenAI's GPT models and web scraping — no manual research required.

## How It Works

This project demonstrates a **multi-step LLM pipeline**:

1. **Scrape** — Fetches all links and page content from a company's website
2. **Filter** — Uses `gpt-5-nano` with structured JSON output to intelligently select only brochure-relevant links (About, Careers, Products, etc.)
3. **Aggregate** — Combines the landing page and all relevant linked pages into a single context
4. **Generate** — Uses `gpt-4.1-mini` to write a polished markdown brochure
5. **Stream** — Outputs the result in real time with a typewriter effect in Jupyter

## Key Concepts Demonstrated

- **Prompt engineering** — System prompts, one-shot examples, and tone control
- **Structured JSON outputs** — Constraining LLM responses to a defined schema
- **Multi-model pipelines** — Using a fast/cheap model for filtering and a capable model for generation
- **Streaming responses** — Real-time token streaming with live notebook display
- **Web scraping** — Custom `scraper` module for fetching page content and links

## Project Structure

```
.
├── ai_brochure_generator.ipynb   # Main notebook
├── scraper.py                    # Web scraping utilities
├── requirements.txt              # Dependencies
├── .env.example                  # Environment variable template
└── README.md
```

## Quickstart

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/ai-brochure-generator.git
cd ai-brochure-generator
```

### 2. Set up your environment

```bash
python -m venv venv
source venv/bin/activate       # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Configure your API key

```bash
cp .env.example .env
# Edit .env and add your OpenAI API key
```

`.env`:
```
OPENAI_API_KEY=sk-proj-...
```

### 4. Run the notebook

```bash
jupyter notebook ai_brochure_generator.ipynb
```

Then run all cells and call `stream_brochure()` with any company:

```python
stream_brochure("Anthropic", "https://anthropic.com")
```

## Requirements

- Python 3.9+
- OpenAI API key with access to `gpt-5-nano` and `gpt-4.1-mini`

## Example Output

Running `stream_brochure("HuggingFace", "https://huggingface.co")` generates a structured markdown brochure covering the company's mission, products, culture, and open roles — in seconds.

## License

MIT
