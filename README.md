# Elara

A simple tool to anonymize LLM prompts.

Uses [urchade/gliner_multi_pii-v1](https://huggingface.co/urchade/gliner_multi_pii-v1) for named entity recognition (NER).

Watch the [demo](https://youtu.be/K7PJqIbQVjE) to see Elara in action.

## Components

- SvelteKit fullstack web app running on port `5173`
- Python webserver to interact with the model running on port `8000`

## Setup

### Run with Docker

To quickly set up and run Elara using Docker, follow these steps:

1. Ensure you have [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/) installed on your system.
2. Use the following command to build and start the services:
```bash
docker compose up -d
```
3. Wait until both services are up and running:
4. The Python API will be available at `http://localhost:8000`.
5. The SvelteKit app will be available at `http://localhost:5173` (check Usage for details).

### Run without Docker

#### Python

First, if you don't have [`uv`](https://github.com/astral-sh/uv) installed on your system, install it with the following commands (`uv` allows for easy package and version management for Python projects):

```bash
# On macOS and Linux.
curl -LsSf https://astral.sh/uv/install.sh | sh
```

```bash
# On Windows.
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Then, start the Python webserver with `uv`:

```bash
cd python && uv run --python 3.12 --with-requirements requirements.txt main.py
```

Wait until you see `INFO:     Application startup complete.` in the terminal before running and using the SvelteKit app (ensures that the model has been loaded and the server is ready to handle requests).

#### SvelteKit

Run the SvelteKit app with `npm`:

```bash
cd sveltekit && npm i && npm run dev
```

## Usage

1. Open the SvelteKit app in your browser at `http://localhost:5173`.
2. Paste/write text into the "ORIGINAL TEXT" textarea.
3. Click the "SUBMIT" button to anonymize the text.
4. Copy the anonymized text, which will appear in the "ANONYMIZED TEXT" card.
5. Paste the anonymized text into an LLM of your choice, and generate a response.
6. Copy the LLM's response and paste it into the "ANONYMIZED LLM RESPONSE" textarea.
7. The "DE-ANONYMIZED TEXT" card will show the de-anonymized version of the LLM's response, which you can copy and use as needed.
8. If you'd like to modify any labels, please add or remove lines from `labels.txt` in the project's root. 
