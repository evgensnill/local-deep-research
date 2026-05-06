# Local Deep Research

A powerful local research assistant that performs deep, iterative research using local LLMs and web search — no API keys required for core functionality.

> Fork of [LearningCircuit/local-deep-research](https://github.com/LearningCircuit/local-deep-research)

## Features

- 🔍 **Deep Research**: Iterative search and synthesis across multiple sources
- 🏠 **Local-First**: Runs entirely on your machine using Ollama or other local LLM backends
- 🌐 **Web Search Integration**: Supports multiple search engines (DuckDuckGo, SearXNG, Tavily)
- 📄 **Document Analysis**: Process and research local documents alongside web content
- 🔒 **Privacy-Focused**: Your queries and results stay on your machine
- 📊 **Structured Reports**: Generates well-organized research reports with citations

## Requirements

- Python 3.10+
- [Ollama](https://ollama.ai/) (recommended) or another OpenAI-compatible LLM server
- 8GB+ RAM (16GB recommended for larger models)

## Quick Start

### Installation

```bash
# Clone the repository
git clone https://github.com/your-org/local-deep-research.git
cd local-deep-research

# Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -e .
```

### Basic Usage

```bash
# Start a research session
python -m local_deep_research "What are the latest advances in quantum computing?"

# With custom output directory
python -m local_deep_research "Climate change mitigation strategies" --output ./reports

# Interactive mode
python -m local_deep_research --interactive
```

### Configuration

Copy the example config and customize it:

```bash
cp config/settings.example.toml config/settings.toml
```

Key settings in `config/settings.toml`:

```toml
[llm]
model = "llama3.1:8b"       # Ollama model to use
base_url = "http://localhost:11434"  # Ollama server URL
temperature = 0.1

[search]
engine = "duckduckgo"       # Options: duckduckgo, searxng, tavily
max_results = 10
max_iterations = 3

[output]
format = "markdown"          # Options: markdown, json, html
save_sources = true
```

## Architecture

```
local_deep_research/
├── core/
│   ├── researcher.py       # Main research orchestration
│   ├── query_engine.py     # Query generation and refinement
│   └── synthesizer.py      # Result synthesis and report generation
├── search/
│   ├── base.py             # Abstract search interface
│   ├── duckduckgo.py       # DuckDuckGo backend
│   ├── searxng.py          # SearXNG backend
│   └── tavily.py           # Tavily API backend
├── llm/
│   ├── ollama.py           # Ollama integration
│   └── openai_compat.py    # OpenAI-compatible API support
└── utils/
    ├── text.py             # Text processing utilities
    └── citations.py        # Citation formatting
```

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

- 🐛 [Report a bug](.github/ISSUE_TEMPLATE/bug_report.md)
- 💡 [Request a feature](.github/ISSUE_TEMPLATE/feature_request.md)
- 🔀 [Submit a pull request](.github/PULL_REQUEST_TEMPLATE/first_time_contributor.md)

## License

MIT License — see [LICENSE](LICENSE) for details.

## Acknowledgements

- Original project by [LearningCircuit](https://github.com/LearningCircuit/local-deep-research)
- Built with [LangChain](https://github.com/langchain-ai/langchain) and [Ollama](https://ollama.ai/)
