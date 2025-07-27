# Fastal LangGraph Toolkit

[![CI](https://github.com/FastalGroup/fastal-langgraph-toolkit/actions/workflows/test.yml/badge.svg)](https://github.com/FastalGroup/fastal-langgraph-toolkit/actions/workflows/test.yml)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PyPI version](https://badge.fury.io/py/fastal-langgraph-toolkit.svg)](https://badge.fury.io/py/fastal-langgraph-toolkit)

Common utilities and tools for building LangGraph agents.

## Installation

For development (editable install):
```bash
uv add --editable /path/to/fastal-langgraph-toolkit
```

## Quick Start

```python
from fastal.langgraph.toolkit import ModelFactory
from types import SimpleNamespace

# Create configuration (SimpleNamespace required)
config = SimpleNamespace(
    api_key="your-api-key",
    temperature=0.7
)

# Create LLM
llm = ModelFactory.create_llm("openai", "gpt-4", config)

# Create embeddings
embeddings = ModelFactory.create_embeddings("openai", "text-embedding-3-small", config)

# Check available providers
providers = ModelFactory.get_available_providers()
```

## Configuration

The toolkit requires configuration objects (not dictionaries). Use `SimpleNamespace`:

```python
from types import SimpleNamespace

# For OpenAI
config = SimpleNamespace(
    api_key="sk-...",
    base_url="https://api.openai.com/v1",  # Optional
    temperature=0.7                        # Optional
)

# Environment variables helper
from fastal.langgraph.toolkit.models.config import get_default_config
config = get_default_config("openai")  # Uses OPENAI_API_KEY, etc.
```

## Features

- Multi-provider LLM support (OpenAI, Anthropic, Ollama, Bedrock)
- Multi-provider embeddings support  
- Configuration injection pattern
- Provider availability checking

## License

MIT License