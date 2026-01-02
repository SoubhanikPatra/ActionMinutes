## System Baseline

This project was set up and is developed on:

- Operating System: Ubuntu 24.04 LTS (Noble)
- Architecture: x86_64

The setup instructions assume a clean Ubuntu installation with only
system defaults and Git pre-installed.

## System Preparation

Before installing development tools, the system package index was refreshed
and all existing packages were upgraded using the default Ubuntu repositories.

This ensures compatibility with modern build tools and prevents dependency
conflicts during Python and machine learning library installation.

No system Python packages were modified or replaced as part of this step.

## Python Installation and Management

ActionMinutes uses Python 3.10.13, managed via `pyenv` to ensure:

- Isolation from the system Python (Ubuntu ships with 3.12)
- Compatibility with the latest versions of PyTorch, TensorFlow, and FastAPI
- Reproducibility across different machines

### Steps Taken

1. Installed `pyenv` using the official installation script.
2. Configured the shell (`.bashrc`) to initialize `pyenv` automatically:
   ```bash
   export PYENV_ROOT="$HOME/.pyenv"
   export PATH="$PYENV_ROOT/bin:$PATH"
   eval "$(pyenv init --path)"
   eval "$(pyenv init -)"
   ```
3. Installed python 3.10.13 using pyenv:
   pyenv install 3.10.13
   pyenv global 3.10.13

4. Verified Python version
   python --version

## Backend Virtual Environment

A dedicated Python virtual environment was created inside the backend folder
to isolate project dependencies and prevent conflicts with other projects or
the system Python.

### Steps Taken

1. Moved to the backend directory:
   ```bash
   cd backend

2. Created the virtual environment:
   python -m venv .venv

3. Activated the environment:
   source .venv/bin/activate

4. Upgraded python package management:
   pip install --upgrade pip setuptools wheel

5. Verified the environment python version:
   which python
   python --version

## Backend Framework Setup

The backend of ActionMinutes will be implemented using **FastAPI**, a modern,
high-performance Python web framework suitable for serving APIs and ML models.

### Planned Steps

1. Create a `requirements.txt` file to list all backend dependencies.
2. Install the dependencies inside the virtual environment:
   ```bash
   pip install -r requirements.txt

3. Create a minimal fastAPI app(backend/main.py) as a skeleton:
   from fastapi import FastAPI
   app = FastAPI(title="ActionMinutes API")

4. Run the server locally to verify the environment:
   uvicorn main:app --reload