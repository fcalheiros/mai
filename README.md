# mai - My AI - Command-Line Interface for Gemini/Gemma API

`mai` is a shell script that allows you to interact with the Google Gemini and Gemma APIs directly from the command line. It supports sending text and files (such as images) and receiving both text and files in the response. The script also maintains conversation history, compresses it automatically, and logs all interactions.

## Prerequisites

Before using `mai`, ensure you have the following utilities installed on your system:

- jq — For processing JSON responses  
- curl — For making HTTP requests  
- file — For detecting MIME types of attached files  
- base64 — For encoding and decoding file data  
- gzip — For compressing conversation history  

These tools are available by default on most Linux distributions and macOS.

## Installation

### Linux (Ubuntu/Debian)

sudo apt-get update  
sudo apt-get install jq curl file coreutils gzip

### Linux (Fedora/CentOS)

sudo dnf install jq curl file coreutils gzip

### macOS (Homebrew)

brew install jq

(macOS already includes curl, file, base64, and gzip)

## Obtaining the API Key

To use the Gemini/Gemma API, you need a Google Cloud API key:

1. Visit the Google Cloud Console.  
2. Create or select a project.  
3. Go to “APIs & Services → Credentials”.  
4. Click “Create credentials → API key”.  
5. Copy the generated key.

## Usage

1. Save the script from the `mai` file.  
2. Make it executable:

chmod +x mai

3. Run it for the first time:

./mai

The script will ask for your API key, ask for the model name (e.g., gemini-2.5-flash-lite, gemma-3-27b-it), and create the configuration file at:

$HOME/.local/.mai/mai.conf

4. You may edit the configuration later using:

./mai --config

5. Run the script with text and optionally a file:

./mai "Describe this image:" photo.jpg

Or text only:

./mai "Write a short poem about nature."

Responses are printed to the terminal. Any files returned by the model are saved in:

~/maiout/

## Options

The script supports the following options:

--version  
Shows the script version.

--debug  
Saves the full request and response to ~/maiout/debug.log.

--config  
Opens the configuration file in your default editor.

--list-models  
Fetches and displays all available models from the API.

--logs  
Shows the log file (~/maiout/mai.log).

--new, -n  
Starts a new conversation (clears history).

--help, -h  
Displays the help menu.

## Conversation History

`mai` stores conversation history in:

~/.local/.mai/history.ndjson

When the file reaches 10 MB, it is automatically compressed into:

history.ndjson.gz

The script always sends only the last 20 messages to the model.

## Logging

All interactions are logged to:

~/maiout/mai.log

Each entry includes:

- timestamp  
- prompt  
- model response  
- whether files were returned  

## Script `mai`

The `mai` script is available in the repository under the file named `mai`.

## Contributing

Contributions are welcome. Feel free to open issues or submit pull requests.
