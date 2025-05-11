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

export TG_ALLOWED_USERS="alice,bob,123456789"

- Folder to Scan
By default the bot scans ./data/. Override with:

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

## Usage
/start
Brief welcome message and usage hints.

/index
Triggers a full re-index of all .docx & text-PDF files under DOC_ROOT_PATH.
The bot sends real-time progress (“Indexing file 42/317…”) and a final summary.

/search <exact text>
Finds every file containing that exact substring (case-insensitive).
Returns a list of matching file paths.

## Logging
All actions (scans, indexing, searches, warnings) are logged to:

lua
Copy
bot.log
with timestamps and log levels.

## Implementation Notes
- File Scanning

    -Skips non-.docx or invalid-ZIP docx files

    -Reads PDF files via PyMuPDF, skips binary/empty PDFs

- Indexing

    -Uses Whoosh (or similar) to build an inverted index of file contents

    -Supports exact‐phrase queries for fastest response

- Concurrency & Cleanup

    -Closes any open file handles before/after operations

    -Updates progress in the initiating Telegram message using edit_message_text

## Contributing
1- Fork the repo

2- Create a feature branch

3- Submit a PR with tests and documentation updates

Made with ❤️ and Python
