# Vak

Vak is a common configuration and CrewAI helper library designed to be used as a dependency in other projects. It provides a structured way to manage LLM configurations and build LLM instances using dependency injection.

## Installation

### As a Library (Git Dependency)

You can install Vak directly from the git repository. Add this to your `requirements.txt`:

```text
git+ssh://git@github.com/your-org/vak.git@main#egg=Vak
```

Or install via pip:

```bash
pip install git+ssh://git@github.com/your-org/vak.git
```

### Local Development

You can install Vak locally for development:

```bash
pip install -e .
```

## Usage

### LLM Factory

Vak provides an `LLMFactory` to easily create LLM instances based on configuration.

```python
from nikhil.vak.domain.llm_factory.dependency.llm_container import LLMContainer
from pathlib import Path

# Initialize the container
container = LLMContainer()

# Configure the path to your LLM config file
config_path = Path("config/llm_config.yaml")
container.config.llm.yaml_path.from_value(str(config_path))

# Get the builder
builder = container.llm_builder()

# Build an LLM
result = builder.build_creative()
print(f"Model: {result.model_name}")
```

## Configuration

The LLM configuration is managed via a YAML file. See `config/llm_config_example.yaml` for an example.

## Development

To set up the development environment:

1. Install dependencies:
   ```bash
   pip install -e ".[dev]"
   ```

2. Run tests:
   ```bash
   pytest
   ```
