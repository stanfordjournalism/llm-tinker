# LLM Tinker

Basics on how to set up a local coding environment to use an [open weights](https://opensource.org/ai/open-weights) model for data classification and other tasks.

Work through the notebooks in order listed below if you're new to this topic.

> IMPORTANT: Before you start, make sure to follow the setup instructions below.

- [llm_tinker.ipynb](llm_tinker.ipynb): Basic setup/usage of Ollama + LangChain in Jupyter, and some important notes.
- [classify_trump_tweets.ipynb](classify_trump_tweets.ipynb): A Jupyter Notebook that demonstrates how to use Ollama with LangChain to classify, or label, tweets by Trump. The notebook demonstrates how to identify tweets by type (text-only, media-only, or both). Guidance on how to refine and perform additional classification tasks are provided at the end of the notebook.
- [classify_trump_tweets_for_export.ipynb](classify_trump_tweets_for_export.ipynb): Similar to [classify_trump_tweets.ipynb](classify_trump_tweets.ipynb), but illustrates how to add classification as a new DataFrame column and then  export the results to a CSV file. This notebook is useful if you want to save the classification results for downstream evaluation.
- [eval_tweet_classification.ipynb](eval_tweet_classification.ipynb): A Jupyter Notebook that demonstrates how to evaluate the performance of a classification model using Precision, Recall, and F1 Score metrics. The notebook uses the results from the [classify_trump_tweets_for_export.ipynb](classify_trump_tweets_for_export.ipynb) notebook to evaluate the classification model's performance on [trump_tweets_sample_labeled_with_predictions.csv](trump_tweets_sample_labeled_with_predictions.csv).

## Setup

### Install Ollama

Install [Ollama](https://github.com/ollama/ollama?tab=readme-ov-file#ollama), a tool for installing and running open weights models locally.

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

