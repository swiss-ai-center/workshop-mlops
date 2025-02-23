# AI Days@HES-SO MLOps Workshop

A simple workshop support to MLOps tools and practices - from a conventional
way to a modern approach of working with ML projects. Website available at
<https://swiss-ai-center.github.io/workshop-mlops/>.

## Overview

The repository is organized into several branches, each fulfilling a specific role:

* `main`: the guide that is continuously deployed
* `code`: the code used to create and train the model referenced in the guide
* `data`: the dataset used to train and evaluate the model
* `extra-data`: the supplementary dataset used for inference and labeling before retraining the model
* `freeze`: a backup of the validated dependencies list which can be used as a fallback in case of breakage in the transitive dependencies tree.

Temporary branches may also exist for ongoing issues and improvements to the guide.

## Development

### Local development with Docker Compose (recommended)

To improve the documentation locally, run
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) with the
following commands:

```sh
# Build the Docker container
docker compose build

# Start the Docker container
docker compose up serve
```

You can now access the local development server at <http://localhost:8000>.

If you make changes to the documentation, the web page should reload.

### Local development with Python

To improve the documentation locally, run
[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) with the
following commands:

```sh
# Install all dependencies for Material for MkDocs
sudo apt install --yes \
    libcairo2-dev \
    libfreetype6-dev \
    libffi-dev \
    libjpeg-dev \
    libpng-dev \
    libz-dev

# Create the virtual environment
python3.12 -m venv .venv

# Activate the virtual environment
source .venv/bin/activate

# Install the Python dependencies
pip install \
    --requirement requirements.txt \
    --requirement requirements-freeze.txt

# Run Material for MkDocs
mkdocs serve
```

You can now access the local development server at <http://localhost:8000>.

If you make changes to the documentation, the web page should reload.

### Format the documentation with Docker Compose (recommended)

To format the Markdown documentation, run
[mdwrap](https://github.com/swiss-ai-center/mdwrap) with the following commands:

```sh
# Build the Docker container
docker compose build

# Start the Docker container
docker compose up format
```

### Format the documentation with Python

To format the Markdown documentation, run
[mdwrap](https://github.com/swiss-ai-center/mdwrap) with the following commands:

```sh
# Create the virtual environment
python3.12 -m venv .venv

# Activate the virtual environment
source .venv/bin/activate

# Install the Python dependencies
pip install \
    --requirement requirements.txt \
    --requirement requirements-all.txt

# Run mdwrap
mdwrap --fmt docs
```
