# Single-File Python Starter Template  
**Zero-config dependency management in a single `.py` file**

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/downloads/)
![Dependencies](https://img.shields.io/badge/dependencies-managed%20automatically-success)
![Runs Anywhere](https://img.shields.io/badge/runs%20anywhere-yes-brightgreen)

⚠️ **LICENSE & USAGE NOTICE — READ FIRST**

This repository is **source-available for private technical evaluation and testing only**.

- ❌ No commercial use  
- ❌ No production use  
- ❌ No academic, institutional, or government use  
- ❌ No research, benchmarking, or publication  
- ❌ No redistribution, sublicensing, or derivative works  
- ❌ No independent development based on this code  

All rights remain exclusively with the author.  
Use of this software constitutes acceptance of the terms defined in **LICENSE.txt**.

---

A clean, modern, single-file Python script template that:

- Automatically detects and prompts to install missing dependencies (`requests`, `tomli`, `rich`, `rich-argparse`)
- Uses only built-in modules until dependencies are confirmed present
- Provides beautiful terminal output via `rich`
- Includes proper argument parsing from day one
- Is ready to be used as a standalone tool, CLI utility, or quick prototype

Perfect for small tools, personal scripts, automation helpers, or as a starting point when you want to ship **one file only**.

## ✨ Features

- **Automatic dependency handling** — checks for missing packages and offers one-click install (or shows copy-paste command)
- **--no-install** flag — useful in CI/CD or locked-down environments
- **Rich console output** — colored, formatted, emoji-enhanced terminal experience
- **Safe import strategy** — third-party imports happen *after* dependency check
- **Clear sectioning** — easy to find & replace your business logic
- **MIT licensed** — do whatever you want with it

## 📦 Requirements

- **Python 3.8+**
- Internet connection (only for the first run — if dependencies are missing)

No `requirements.txt`, no `pyproject.toml`, no virtual environment **required** (though still recommended for serious development).

## 🚀 Installation

Just download the file:

### Option 1: wget
```bash
wget https://raw.githubusercontent.com/YOUR-USERNAME/YOUR-REPO/main/single_file_project.py -O mytool.py
```
### Option 2: curl
```bash
curl -o mytool.py https://raw.githubusercontent.com/YOUR-USERNAME/YOUR-REPO/main/single_file_project.py
```
### Option 3: Right-click → Save link as...

That's it — one file.

## 🛠 Usage
 
Normal run (will prompt to install dependencies if needed)
```bash
python mytool.py
```
Skip install prompt (useful in scripts/CI)
```bash
python mytool.py --no-install
```
See available arguments (once rich-argparse is installed)
```bash
python mytool.py --help
```
First run example output (when dependencies are missing):

```text
❌ Error: Missing dependencies required to run this program.
Please install them in your environment by running the following command:

   `/usr/bin/python3 -m pip install "requests>=2.31.0" "tomli>=2.0.0" "rich>=13.0.0" "rich-argparse>=1.0.0"`

⚠️ Warning: Installing packages can pose security risks. Consider using a virtual environment (venv) for isolation.
Would you like to install them now? (y/n):
```

## 📖 Examples

Basic connectivity check (already in the template):
```python
Pythonresponse = requests.get("https://www.google.com")
console.print(f"Successfully connected to Google. Status code: {response.status_code}")
```
Add your own CLI arguments easily:
```Python
# In main()
parser = argparse.ArgumentParser(
    description="My cool tool",
    formatter_class=RichHelpFormatter,  # beautiful --help
)
parser.add_argument("--url", default="https://api.github.com", help="API endpoint")
args = parser.parse_args()
```
## 🗂 Project Structure

Since it's a single-file project, the structure is intentionally minimal:
```text
single_file_project.py      ← everything lives here
├── README.md               ← you're reading it
└── .gitignore              (recommended)
```
---
## ⚙️ How It Works
1. Very early argument parsing — only built-in argparse is used
2. Dependency check — uses importlib.util.find_spec() (no import attempt → no ImportError spam)
3. Smart install suggestion — detects venv vs global, offers --user when appropriate
4. Optional auto-install — interactive prompt (skipped in non-TTY or with --no-install)
5. Delayed third-party imports — rich, requests, tomli are imported only after confirmation

## 🔧 Customization

Change dependencies
Edit this dictionary at the top:

```Python
REQUIRED_DEPENDENCIES = {
    "requests": "requests>=2.31.0",
    "tomli": "tomli>=2.0.0",
    "rich": "rich>=13.0.0",
    "rich-argparse": "rich-argparse>=1.0.0",
    # "click": "click>=8.1.0",         # ← add more here
}
```
Add your logic
Replace or extend the main() function — that's your playground.

Rename the file
Feel free — tool.py, check-sites.py, my-cli.py, etc.

### 🤝 Contributing

Contributions, bug reports, and feature suggestions are welcome!
- Fork the repository
- Create your feature branch (git checkout -b feature/amazing-feature)
- Commit your changes (git commit -m 'Add some amazing feature')
- Push to the branch (git push origin feature/amazing-feature)
- Open a Pull Request

Please make sure your changes keep the single-file philosophy unless there's a very good reason to split it.

📄 License
This project is licensed under the MIT License — see the LICENSE file for details (or just consider the whole content MIT licensed if you haven't added a LICENSE file yet).
