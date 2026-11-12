# Niva AI Assistant

<p align="center">
  <strong>An AI-powered desktop assistant for voice interaction, productivity and Windows automation</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/AI-Google%20Gemini-8E75B2?style=for-the-badge" alt="Google Gemini" />
  <img src="https://img.shields.io/badge/Platform-Windows-0078D4?style=for-the-badge&logo=windows&logoColor=white" alt="Windows" />
  <img src="https://img.shields.io/badge/Interface-Voice%20%26%20Desktop-166534?style=for-the-badge" alt="Voice and desktop" />
</p>

**Niva** is a Python-based personal desktop assistant developed by **GFC (Ganraj Fruit Company)**. The project combines a Google Gemini conversational engine with voice input/output, desktop automation, document processing and productivity workflows.

The current repository contains a single main application script, `up.py`. This README documents the implementation visible in that file and distinguishes working code paths from features that may require external accounts, credentials, compatible hardware or additional configuration.

---

## Contents

- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [How Niva Works](#how-niva-works)
- [Repository Structure](#repository-structure)
- [System Requirements](#system-requirements)
- [Installation](#installation)
- [Configuration and API Credentials](#configuration-and-api-credentials)
- [Run Niva](#run-niva)
- [Voice and Keyboard Controls](#voice-and-keyboard-controls)
- [Feature Guide](#feature-guide)
- [External Services and Permissions](#external-services-and-permissions)
- [Security Considerations](#security-considerations)
- [Troubleshooting](#troubleshooting)
- [Development Notes](#development-notes)
- [Roadmap](#roadmap)
- [Credits](#credits)

---

## Overview

Niva is designed to help users interact with their Windows computer through typed or voice-driven commands. It can route general questions to Gemini and execute selected local workflows through Python libraries and Windows desktop interfaces.

### Project goals

- Make common desktop tasks easier to initiate using natural language.
- Assist with spreadsheets, documents, invoices and routine data-entry workflows.
- Provide spoken responses and voice-command interaction.
- Connect AI reasoning with selected local computer actions.
- Bring communication and productivity workflows into one assistant.

## Features

The following capabilities are represented by functions and command handlers in the current `up.py` source.

### AI conversation and live search
- Google Gemini integration using the Google Gen AI Python SDK.
- Chat session configured with the `gemini-2.5-flash` model.
- Google Search tool configuration for requests that need current information.
- Retry handling for selected temporary API failures.
- Conversation context maintained through a Gemini chat object.

### Voice interaction
- Microphone input using SpeechRecognition and sounddevice-related audio support.
- Text-to-speech output using Microsoft Edge TTS.
- Audio playback through Pygame.
- Keyboard controls to start, stop and interrupt interaction.
- Language-sensitive speech handling in the current implementation.

### Windows desktop automation
- Open websites, applications, folders and files.
- Keyboard and mouse automation through PyAutoGUI and the keyboard package.
- Take screenshots.
- Lock the Windows workstation.
- Close selected applications.
- Execute generated local code files after user confirmation.

### Excel and CSV productivity
- Read Excel and CSV data with Pandas and OpenPyXL.
- Enter spreadsheet rows into an already-open desktop form using keyboard automation.
- Create and format Excel workbooks.
- Save notes to a spreadsheet.
- Generate spreadsheet-based lead lists from web research.

**Important:** Automated typing interacts with the currently focused application. Review the selected spreadsheet and target form before starting, and do not use this feature with sensitive or unverified data.

### Documents and invoices
- Read selected documents and send their contents to Gemini for analysis.
- Generate PDF invoices using the FPDF library.
- Create and open generated code or text output in a local editor workflow.

### Email workflows
- SMTP-based email sending.
- IMAP-based inbox access and email reading.
- Email parsing and header decoding.
- AI-assisted extraction of recipient, subject and message details.

Email functionality requires valid provider settings and may require an app password or OAuth-based authentication, depending on the email provider.

### WhatsApp workflows
- WhatsApp automation through PyWhatKit and browser interaction.
- Send text messages and selected local files using supported command flows.
- Extract message and recipient details from natural-language instructions.

WhatsApp Web must be available and authenticated in the browser. Browser automation can be affected by WhatsApp Web changes, network conditions and account security checks.

### Camera and image analysis
- Camera access through OpenCV.
- Image processing through Pillow.
- Camera-based visual input can be passed into the AI analysis workflow.

### Web research and data extraction
- Web requests with Requests.
- HTML parsing with BeautifulSoup.
- Wikipedia lookups.
- Search-result and lead-data workflows.
- Export selected research results to Excel.

---

## Technology Stack

| Area | Libraries / Services | Purpose |
|---|---|---|
| Core language | Python 3 | Application logic and automation |
| AI engine | Google Gen AI SDK | Gemini chat and AI responses |
| AI model | Gemini 2.5 Flash | Configured conversational model |
| Search | Gemini Google Search tool | Search-enabled AI requests |
| Speech recognition | SpeechRecognition, sounddevice | Voice input and audio capture |
| Text to speech | edge-tts | Spoken assistant responses |
| Audio playback | Pygame | Play generated speech audio |
| Desktop automation | PyAutoGUI, keyboard | Mouse and keyboard actions |
| Data analysis | Pandas, NumPy | Spreadsheet and data processing |
| Excel | OpenPyXL | Workbook creation and formatting |
| PDF | FPDF / fpdf2 | Invoice generation |
| Web requests | Requests | HTTP requests |
| HTML parsing | BeautifulSoup | Web page data extraction |
| Computer vision | OpenCV, Pillow | Camera and image handling |
| Email | smtplib, imaplib, email | Email sending and inbox processing |
| Desktop UI | Tkinter | File selection dialogs |
| Other integrations | Wikipedia, PyJokes, PyWhatKit | Information, entertainment and web actions |
| Windows integration | msvcrt, ctypes, subprocess, os | Keyboard input and operating-system actions |

The Python standard library is used for file handling, JSON, threading, date/time, regular expressions, browser launching, process control and email protocols.

---

## How Niva Works

1. The application starts and initializes the Gemini client, audio components and assistant state.
2. The user enters a command through the supported input flow.
3. The command handler checks whether it matches a built-in local automation.
4. If a local handler matches, Niva performs that workflow using the relevant Python library or Windows interface.
5. Otherwise, the prompt is sent to Gemini.
6. The response is printed and can be spoken through Edge TTS and Pygame.
7. Selected generated files can be opened locally; execution is handled through a separate confirmation flow.

### High-level architecture

```text
                 User
                  |
          Voice / Keyboard Input
                  |
                  v
          Niva Python Application
                  |
          Command Classification
             /          \
            /            \
           v              v
     Local Actions     Gemini Client
           |              |
           v              v
    Windows / Files    AI Response
    Excel / Email      Search-enabled
    WhatsApp / Camera       |
           |                |
           +-------+--------+
                   |
                   v
          Text / Voice Output
```

---

## Repository Structure

The current default branch contains these files:

```text
Niva-AI-Assistant/
│
├── README.md    # Project overview, setup and developer documentation
└── up.py        # Main Niva desktop assistant application
```

There is currently no `requirements.txt`, `pyproject.toml` or separate configuration module in the inspected repository tree. Dependencies and configuration instructions are therefore documented below based on imports and settings in `up.py`.

---

## System Requirements

### Supported environment

The current source is Windows-oriented. It imports and uses Windows-specific modules and commands, including `msvcrt`, `ctypes.windll`, `os.startfile` and `cmd.exe`.

| Requirement | Details |
|---|---|
| Operating system | Windows 10 or Windows 11 recommended |
| Python | Python 3.10 or later recommended |
| Internet | Required for Gemini, Edge TTS and online integrations |
| Microphone | Required for voice input |
| Speakers / headphones | Required for spoken responses |
| Camera | Optional; required for camera workflows |
| Google AI API key | Required for Gemini features |
| Email account credentials | Required only for email features |
| WhatsApp Web session | Required only for WhatsApp workflows |
| MySQL / database | Not used by the current inspected script |

Python 3.10+ is a recommended setup target, not a version constraint declared by the repository.

---

## Installation

### 1. Install Python

Download and install Python for Windows:

- https://www.python.org/downloads/windows/

During setup, enable **Add Python to PATH**.

Verify the installation in PowerShell:

```powershell
python --version
python -m pip --version
```

### 2. Clone the repository

```powershell
git clone https://github.com/gfcexpert/Niva-AI-Assistant.git
cd Niva-AI-Assistant
```

### 3. Create a virtual environment

```powershell
python -m venv .venv
```

Activate it:

```powershell
.\.venv\Scripts\Activate.ps1
```

If PowerShell blocks script activation, use Command Prompt:

```cmd
.venv\Scripts\activate.bat
```

### 4. Upgrade pip

```powershell
python -m pip install --upgrade pip
```

### 5. Install the Python dependencies

The repository does not currently include a dependency lockfile or `requirements.txt`. Install the third-party packages imported by the current application:

```powershell
python -m pip install google-genai edge-tts pygame SpeechRecognition sounddevice numpy pandas openpyxl keyboard requests beautifulsoup4 opencv-python Pillow wikipedia pyjokes pywhatkit pyautogui fpdf2
```

If audio packages fail to install, check that the Python version and architecture are supported by the package and install any required Windows audio components.

### 6. Configure API credentials

Niva requires a valid Google Gemini API key. See [Configuration and API Credentials](#configuration-and-api-credentials) before running the application.

### 7. Start the application

```powershell
python up.py
```

---

## Configuration and API Credentials

### Google Gemini

The current source creates a Google Gen AI client and configures the `gemini-2.5-flash` model. The API key is currently assigned directly in `up.py` as a placeholder.

1. Create or access a Google AI Studio API key: https://aistudio.google.com/apikey
2. Open `up.py`.
3. Replace the placeholder key with your own valid key for local testing.
4. Keep the key private and never commit a real key to GitHub.

**Recommended improvement:** Move the key to an environment variable such as `GOOGLE_API_KEY` and load it with `os.getenv()`. The current script does not yet load this setting from a `.env` file.

### Email configuration

The current source contains sender-account settings directly in the Python file. Before using email features:

- Remove any exposed credentials from the source.
- Revoke and rotate any password or app password that has ever been committed to a public repository.
- Configure credentials securely through environment variables or a dedicated secrets manager.
- Prefer OAuth or provider-supported app-password authentication.
- Never commit mailbox passwords, access tokens or private email data.

### Other integrations

- **Edge TTS:** Requires an internet connection to generate speech.
- **WhatsApp:** Requires an authenticated WhatsApp Web browser session.
- **Camera:** Requires camera permission and a working camera device.
- **Web research:** Requires internet access.
- **Excel and PDF:** Require the relevant Python packages to be installed.

---

## Run Niva

From the repository directory, with the virtual environment activated:

```powershell
python up.py
```

The application runs as a desktop/console process. Keep the console open while using Niva. Use the configured keyboard controls to interact with the microphone and interrupt speech.

To stop the application, use the supported exit command or terminate the process from its console.

---

## Voice and Keyboard Controls

The startup message in the current source advertises these controls:

| Key | Action |
|---|---|
| `Alt` | Start microphone input |
| `Ctrl` | Stop microphone input |
| `Esc` | Interrupt Niva's current audio playback |

The exact behavior depends on the active input-listener flow and the Windows keyboard state.

---

## Feature Guide

| Workflow | Example request |
|---|---|
| Ask the AI | “Explain how an export invoice works.” |
| Open a website | “Open GitHub.” |
| Create an invoice | “Create an invoice for this order.” |
| Excel data entry | “Fill the form using this Excel file.” |
| Debug a code file | “Check and fix this Python file.” |
| Analyze a document | “Read this PDF and summarize the key points.” |
| Create a lead spreadsheet | “Find fruit importers in Dubai and create an Excel sheet.” |
| Email | “Draft an email to this contact.” |
| WhatsApp | “Send this message on WhatsApp.” |
| Camera analysis | “Look at this using the camera.” |
| Screenshot | “Take a screenshot.” |
| Save a note | “Save this note to Excel.” |

These are illustrative examples. Available actions depend on the command matching logic, external services, credentials and local desktop state.

---

## External Services and Permissions

| Service / Resource | Why it is needed |
|---|---|
| Google AI Studio / Gemini API | AI responses and search-enabled requests |
| Microsoft Edge TTS service | Online text-to-speech generation |
| WhatsApp Web | Browser-based messaging workflows |
| Email provider | SMTP sending and IMAP inbox access |
| Internet connection | AI, speech and web research |
| Microphone | Voice capture |
| Camera | Visual analysis |
| Local file access | Spreadsheet, document and invoice workflows |
| Windows accessibility | Keyboard, mouse, application and workstation controls |

Grant only the permissions needed for the workflows you intend to use.

---

## Security Considerations

Niva can interact with local files, keyboard input, mouse controls, email accounts and browser sessions. Use it carefully.

1. **Rotate exposed credentials:** The current repository source contains credential-like values. Treat any real credential committed to a public repository as compromised. Revoke and replace it immediately.
2. **Use environment variables:** Do not store API keys, email passwords or tokens in source code.
3. **Review automation targets:** Confirm the active window and selected file before running automated data entry.
4. **Protect private files:** Do not send confidential documents, personal data or business records to an AI service unless you are authorised to do so.
5. **Confirm outgoing actions:** Review recipients, message content, attachments and invoice details before sending or sharing.
6. **Be careful with generated code:** Inspect generated files before execution. Never run code you do not understand or trust.
7. **Limit permissions:** Run Niva with a standard user account instead of administrator privileges unless a specific task requires otherwise.
8. **Keep dependencies updated:** Install packages from trusted sources and review updates before adopting them.

This project documentation is not a security audit. Review the implementation before using Niva with sensitive business or personal information.

---

## Troubleshooting

| Issue | Suggested checks |
|---|---|
| `python` is not recognized | Reinstall Python with PATH enabled, then reopen PowerShell |
| ModuleNotFoundError | Activate `.venv` and install the missing package |
| Gemini authentication error | Verify the API key, API access and model availability |
| Gemini quota or server error | Check API quota, billing settings and service status |
| Microphone not detected | Check Windows microphone permissions and the selected input device |
| No spoken output | Check internet access, Edge TTS connectivity and Pygame audio output |
| Pygame or audio initialization error | Check audio drivers and package compatibility |
| Camera unavailable | Check Windows camera permissions and whether another application is using it |
| Excel file error | Verify the file format and install Pandas / OpenPyXL |
| PDF generation error | Verify the FPDF package installation |
| WhatsApp action does not complete | Sign in to WhatsApp Web and check browser state |
| Email authentication fails | Check provider security settings and use supported authentication |
| Windows command fails | Run on a supported Windows environment and check file/application paths |

---

## Development Notes

### Current implementation

- Main application entry point: `up.py`.
- Main execution function: `main()`.
- AI client: Google Gen AI SDK.
- Configured model: `gemini-2.5-flash`.
- Desktop automation is implemented directly in the main Python script.
- Dependencies are imported directly; no dependency manifest is currently committed.

### Recommended project improvements

- [ ] Add a pinned `requirements.txt`.
- [ ] Move API and email credentials into environment variables.
- [ ] Split the monolithic script into AI, voice, automation, email and file-processing modules.
- [ ] Add structured logging and consistent error handling.
- [ ] Add confirmation prompts for destructive or externally visible actions.
- [ ] Add automated tests for command routing and utility functions.
- [ ] Add a configuration example file with placeholders only.
- [ ] Add a setup script and a documented first-run configuration flow.
- [ ] Add a permission and privacy guide for local automation.
- [ ] Add a cross-platform compatibility layer if Linux or macOS support is planned.

---

## Roadmap

The following items are potential future improvements and are not claims of completed functionality.

- [ ] Modular application architecture.
- [ ] Secure secrets management.
- [ ] Dependency pinning and reproducible installation.
- [ ] Improved voice activity detection and microphone controls.
- [ ] Safer automation with previews and explicit confirmations.
- [ ] Test coverage and continuous integration.
- [ ] Plugin-based integrations for additional productivity tools.
- [ ] User-configurable settings and command preferences.
- [ ] Structured documentation for each automation workflow.

---

## Credits

**Project:** Niva AI Assistant  
**Developer:** **GFC — Ganraj Fruit Company**  
**Repository:** [gfcexpert/Niva-AI-Assistant](https://github.com/gfcexpert/Niva-AI-Assistant)

Niva is an independent AI and desktop automation project built to explore practical ways to combine conversational AI, voice interaction and everyday computer workflows.

<p align="center">
  <strong>NIVA AI</strong><br>
  <em>Think Smarter. Work Faster. Automate Better.</em><br>
  <strong>Developed by GFC — Ganraj Fruit Company</strong>
</p>
