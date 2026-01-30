# CONTRIBUTING.md

# Contributing

Thanks for your interest in contributing! This project is a local, offline-first node graph editor for organizing D&D campaign knowledge, built with PySide6/Qt and JSON import/export. (See README for features and usage.) 

## Ways to contribute
- Report bugs (UI glitches, crashes, incorrect imports/exports, attachment handling)
- Propose enhancements (UX, performance, new node/edge properties, search improvements)
- Improve docs (README, shortcuts, examples)
- Submit code changes (bug fixes, features, refactors)
- Add test coverage where possible

## Before you start
- Be respectful and follow `CODE_OF_CONDUCT.md`.
- Prefer small, focused pull requests.
- Don’t include real personal data in screenshots, sample JSON, or test fixtures.

## Development setup

### Prerequisites
- Python 3.10+ recommended
- A virtual environment tool (venv, uv, conda, etc.)

### Create a venv and install dependencies
```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

pip install -r requirements.txt
