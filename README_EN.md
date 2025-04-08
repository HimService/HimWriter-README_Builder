# HimWriter-README_Builder

[繁體中文](README.md) | [English](README_EN.md)

## Project Overview

**HimWriter-README_Builder** is a tool that leverages the Google Gemini API to automatically generate README.md files. This project aims to assist developers in quickly creating project documentation by allowing users to customize the tone, language, and sections to include, significantly simplifying the README writing process. The tool features a graphical user interface (GUI) that is intuitive and easy to use, making it suitable for all types of software projects.

### Key Features

* **Automatic README.md Generation**: Generates structured README.md files based on project file contents.
* **Multiple Languages and Tones**: Supports various languages (e.g., Traditional Chinese, English) and tones (e.g., formal, technical), adjustable to meet project needs.
* **Gemini Model Selection**: Allows users to choose different Google Gemini models (e.g., `gemini-pro`, `gemini-1.5-flash`) for content generation.
* **Customizable Sections**: Users can specify required sections in the README, such as file structure, installation instructions, etc.
* **Graphical User Interface (GUI)**: Offers a user-friendly GUI for an enhanced operational experience.
* **Automatic Folder Ignoring**: Utilizes the Gemini API to analyze the project directory structure and automatically suggest ignoring non-essential folders like virtual environments or build outputs, improving README accuracy.
* **Error Handling and Retry Mechanism**: Implements error handling for Gemini API quota limits with a retry mechanism to enhance tool stability.

## Installation

### System Requirements

* **Python 3.7 or higher**
* **pip** (Python package management tool)

### Installation Steps

1. **Download the Project**:
    ```bash
    cd HimWriter-README_Builder
    ```

2. **Install Dependencies**:
    Run the following command in the project root directory to install the required Python packages:
    ```bash
    pip install -r requirements.txt
    ```

3. **Set Up Gemini API Key**:
    * Visit [Google AI Studio](https://makersuite.google.com/app/apikey) to obtain a Gemini API key.
    * Open the `config.py` file in the project directory.
    * Replace `API_KEY` with your obtained Gemini API key:
        ```python
        API_KEY = "YOUR_ACTUAL_API_KEY"
        ```

## Usage

1. **Run the Application**:
    Execute the following command in the project root directory to launch the GUI application:
    ```bash
    python main.py
    ```

2. **Configure Parameters**:
    * **Project Path**: Click the "Browse" button or manually enter the root directory path of your project.
    * **Model**: Select the desired Gemini model from the "Model" dropdown menu. Default options include `gemini-pro`, `gemini-1.5-pro`, `gemini-1.5-flash`, `gemini-2.0-flash-thinking-exp-01-21`.
    * **Tone**: Choose the tone for the README from the "Tone" dropdown menu, such as "formal," "casual," "technical," etc. You can also select "other" and enter a custom tone in the field below.
    * **Language**: Select the README language from the "Language" dropdown menu, such as "Traditional Chinese," "English," etc.
    * **Required Sections**: Check the sections you want the README to include, such as "File Structure," "Detailed Installation," "Introduction," "Project Structure," etc. You can also check "Other" and enter additional section names as needed.

3. **Generate README**:
    Click the "Generate" button to start the process. The application will read your project files and call the Gemini API to generate the README content. During generation, the "Execution Status" area will display progress messages, and the "Generated Result" area will show the generated README content (in Markdown format).

4. **Save README**:
    After verifying the README content in the "Generated Result" area, click the "Save" button. Choose the path and filename where you want to save the README (default is `generated/README.md`) to store it locally.

### Configuration Options

In the `config.py` file, you can modify the following options:

* **`MODELS`**: This list defines the available Gemini models. You can add or remove model names as needed.
* **`SUPPORTED_LANGUAGES`**: This list defines the supported README languages. You can add or remove language names as needed.
* **`TONES`**: This list defines the default tone options for the README. You can add or remove tone options as needed.

### Notes

* Ensure the Gemini API key is correctly set before first use.
* The quality of the generated README depends on the Gemini model's capabilities and the project file contents. It’s recommended to review and edit the generated content as necessary.
* Ensure the selected model matches the API-supported model types, or the tool will not function.
* If you encounter a Gemini API quota limit error (HTTP 429), the application will automatically retry, and related messages will appear in the "Execution Status" area. Please be patient or try again later.

## Current Issues

### Export Errors
- If there are issues with the exported README.md, please copy the raw generated content from the GUI and modify it manually. We are currently working on fixing this issue.

## Contribution
If you have suggestions for new features or encounter bugs, please contact us.

## License
Please read the `LICENSE` file.