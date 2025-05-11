# Telegram Document Search Bot

A fast, indexed Telegram bot for searching exact strings inside text-based documents (DOCX & PDF) in a folder and its subdirectories.  

## Features

- Recursively scans a given folder for:
  - Valid **.docx** packages (skips invalid/old-Office binaries)
  - Text-based **.pdf** files  
- Builds an **index** for rapid “exact match” lookups  
- Real-time progress updates in Telegram chat  
- Restricts use to a configurable list of authorized Telegram user IDs or usernames  
- Closes any open file handles in the working directory tree before and after each search  
- Supports two main commands:
  - `/index` – (Re)build the search index  
  - `/search <exact string>` – Find all files containing that exact phrase  

## Requirements

- Python 3.10+  
- Install dependencies via:
  ```bash
  pip install -r requirements.txt

 ## Typical dependencies:

- python-telegram-bot

- python-docx

- PyMuPDF (for PDF text extraction)

- whoosh (or similar) for indexing

## Configuration
- Bot Token
Create a bot with @BotFather and set your token in environment or .env:
```bash
export TELEGRAM_BOT_TOKEN="123456:ABC-DEF…"

- Authorized Users
In your environment or config file, list allowed Telegram user IDs or usernames:
```bash
export TG_ALLOWED_USERS="alice,bob,123456789"

- Folder to Scan
By default the bot scans ./data/. Override with:
```bash
export DOC_ROOT_PATH="/path/to/your/docs"

## Installation & Running
```bash
git clone https://github.com/yourusername/telegram-doc-search.git
cd telegram-doc-search
pip install -r requirements.txt
export TELEGRAM_BOT_TOKEN="…"
export TG_ALLOWED_USERS="…"
export DOC_ROOT_PATH="/path/to/docs"
python search7.py
