# LLM Tinker

A basic repo demonstrating how to set up a local LLM environment using Ollama and LangChain.

- [llm_tinker.ipynb](llm_tinker.ipynb): A Jupyter Notebook that demonstrates how to use Ollama with LangChain.
- [label_trump_tweets.ipynb](label_trump_tweets.ipynb): A Jupyter Notebook that demonstrates how to use Ollama with LangChain to classify, or label, tweets by Trump. The notebook demonstrates how to identify tweets by type (text-only, media-only, or both). Your task to perform additional classification of the tweets by building on this notebook, e.g. to classify the tweets by sentiment or topic.

## Setup

### Install Ollama

Install [Ollama](https://github.com/ollama/ollama?tab=readme-ov-file#ollama)

Install an open model using Ollama. For example, to install the
multi-modal 'gemma 3' model, run the following command in the terminal:

> WARNING: This will install a model that is 3.3GB in size, so make sure you have enough disk space.
> You also likely will need at least 8GB of free RAM -- ie amount beyond what you're already using
> -- to run this model. If
> you have less RAM or disk space, you can try a smaller model, such as `gemma3:1b`

```bash
# Install the gemma3 model
ollama pull gemma3
```

If you want to test Ollama and your model in the command line,
you can run the following command:

```bash
ollama run gemma3
```

Then type in a question and hit enter. For example, you can ask:

```bash
What is the capital of France?
```

### Set up a new Python project

Open a terminal shell and run the below commands, one by one:

```bash
# Navigate to your code directory, e.g.
cd ~/code

# Create a new directory for the project
mkdir llm-tinker

# Navigate into the new directory
cd llm-tinker

# Create a new virtual environment
uv init

# Install the required packages
uv add jupyterlab ipykernel pandas langchain_ollama
```

## Working in VS Code

> Below steps are adapated from the [Ollama Quickstart](https://python.langchain.com/docs/how_to/local_llms/#quickstart) and illustrated in `llm_tinker.ipynb`.

Open up the new code project in VS Code.

Then create a new Jupyter Notebook file, e.g. `my-llm-classifier.ipynb`.

Make sure to select the correct Python kernel for the notebook in the upper right corner of the notebook.

Add the following cell to the notebook and execute it.

```python
from langchain_ollama import OllamaLLM
```

If you see a green check mark, then the package is installed correctly.

Here's a simple example of how to use the `OllamaLLM` class to invoke a model:

```python
# Note we're specifying the name of the model we installed with Ollama
llm = OllamaLLM(model="gemma3")
llm.invoke("What is the capital of France?")
```

> See [label_trump_tweets.ipynb](label_trump_tweets.ipynb) for a more advanced example of how to use Ollama with LangChain to classify tweets about Trump, with guidance on additional classification tasks you can perform.

