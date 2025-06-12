# Local Python Environment Setup for OpenWebUI

This guide explains how to create and use a local, user-only Python environment for running OpenWebUI on this machine.

## Requirements
- Python 3.11 or newer is **required** for OpenWebUI. (Current system Python is 3.9.6.)
- If you do not have Python 3.11+, install it first (see below).

## 1. Install Python 3.11 (if not present)
- **macOS:**
  - Using Homebrew:
    ```sh
    brew install python@3.11
    ```
  - Or download from https://www.python.org/downloads/

## 2. Create a Local Virtual Environment
From your project directory (this folder):

```sh
python3.11 -m venv .venv
```

If you already created the environment with another Python version, you may need to recreate it with Python 3.11.

## 3. Activate the Environment
- **macOS/Linux:**
  ```sh
  source .venv/bin/activate
  ```
- **Windows:**
  ```sh
  .venv\Scripts\activate
  ```

---

## Local Python 3.11 & SSL Build Notes

- **System Python was too old (3.9.6).**
- **Homebrew was not available.**
- **Manual Python 3.11 build:**
  - Initial build lacked SSL support (pip failed to connect to PyPI).
  - Downloading OpenSSL from openssl.org failed due to a redirect (HTML file received).
  - Correct OpenSSL source was obtained from the GitHub release link.
  - OpenSSL 1.1.1w was built and installed locally to `$HOME/.local`.
  - Python 3.11 was rebuilt with `--with-openssl=$HOME/.local` and SSL support worked.
- **Result:** Python 3.11 with SSL is now available for local user, and OpenWebUI can be installed and run in the `.venv`.

These steps are suitable for automation or for AI to follow in similar environments.

## 4. Install OpenWebUI
With the environment activated, run:

```sh
pip install --upgrade pip
pip install open-webui
```

## 5. Run OpenWebUI
With the environment activated, run:

```sh
open-webui serve
```

Then visit http://localhost:8080 in your browser.

## Notes
- Always activate the environment before running OpenWebUI or installing packages.
- If you upgrade Python, recreate the virtual environment.
- For more info, see: https://github.com/open-webui/open-webui
