# Vak

Vak is a common configuration and CrewAI helper library designed to be used as a dependency in other projects. It provides a structured way to manage LLM configurations and build LLM instances using dependency injection.

## Installation

### As a Library (Git Dependency)

You can install Vak directly from the git repository. Add this to your `requirements.txt`:

#### Using SSH
```text
git+ssh://git@github.com/your-org/vak.git@main#egg=Vak
```

#### Using HTTPS
```text
git+https://github.com/your-org/vak.git@main#egg=Vak
```

Or install via pip:

```bash
pip install git+ssh://git@github.com/your-org/vak.git
# OR
pip install git+https://github.com/your-org/vak.git
```

### Local Development

You can install Vak locally for development:

```bash
pip install -e .
```

## Usage

### LLM Factory

Vak provides an `LLMContainer` to easily create LLM instances based on configuration. This uses dependency injection to provide pre-configured "creative" and "evaluation" LLMs.

```python
from nikhil.vak.domain.llm_factory.dependency.llm_container import LLMContainer
from pathlib import Path

# Initialize the container
container = LLMContainer()

# Configure the path to your LLM config file
config_path = Path("config/llm_config.yaml")
container.config.llm.yaml_path.from_value(str(config_path))

# 1. Get a Creative LLM
try:
    creative_result = container.creative_llm()
    print(f"Creative Model: {creative_result.model_name}")
    # Use the LLM instance
    # response = creative_result.llm.call(...)
except Exception as e:
    print(f"Error: {e}")

# 2. Get an Evaluation LLM
try:
    evaluation_result = container.evaluation_llm()
    print(f"Evaluation Model: {evaluation_result.model_name}")
except Exception as e:
    print(f"Error: {e}")
```

## Configuration

The LLM configuration is managed via a YAML file. See `src/nikhil/vak/domain/llm_factory/example/config/llm_config.yaml` for a comprehensive example.

The configuration supports:
- **Creative** and **Evaluation** use cases.
- Multiple models per use case (e.g., `phi`, `llama`, `gpt`).
- Detailed parameters (temperature, top_p, etc.).


