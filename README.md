# Mironova GPT (MVP)

Mironova GPT is a fork of [Private GPT](./README-PRIVATE-GPT.md) with the following changes:

## Pre-requisites

-   Python 3.11 / Pip
    ```bash
    sudo apt update
    sudo apt install python3.11 python3-pip
    ```
-   Virtualenv
    ```bash
    pip install virtualenv
    ```

## Downloading and Installing Ollama

Follow these steps to download and install [Ollama](https://github.com/ollama/ollama):

1. **Install Ollama:**

    ```bash
    curl -fsSL https://ollama.com/install.sh | sh
    ```

    A docker version is also available here: [Ollama Docker Container](https://hub.docker.com/r/ollama/ollama)

2. **Download Models:**

    ```bash
    ollama pull mistral
    ```

    Replace `mistral` with the name of the model you want to download. You can find the available models here: [Ollama Models](https://ollama.com/library)

3. **Get Ollama up and running:**

    ```bash
    ollama run mistral
    ```

    Replace `mistral` with the name of the model you want to run. You can find the available models here: [Ollama Models](https://ollama.com/library)

    Also, you will need to change the model in the [config file](./settings-ollama.yaml) changing the llm_model key.

## PrivateGPT Installation

Follow these steps to install PrivateGPT on Ubuntu:

1. **Clone the Repository:**

    ```bash
    git clone https://github.com/zylon-ai/private-gpt.git
    ```

2. **Navigate to the Project Directory:**

    ```bash
    cd privategpt
    ```

3. **Set Up Environment:**

    Create a virtual environment (optional but recommended):

    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

4. **Install Dependencies:**

    ```bash
    pip install setuptools
    pip install poetry
    poetry run python scripts/setup
    poetry install --extras "ui llms-ollama embeddings-ollama vector-stores-qdrant"
    ```

5. **Run PrivateGPT:**

    ```bash
    PGPT_PROFILES=ollama make run
    ```

    ```

    ```

## Usage

PrivateGPT provides a command-line interface for easy interaction. Here are some examples of how to use it:

-   **Generate Text:**

    ```bash
    python3 privategpt.py --model ollama --length 100 --temperature 0.7
    ```

    Replace `--model` with the desired model (ollama or mistral), `--length` with the desired length of generated text, and `--temperature` with the sampling temperature.

-   **Interactive Mode:**

    ```bash
    python3 privategpt.py --model mistral --interactive
    ```

    This allows you to interactively generate text. Type your prompt and press Enter to see the model's response.

-   **Specify Prompt:**

    ```bash
    python3 privategpt.py --model ollama --prompt "Once upon a time, in a land far, far away"
    ```

-   **Document Ingestion:**

    [Ingestion](https://docs.privategpt.dev/manual/document-management/ingestion)

    Replace the prompt text with your own.

## Additional Notes

-   **Model Customization:**

    You can fine-tune the pre-trained models on your own data for better performance. Refer to the respective documentation for ollama and mistral for instructions on fine-tuning.
