---
page_type: sample
languages:
  - python
name: Integrated vectorization (Python)
products:
  - azure
  - azure-cognitive-search
  - azure-openai
description: |
  Using azure-search-documents and the Azure SDK for Python, apply data chunking and vectorization in an indexer pipeline.
urlFragment: integrated-vectors-python
---

# Integrated vectorization using Python (Azure AI Search)  

The Python notebook creates vectorized data on Azure AI Search and runs a series of queries.

The code reads the `data/documents/Posters` files. The current github folder contains only 5 sample files. Output is a combination of human-readable text and embeddings that are pushed into a search index.

## Prerequisites

- An Azure subscription, with [access to Azure OpenAI](https://aka.ms/oai/access).

- Azure AI Search, any version, but make sure search service capacity is sufficient for the workload. We recommend Basic or higher for this demo.

- Azure Storage, with a blob container contaning documents to load, chunk, and vectorize. We recommend the PDFs in the `data/documents` folder.

- A deployment of the `text-embedding-ada-002` embedding model in your Azure OpenAI service. As a naming convention, we name deployments after the model name: "text-embedding-ada-002".

- Python (these instructions were tested with version 3.11.x)


## Run the code

1. Use the `env-sample.txt` as a template for a new `.env` file located in the subfolder containing the notebook. Review the variables to make sure you have values for Azure AI Search and Azure OpenAI.

1. Open `azure-hybrid-search.ipynb` file in Visual Studio Code.

1. Optionally, create a virtual environment so that you can control which package versions are used. Use Ctrl+shift+P to open a command palette. Search for `Python: Create environment`. Select `Venv` to create an environment within the current workspace.

1. Execute the cells one by one, or select **Run** or Shift+Enter.

## Troubleshoot errors

If you get error 429 from Azure OpenAI, it means the resource is over capacity:

- Check the Activity Log of the Azure OpenAI service to see what else might be running.

- Check the Tokens Per Minute (TPM) on the deployed model. On a system that isn't running other jobs, a TPM of 33K or higher should be sufficient to generate vectors for the sample data. You can try a model with more capacity if 429 errors persist.

- Review these articles for information on rate limits: [Understanding rate limits](https://learn.microsoft.com/azure/ai-services/openai/how-to/quota?tabs=rest#understanding-rate-limits) and [A Guide to Azure OpenAI Service's Rate Limits and Monitoring](https://clemenssiebler.com/posts/understanding-azure-openai-rate-limits-monitoring/).
