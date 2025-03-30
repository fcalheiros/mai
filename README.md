# mai - Command-Line Interface for Gemini 2.0 Flash API

`mai` is a shell script that allows you to interact with the Google Gemini 2.0 Flash API directly from the command line. It supports sending text and files (like images) and receiving text and files as a response.

## Prerequisites

Before using `mai`, ensure you have the following utilities installed on your system:

* **jq**: For processing the API's JSON response.
* **base64**: For encoding and decoding files.
* **file**: For determining the MIME type of files.
* **curl**: For making HTTP requests.

### Installation

#### Linux (Ubuntu/Debian)

1.  Open a terminal.
2.  Run the following commands:

    ```bash
    sudo apt-get update
    sudo apt-get install jq base64 file curl
    ```

#### Linux (Fedora/CentOS)

1.  Open a terminal.
2.  Run the following commands:

    ```bash
    sudo dnf install jq coreutils file curl
    ```

#### macOS (Homebrew)

1.  If you don't have Homebrew installed, install it following the instructions at [brew.sh](https://brew.sh/).
2.  Open a terminal.
3.  Run the following command:

    ```bash
    brew install jq
    ```

    (base64 and file are already installed on macOS)

## Obtaining the API Key

To use the Gemini 2.0 Flash API, you'll need a Google Cloud API key. Follow these steps to obtain it:

1.  Go to the [Google Cloud Console](https://console.cloud.google.com/).
2.  Create a new project or select an existing one.
3.  Navigate to "APIs & Services" > "Credentials".
4.  Click "Create credentials" > "API key".
5.  Copy the generated API key.

## Usage

1.  Save the script from the `mai` file.
2.  Make the script executable: `chmod +x mai`.
3.  Run the script for the first time:

    ```bash
    ./mai
    ```

    The script will prompt you for your API key and create the `mai.conf` configuration file.

4.  You can replace the API key and URL by editing the `mai.conf` configuration file located at `$HOME/.local/.mai`.

5.  Run the script with the text and, optionally, the file as arguments:

    ```bash
    ./mai "Describe this image:" image.jpg
    ```

    Or, with text only:

    ```bash
    ./mai "Write a short poem about nature."
    ```

6.  The API response will be displayed in the terminal, and any received files will be saved in the `~/maiout` folder.

### Options

* `--version`: Displays the script version.
* `--debug`: Saves the complete request and API response to `~/maiout/debug.log`.
* `--config`: Opens the configuration file for editing.
* `--log`: Enables logging of API requests and responses to `~/maiout/mai.log`.

## Script `mai`

The `mai` script is available in the [mai](mai) file.

## Contributing

Contributions are welcome! Feel free to submit pull requests or open issues.

