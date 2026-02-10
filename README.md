# ⠋⠗⠁⠊⠑ Braille Vision

<div align="center">

**A powerful dual-interface tool for converting PDF and image documents to Braille text supporting both English and Arabic languages**

[![Python](https://img.shields.io/badge/Python-3.7%2B-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](#-license)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey.svg)]()

</div>

---

## 📖 Overview

**Braille Vision** is a comprehensive accessibility tool designed to transform PDF documents and images into Braille text format, supporting both English and Arabic languages. This project provides two distinct interfaces to cater to different user preferences:

- **CLI Version** (`braille_cli.py`) - A powerful command-line interface for automation, scripting, and batch processing
- **GUI Version** (`braille_gui.py`) - An intuitive Tkinter-based graphical interface with modern styling, real-time logging, and multi-threaded processing
- **Windows Executable** (`dist/braille_gui.exe`) - Standalone GUI application for Windows users (no Python installation required)

The converter extracts text from PDF files and performs OCR (Optical Character Recognition) on images, then translates the extracted content into Unicode-based Braille characters. It intelligently detects whether the source text is in English, Arabic, or a mixture of both languages, applying the appropriate Braille mapping for each character.

Beyond simple text conversion, the tool exports results in multiple formats:
- **Plain text (TXT)** files containing Braille Unicode characters
- **Normal DOCX** files preserving the original text with proper RTL (right-to-left) formatting for Arabic content
- **Braille DOCX** files containing the translated Braille text for easy sharing and printing

This dual-mode approach makes Braille Vision suitable for:
- Accessibility professionals creating Braille materials
- Educational institutions producing accessible content
- Automation workflows requiring batch conversion
- Individual users seeking quick document conversion
- Organizations supporting visually impaired communities

---

## ✨ Features

### 🎯 Core Conversion Capabilities

- **PDF Text Extraction**: Robust text extraction from multi-page PDF documents using `pdfplumber`
- **Advanced OCR Processing**: Image-to-text conversion using Tesseract OCR with automatic language detection
- **Bilingual Braille Support**: 
  - Complete English Grade 1 Braille mapping (a-z, 0-9, punctuation, symbols)
  - Comprehensive Arabic Braille mapping including all letters, numbers, and diacritics
  - Capital letter indicator support for English text
  - Mixed-language document handling
- **Multi-Format Export**:
  - Plain text (`.txt`) with Braille Unicode characters
  - Microsoft Word (`.docx`) with original text and RTL support for Arabic
  - Microsoft Word (`.docx`) with Braille text
- **Intelligent Language Detection**: Automatic identification of English, Arabic, or mixed content
- **Character-Level Statistics**: Detailed breakdown of Arabic chars, English chars, and total character count

### 🖥️ CLI Version Features

- **Simple Command-Line Interface**: Easy-to-use syntax for quick conversions
- **Flexible Output Naming**: Custom output file paths or automatic naming based on input
- **Progress Indicators**: Real-time feedback during PDF page processing
- **Detailed Error Reporting**: Clear error messages with actionable solutions
- **Scriptable Automation**: Perfect for batch processing and integration into workflows
- **Exit Status Codes**: Proper error codes for scripting and automation

### 🎨 GUI Version Features

- **Modern Dark Theme**: Professionally styled interface with custom color palette
- **Intuitive File Browsing**: Dedicated browse buttons for input files and output folders
- **Flexible Export Options**: Toggle checkboxes for TXT, Normal DOCX, and Braille DOCX exports
- **Real-Time Logging System**: 
  - Color-coded log messages (info, success, warning, error)
  - Scrollable log panel with syntax highlighting
  - Thread-safe logging from background workers
- **Live Statistics Display**: Pill-style indicators showing language breakdown and character counts
- **Multi-Threading Architecture**: Non-blocking UI during conversion to prevent freezing
- **Custom Styled Components**:
  - Hover-effect buttons with smooth transitions
  - Rounded corners and modern aesthetics
  - Tooltips on export options
  - Responsive layout with proper scaling
- **Input Validation**: Automatic file existence checking with user-friendly error dialogs
- **Session State Management**: Remembers output folder selection across operations
- **Visual Feedback**: Button state changes, disabled states during processing

### 🔧 Technical Features

- **Log Callback Mechanism**: Pluggable logging system for both console and GUI
- **Tesseract Auto-Detection**: Automatic location of Tesseract binary on Windows systems
- **Fallback Language Handling**: Graceful degradation from `eng+ara` to `eng` if Arabic pack unavailable
- **Unicode Braille Output**: Standard Unicode Braille patterns (U+2800 to U+28FF)
- **RTL Document Formatting**: Proper bidirectional text support in Word documents
- **Error Recovery**: Comprehensive exception handling with detailed stack traces
- **Cross-Platform Compatibility**: Works on Windows, macOS, and Linux

---

## 📁 Project Structure

```
braille-vision/
│
├── braille_cli.py              # Command-line interface script
├── braille_gui.py              # GUI Application source code (Tkinter)
├── requirements.txt            # Project dependencies
├── README.md                   # Project documentation
│
├── dist/                       # Executable Version
│   └── braille_gui.exe         # Standalone Windows App 
│
├── assets/                     # Project assets
│   └── screenshots/            # Images used in README
│       ├── main_interface.png
│       └── conversion_demo.png
│
└── examples/                   # 🧪 Test Files & Expected Results
    │
    ├── inputs/                 # 1. Source files to test the app
    │   ├── sample_english.pdf      # English text PDF
    │   ├── sample_arabic.pdf       # Arabic text PDF
    │   ├── sample_mixed.pdf        # Mixed (Ar/En) PDF
    │   └── sample_image.png        # Image for OCR testing
    │
    └── outputs/                # 2. Generated results (3 files per input)
        ├── from_english/           # Result of converting sample_english.pdf
        │   ├── sample_english_braille.txt
        │   ├── sample_english_normal.docx
        │   └── sample_english_braille.docx
        │
        ├── from_arabic/            # Result of converting sample_arabic.pdf
        │   ├── sample_arabic_braille.txt
        │   ├── sample_arabic_normal.docx
        │   └── sample_arabic_braille.docx
        │
        ├── from_mixed/             # Result of converting sample_mixed.pdf
        │   ├── sample_mixed_braille.txt
        │   ├── sample_mixed_normal.docx
        │   └── sample_mixed_braille.docx
        │
        └── from_image/             # Result of converting sample_image.png
            ├── sample_image_braille.txt
            ├── sample_image_normal.docx
            └── sample_image_braille.docx

```

### File Descriptions

| File/Folder | Purpose |
|------|---------|
| `braille_cli.py` | Terminal-based converter with argparse interface |
| `braille_gui.py` | Graphical application with Tkinter UI (source code) |
| `dist/braille_gui.exe` | Standalone Windows executable (no Python installation needed) |
| `requirements.txt` | Python package dependencies list |
| `examples/` | Sample input files and screenshots for testing |
| `README.md` | Complete project documentation |

---

## 📦 Requirements

### Python Version
- **Python 3.7 or higher** (tested on 3.7, 3.8, 3.9, 3.10, 3.11)

### Python Packages

The following packages are required and can be installed via pip:

| Package | Version | Purpose |
|---------|---------|---------|
| `pdfplumber` | Latest | PDF text extraction |
| `pytesseract` | Latest | Python wrapper for Tesseract OCR |
| `Pillow` | Latest | Image processing for OCR |
| `python-docx` | Latest | Microsoft Word document creation |

### External Dependencies

**Tesseract OCR** must be installed separately on your system:

#### 🪟 Windows
```bash
# Download installer from:
https://github.com/UB-Mannheim/tesseract/wiki

# Or use Chocolatey:
choco install tesseract

# Add Tesseract to PATH or the GUI will auto-detect common locations:
# C:\Program Files\Tesseract-OCR\tesseract.exe
# C:\Program Files (x86)\Tesseract-OCR\tesseract.exe
```

#### 🍎 macOS
```bash
# Using Homebrew:
brew install tesseract

# With Arabic language pack:
brew install tesseract-lang
```

#### 🐧 Linux (Debian/Ubuntu)
```bash
sudo apt-get update
sudo apt-get install tesseract-ocr tesseract-ocr-ara tesseract-ocr-eng

# For other distributions, use your package manager:
# Fedora/RHEL: sudo dnf install tesseract tesseract-langpack-ara
# Arch: sudo pacman -S tesseract tesseract-data-ara
```

---

## 🚀 Installation Guide

### ⚡ Quick Start (Windows Users)

**No Python installation required!**

If you're on Windows and just want to use the GUI application:

1. **Download the project** from GitHub
2. **Navigate to the `dist` folder**
3. **Install Tesseract OCR** (required for image processing):
   - Download from: https://github.com/UB-Mannheim/tesseract/wiki
   - Run the installer
   - Add to PATH or place in `C:\Program Files\Tesseract-OCR\`
4. **Double-click `braille_gui.exe`** to launch the application

That's it! The executable includes all Python dependencies built-in.

---

### 📚 Full Installation (For Developers & CLI Users)

If you want to use the CLI version or modify the source code, follow these steps:

### Step 1: Clone the Repository

```bash
git clone https://github.com/adham-eltantawi/braille-vision.git
cd braille-vision
```

Alternatively, download the ZIP file from GitHub and extract it.

### Step 2: Create a Virtual Environment (Recommended)

```bash
# Create virtual environment
python -m venv venv

# Activate on Windows:
venv\Scripts\activate

# Activate on macOS/Linux:
source venv/bin/activate
```

### Step 3: Install Python Dependencies

```bash
pip install pdfplumber pytesseract Pillow python-docx
```

Or use the provided `requirements.txt` file:

```bash
pip install -r requirements.txt
```

### Step 4: Install Tesseract OCR

Follow the instructions in the [Requirements](#-requirements) section above for your operating system.

### Step 5: Verify Installation

#### Test Tesseract:
```bash
tesseract --version
```

You should see output like:
```
tesseract 5.x.x
```

#### Test Python Environment:
```bash
python -c "import pdfplumber, pytesseract, PIL, docx; print('All dependencies OK')"
```

If successful, you'll see:
```
All dependencies OK
```

---

## 💻 Usage

### ⚡ Windows Executable (Easiest Method)

**For Windows users who installed via the Quick Start method:**

1. **Double-click** `braille_gui.exe` in the `dist` folder
2. The GUI application will launch automatically
3. **Make sure Tesseract OCR is installed** (see Quick Start section)
4. Follow the GUI instructions below in section C

**Note:** The `.exe` file is a standalone application - no Python installation needed!

---

### A) CLI Version

The command-line version provides a simple, scriptable interface for quick conversions.

#### Basic Syntax

```bash
python braille_cli.py <input_file> [options]
```

#### Examples

**Convert a PDF document:**
```bash
python braille_cli.py document.pdf
```

This creates:
- `document_braille.txt` - Braille text file
- `document_normal.docx` - Original text with RTL support
- `document_braille.docx` - Braille Word document

**Convert an image with custom output:**
```bash
python braille_cli.py scan.png -o my_output.txt
```

**Convert a JPEG image:**
```bash
python braille_cli.py photo.jpg
```

#### Command-Line Options

| Option | Description |
|--------|-------------|
| `input_file` | Path to PDF or image file (required) |
| `-o`, `--output` | Custom output text file path (optional) |
| `-h`, `--help` | Display help message and examples |

#### Expected Output

```
============================================================
Braille Converter (English & Arabic)
============================================================
Input: document.pdf

Processing PDF … 5 page(s) found.
  Reading page 1/5 …
  Reading page 2/5 …
  Reading page 3/5 …
  Reading page 4/5 …
  Reading page 5/5 …

✓ Extracted 2847 characters

Language: MIXED
  English: 1920
  Arabic: 927

Converting to Braille...
✓ Text: document_braille.txt

Generating Word documents...
✓ Normal: document_normal.docx
✓ Braille: document_braille.docx

============================================================
```

#### Error Handling

The CLI provides clear error messages:

```bash
# File not found
python braille_cli.py missing.pdf
# Output: File not found: missing.pdf

# Unsupported format
python braille_cli.py document.txt
# Output: Unsupported file type: '.txt'. Supported: .pdf .png .jpg .jpeg

# Missing dependencies
python braille_cli.py file.pdf
# Output: python-docx is required. Install it:
#   pip install python-docx
```

---

### B) GUI Version (Python Source)

The graphical version offers an intuitive interface with visual feedback and multi-threading.

**Note:** If you're using the Windows executable (`braille_gui.exe`), simply double-click it. The instructions below are for running from Python source.

#### Launching the GUI

```bash
python braille_gui.py
```

The application window will open with a modern dark-themed interface.

#### Using the GUI

**1. Select Input File**
- Click the **"Browse …"** button next to "Source file"
- Navigate to your PDF or image file
- Supported formats: `.pdf`, `.png`, `.jpg`, `.jpeg`
- The file path will appear in the text field

**2. Choose Output Folder**
- Click the **"Browse …"** button next to "Output folder"
- Select where you want to save the converted files
- Default: Current working directory

**3. Select Export Formats**
- **Braille TXT**: Plain text file with Braille Unicode (default: ON)
- **Normal DOCX**: Word document with original text and RTL support (default: ON)
- **Braille DOCX**: Word document with Braille text (default: ON)
- You can enable/disable any combination of these options

**4. Start Conversion**
- Click the **"Convert"** button
- The button will be disabled during processing to prevent multiple simultaneous conversions
- Progress appears in real-time in the log panel

**5. Monitor Progress**
- Watch the **Log Panel** for detailed status messages:
  - 🔵 **Blue (Info)**: Processing steps and informational messages
  - 🟢 **Green (Success)**: Successful operations and file saves
  - 🟡 **Yellow (Warning)**: Non-critical issues (e.g., missing optional components)
  - 🔴 **Red (Error)**: Critical errors with stack traces

**6. View Statistics**
- After text extraction, statistics pills appear showing:
  - **Language**: Detected primary language (ENGLISH, ARABIC, MIXED)
  - **Arabic**: Count of Arabic characters
  - **English**: Count of English characters
  - **Total**: Total character count

#### GUI Components Explained

**Title Bar**
- Displays Braille Unicode art: `⠋⠗⠁⠊⠑`
- Subtitle: "Braille Converter · PDF & Image → Braille"

**Input & Output Card**
- Labeled frame containing file selection controls
- Two entry fields with adjacent browse buttons
- Entry fields support direct text input if you know the path

**Export Options Card**
- Three checkboxes with tooltips (hover to see descriptions)
- Allows selective export format control

**Convert Button**
- Large, accent-colored button
- Hover effect for visual feedback
- Disabled state during active conversion

**Statistics Panel**
- Dynamic pill indicators with color coding
- Updates immediately after text extraction
- Provides quick language composition overview

**Log Panel**
- Scrollable text area with color-coded messages
- Read-only to prevent accidental edits
- Auto-scrolls to latest message
- Supports text selection for copying error messages

#### Multi-Threading Behavior

The GUI uses background threads to prevent interface freezing:
- Main thread handles UI updates and user interaction
- Worker thread performs file processing and conversion
- Thread-safe logging ensures proper message sequencing
- Button state management prevents race conditions

---

## 📸 Screenshots & Examples

### GUI Preview

![GUI Application](examples/screenshots/gui_preview.png)

*The GUI features a modern dark theme with purple accent colors, custom-styled buttons with hover effects, and a professional layout optimized for accessibility work.*

---

### Example Outputs

![Output Files](examples/screenshots/output_files.png)

*Shows the three generated files: Braille TXT, Normal DOCX (with RTL Arabic), and Braille DOCX.*

---

### Sample Input Files

The `examples/` folder contains sample files you can use to test the converter:

| File | Type | Description |
|------|------|-------------|
| `examples/sample_english.pdf` | PDF | English text document |
| `examples/sample_arabic.pdf` | PDF | Arabic text document |
| `examples/sample_mixed.pdf` | PDF | Mixed English and Arabic |
| `examples/sample_image.png` | Image | Scanned document for OCR |

---

### Braille Conversion Examples

#### Example 1: English Text

**Input:**
```
Hello World! This is a test.
```

**Output (Braille):**
```
⠠⠓⠑⠇⠇⠕ ⠠⠺⠕⠗⠇⠙⠖ ⠠⠞⠓⠊⠎ ⠊⠎ ⠁ ⠞⠑⠎⠞⠲
```

---

#### Example 2: Arabic Text

**Input:**
```
مرحبا بك في العالم
```

**Output (Braille):**
```
⠍⠗⠱⠃⠁ ⠃⠅ ⠋⠊ ⠁⠇⠷⠁⠇⠍
```

---

#### Example 3: Numbers

**Input:**
```
The year 2025 is here!
```

**Output (Braille):**
```
⠠⠞⠓⠑ ⠽⠑⠁⠗ ⠼⠃⠚⠃⠑ ⠊⠎ ⠓⠑⠗⠑⠖
```

---

#### Example 4: Mixed Language

**Input:**
```
Welcome مرحبا 2025
```

**Output (Braille):**
```
⠠⠺⠑⠇⠉⠕⠍⠑ ⠍⠗⠱⠃⠁ ⠼⠃⠚⠃⠑
```

---

## 🧠 How the Braille Converter Works

### Braille Mapping System

The converter uses comprehensive Unicode-based Braille mappings for both English and Arabic.

#### English Braille

The English mapping follows **Grade 1 Braille** (uncontracted) standards:

- **Lowercase letters (a-z)**: Direct mapping to Braille patterns
  - Example: `a` → `⠁`, `b` → `⠃`, `z` → `⠵`
- **Capital letters**: Preceded by capital indicator `⠠`
  - Example: `A` → `⠠⠁`, `Hello` → `⠠⠓⠑⠇⠇⠕`
- **Numbers (0-9)**: Prefixed with number indicator `⠼`
  - Example: `1` → `⠼⠁`, `5` → `⠼⠑`, `0` → `⠼⠚`
- **Punctuation**: Standard Braille punctuation marks
  - Period `.` → `⠲`, comma `,` → `⠂`, question `?` → `⠦`
- **Special symbols**: Mathematical and typographic symbols
  - Parentheses, brackets, operators, currency symbols, etc.

#### Arabic Braille

The Arabic mapping follows **Arabic Braille Code** standards:

- **Arabic letters**: All 28 basic letters plus variations
  - Example: `ا` → `⠁`, `ب` → `⠃`, `م` → `⠍`
- **Arabic numbers (٠-٩)**: Eastern Arabic numerals with number indicator
  - Example: `١` → `⠼⠁`, `٥` → `⠼⠑`
- **Hamza variations**: Support for أ, إ, آ, ؤ, ئ
- **Taa marbuta (ة)**: Dedicated Braille pattern `⠡`
- **Diacritics**: Automatically removed (َ ُ ِ ّ ْ ً ٌ ٍ)
  - These marks are not represented in standard Braille
- **Arabic punctuation**: ؟ ، ؛ mapped to equivalent Braille

#### Capital Indicator

For English text, uppercase letters use the **capital indicator** (`⠠`):

```python
# Example conversion logic:
if char.isupper():
    result.append('⠠')  # Capital indicator
    char = char.lower()
result.append(ENGLISH_BRAILLE[char])
```

Output example:
- `Hello` → `⠠⠓⠑⠇⠇⠕` (capital H indicated)
- `WORLD` → `⠠⠺⠠⠕⠠⠗⠠⠇⠠⠙` (each letter capitalized)

#### Language Detection

The converter automatically detects the language of each character:

```python
def is_arabic(char):
    # Unicode range for Arabic script
    return '\u0600' <= char <= '\u06FF' or '\u0750' <= char <= '\u077F'
```

**Detection logic:**
- Scans entire text for Arabic and English patterns
- Counts character occurrences in each language
- Determines primary language: `english`, `arabic`, or `mixed`
- Applies appropriate Braille mapping per character

#### Unicode Output

All Braille characters are represented using **Unicode Braille Patterns** (U+2800 to U+28FF):

- Standard representation across all platforms
- Compatible with screen readers
- Embossable on Braille printers
- Preserves formatting in plain text files

---

## 🏗️ Architecture & Internals

### Core Classes

#### `BrailleConverter` Class

**Purpose:** Handles all Braille conversion logic and language detection.

**Key Attributes:**
```python
ENGLISH_BRAILLE: dict  # English character → Braille mapping
ARABIC_BRAILLE: dict   # Arabic character → Braille mapping
CAPITAL_INDICATOR: str # Capital letter marker (⠠)
arabic_pattern: Pattern # Regex for Arabic text detection
english_pattern: Pattern # Regex for English text detection
```

**Key Methods:**

| Method | Purpose |
|--------|---------|
| `is_arabic(char)` | Check if character is in Arabic Unicode range |
| `detect_language(text)` | Determine if text is English, Arabic, or mixed |
| `text_to_braille(text)` | Convert entire text string to Braille |
| `get_language_stats(text)` | Calculate character counts by language |

**Conversion Algorithm:**
1. Iterate through each character in input text
2. Check if character is Arabic using Unicode range
3. If Arabic: Apply Arabic Braille mapping
4. If English and uppercase: Add capital indicator, convert to lowercase
5. Apply English Braille mapping
6. Handle special characters, numbers, punctuation
7. Preserve whitespace and newlines
8. Return complete Braille string

---

#### `FileProcessor` Class

**Purpose:** Manages file I/O, text extraction, and document generation.

**Key Attributes:**
```python
converter: BrailleConverter  # Instance of converter
_log: callable              # Logging callback function
```

**Key Methods:**

| Method | Purpose |
|--------|---------|
| `extract_pdf(path)` | Extract text from PDF using pdfplumber |
| `extract_image(path, languages)` | Perform OCR on image using Tesseract |
| `process_file(path)` | Route to appropriate extraction method |
| `save_normal_docx(text, path)` | Generate Word doc with original text |
| `save_braille_docx(text, path)` | Generate Word doc with Braille |
| `convert(input_path, output_txt)` | Main conversion orchestrator (CLI) |

**PDF Extraction Process:**
```python
1. Open PDF with pdfplumber
2. Iterate through all pages
3. Extract text from each page
4. Log progress per page
5. Warn if page is image-only
6. Join all pages with double newlines
7. Raise error if no text found
```

**OCR Extraction Process:**
```python
1. Open image with PIL (Pillow)
2. Attempt OCR with eng+ara languages
3. Fallback to eng if Arabic pack unavailable
4. Extract text string
5. Detect primary language
6. Raise error if no text extracted
```

**DOCX Generation:**

*Normal DOCX (Original Text):*
- Creates Word document with Arial font, 12pt
- Splits text by newlines into paragraphs
- Detects language per paragraph
- Arabic/mixed paragraphs: Right-aligned with RTL enabled (`w:bidi`)
- English paragraphs: Left-aligned
- Preserves paragraph structure and spacing

*Braille DOCX:*
- Uses Arial Unicode MS font, 14pt (better Braille visibility)
- All text left-aligned (Braille is directionally neutral)
- Preserves line breaks and structure
- No RTL formatting (Braille reads left-to-right)

---

### GUI Architecture

#### `BrailleConverterApp` Class (Tkinter Application)

**Purpose:** Main application window and UI controller.

**UI Component Hierarchy:**
```
BrailleConverterApp (tk.Tk)
├── outer (Frame - main container)
│   ├── title_bar (Frame)
│   │   ├── Title Label (⠋⠗⠁⠊⠑)
│   │   └── Subtitle Label
│   ├── _input_card (LabelFrame)
│   │   ├── Source file Entry + Browse Button
│   │   └── Output folder Entry + Browse Button
│   ├── _export_card (LabelFrame)
│   │   ├── Braille TXT Checkbox
│   │   ├── Normal DOCX Checkbox
│   │   └── Braille DOCX Checkbox
│   ├── btn_frame (Frame)
│   │   └── Convert Button (StyledButton)
│   ├── stats_frame (Frame - dynamic statistics)
│   └── log_wrapper (LabelFrame)
│       └── LogPanel (custom widget)
```

**Key Methods:**

| Method | Purpose |
|--------|---------|
| `_build_ui()` | Construct all UI components |
| `_input_card()` | Create file selection card |
| `_export_card()` | Create export options card |
| `_browse_input()` | Open file dialog for input |
| `_browse_output()` | Open folder dialog for output |
| `_start_convert()` | Validate and launch conversion thread |
| `_do_convert()` | Worker thread conversion logic |
| `_thread_log()` | Thread-safe logging to UI |
| `_show_stats()` | Display language statistics |

---

#### `StyledButton` Class (Custom Tkinter Widget)

**Purpose:** Create modern, styled buttons with hover effects using Canvas.

**Why Canvas Instead of tk.Button:**
- Full control over rounded corners
- Smooth color transitions
- Custom hover/press states
- Modern visual design
- No platform-specific styling limitations

**State Management:**
```python
States: normal → hover → press → release → hover
Colors:
  - normal: COLORS["accent"] or COLORS["surface"]
  - hover:  COLORS["accent_hover"] or COLORS["surface_alt"]
  - press:  COLORS["accent_press"] or COLORS["border"]
```

**Event Bindings:**
- `<Enter>`: Mouse enters button area → hover state
- `<Leave>`: Mouse leaves button area → normal state
- `<Button-1>`: Mouse button pressed → press state
- `<ButtonRelease-1>`: Mouse released → execute command → hover state

**Disabled State:**
- Unbinds all event handlers
- Changes to greyed-out appearance
- Prevents command execution

---

#### `LogPanel` Class (Custom Tkinter Widget)

**Purpose:** Scrollable, color-coded logging display with read-only text.

**Features:**
- **Tag-based coloring**: Each log level has a distinct color
- **Auto-scrolling**: Always shows latest message
- **Read-only**: Prevents accidental edits (state="disabled")
- **Copy support**: Users can select and copy text
- **Scrollbar**: Vertical scrolling for long logs

**Log Levels:**

| Level | Color | Use Case |
|-------|-------|----------|
| `info` | Cyan (`#8be9fd`) | Processing steps, general info |
| `success` | Green (`#50fa7b`) | Successful operations |
| `warning` | Yellow (`#f1fa8c`) | Non-critical issues |
| `error` | Red (`#ff5555`) | Critical errors |
| `normal` | White (`#e2e2ee`) | Default messages |

**Thread Safety:**
- All log calls from worker thread use `self.after(0, ...)` to queue in main thread
- Prevents race conditions and UI corruption

---

#### `ToolTip` Class (Hover Tooltip)

**Purpose:** Display helpful hints on hover for UI elements.

**Implementation:**
- Binds to widget's `<Enter>` and `<Leave>` events
- Creates temporary Toplevel window without window decorations
- Positions tooltip near widget cursor
- Auto-destroys on mouse leave

**Usage Example:**
```python
checkbox = tk.Checkbutton(...)
ToolTip(checkbox, "This exports Braille as plain text")
```

---

### Multi-Threading System

#### Thread Architecture

**Main Thread (UI Thread):**
- Handles all Tkinter UI updates
- Processes user interactions
- Manages window events
- Executes queued callbacks from worker thread

**Worker Thread (Conversion Thread):**
- Performs file I/O operations
- Runs OCR processing
- Executes Braille conversion
- Generates output files
- Logs progress via callback

**Communication Pattern:**
```python
Worker Thread                Main Thread
     |                           |
     |-- log("Processing...") -->|
     |                           |-- Update LogPanel
     |                           |
     |-- conversion complete --->|
     |                           |-- Update stats
     |                           |-- Enable button
```

**Thread-Safe Logging:**
```python
def _thread_log(self, msg, level):
    # Schedule log call in main thread event loop
    self.after(0, self.log, msg, level)
```

**Why Multi-Threading:**
- Prevents GUI freezing during long operations
- Maintains responsiveness during PDF/OCR processing
- Allows real-time progress updates
- Improves user experience

---

### Color Theme System

The GUI uses a carefully designed dark theme with semantic color naming:

```python
COLORS = {
    "bg": "#1e1e2e",           # Main background
    "surface": "#2a2a3d",      # Card backgrounds
    "surface_alt": "#33334a",  # Hover states
    "accent": "#7c6aff",       # Primary buttons
    "accent_hover": "#9585ff", # Button hover
    "accent_press": "#6350e0", # Button press
    "text": "#e2e2ee",         # Primary text
    "text_dim": "#9090a8",     # Secondary text
    "text_dark": "#1e1e2e",    # Text on accent
    "success": "#50fa7b",      # Success messages
    "warning": "#f1fa8c",      # Warnings
    "error": "#ff5555",        # Errors
    "border": "#44445a",       # Borders
    "log_bg": "#141420",       # Log background
}
```

**Design Principles:**
- High contrast for readability
- Accessible color combinations
- Professional appearance
- Reduced eye strain in low light
- Modern software aesthetic

---

## 🔧 Troubleshooting

### Common Issues and Solutions

#### ❌ Issue: "Tesseract not found" or "pytesseract.TesseractNotFoundError"

**Cause:** Tesseract OCR binary is not installed or not in system PATH.

**Solutions:**

**Windows:**
```bash
# 1. Download and install from:
https://github.com/UB-Mannheim/tesseract/wiki

# 2. Add to PATH or the GUI will auto-detect:
C:\Program Files\Tesseract-OCR\tesseract.exe

# 3. Verify installation:
tesseract --version
```

**macOS:**
```bash
brew install tesseract
tesseract --version
```

**Linux:**
```bash
sudo apt-get install tesseract-ocr
tesseract --version
```

---

#### ❌ Issue: "No text could be extracted from this image"

**Cause:** Image quality is poor, text is too small, or image contains no actual text.

**Solutions:**
1. **Improve image quality:**
   - Use higher resolution scans (300+ DPI recommended)
   - Ensure good lighting and contrast
   - Avoid blurry or rotated images

2. **Pre-process the image:**
   ```python
   # Example: Convert to grayscale, increase contrast
   from PIL import Image, ImageEnhance
   img = Image.open("input.png").convert("L")
   enhancer = ImageEnhance.Contrast(img)
   img = enhancer.enhance(2)
   img.save("enhanced.png")
   ```

3. **Check if image actually contains text:**
   - Some images are purely graphical
   - Handwritten text may not be recognized (Tesseract works best with printed text)

4. **Verify Tesseract is working:**
   ```bash
   tesseract test_image.png output
   cat output.txt
   ```

---

#### ❌ Issue: "Arabic pack unavailable — falling back to eng only"

**Cause:** Tesseract Arabic language data is not installed.

**Solutions:**

**Windows:**
```bash
# Download Arabic traineddata from:
https://github.com/tesseract-ocr/tessdata

# Copy ara.traineddata to:
C:\Program Files\Tesseract-OCR\tessdata\
```

**macOS:**
```bash
brew install tesseract-lang
```

**Linux (Debian/Ubuntu):**
```bash
sudo apt-get install tesseract-ocr-ara
```

**Verify:**
```bash
tesseract --list-langs
# Should show: ara, eng, ...
```

---

#### ❌ Issue: "ModuleNotFoundError: No module named 'pdfplumber'" (or pytesseract, PIL, docx)

**Cause:** Required Python packages are not installed.

**Solution:**
```bash
# Install all dependencies:
pip install pdfplumber pytesseract Pillow python-docx

# Or use requirements.txt:
pip install -r requirements.txt

# Verify installation:
python -c "import pdfplumber, pytesseract, PIL, docx; print('OK')"
```

**If using virtual environment:**
```bash
# Make sure venv is activated:
# Windows:
venv\Scripts\activate

# macOS/Linux:
source venv/bin/activate

# Then install:
pip install pdfplumber pytesseract Pillow python-docx
```

---

#### ❌ Issue: GUI freezes during conversion

**Cause:** This shouldn't happen due to multi-threading, but if it does:

**Solutions:**
1. **Check for errors in terminal:**
   - Run `python braille_gui.py` from terminal
   - Look for exception stack traces

2. **Verify file is valid:**
   - Try a smaller/simpler test file first
   - Corrupted files can cause hangs

3. **Update dependencies:**
   ```bash
   pip install --upgrade pdfplumber pytesseract Pillow python-docx
   ```

4. **Check system resources:**
   - Large PDFs or high-resolution images require significant RAM
   - Close other applications if system is under memory pressure

---

#### ❌ Issue: Arabic text appears reversed or broken in DOCX

**Cause:** The application should handle RTL correctly, but older versions of Word may have issues.

**Solutions:**
1. **Update Microsoft Word:**
   - Ensure you're using a recent version with RTL support

2. **Manually fix in Word:**
   - Select Arabic text
   - Right-click → Paragraph → Text Direction → Right-to-left

3. **Check the Normal DOCX file:**
   - The converter sets RTL automatically for Arabic paragraphs
   - If still broken, try opening in LibreOffice Writer or Google Docs

---

#### ❌ Issue: Permission denied when saving files

**Cause:** Insufficient write permissions in output directory.

**Solutions:**
1. **Choose a different output folder:**
   - Use Desktop, Documents, or Downloads folder
   - Avoid system directories like C:\Program Files\

2. **Run with elevated permissions (not recommended):**
   ```bash
   # Windows (Command Prompt as Administrator):
   python braille_gui.py
   ```

3. **Check folder permissions:**
   ```bash
   # Linux/macOS:
   ls -ld /path/to/output
   chmod 755 /path/to/output
   ```

---

#### ❌ Issue: "Unsupported file type" error

**Cause:** File extension is not .pdf, .png, .jpg, or .jpeg.

**Solutions:**
1. **Convert file to supported format:**
   - TIFF → PNG: Use GIMP or ImageMagick
   - BMP → PNG: Use any image editor
   - DOCX → PDF: Use Word's "Save as PDF" or LibreOffice

2. **Check file extension:**
   ```bash
   # Rename if extension is uppercase:
   mv file.PDF file.pdf
   mv file.PNG file.png
   ```

---

#### ❌ Issue: Braille characters display as boxes (□) in text editor

**Cause:** Text editor/font doesn't support Unicode Braille.

**Solutions:**
1. **Use a Unicode-capable editor:**
   - Notepad++ (Windows)
   - VS Code (all platforms)
   - Sublime Text (all platforms)
   - gedit (Linux)

2. **Install a font with Braille support:**
   - DejaVu Sans Mono
   - Arial Unicode MS
   - Segoe UI Symbol

3. **Change editor font:**
   - In Notepad++: Settings → Style Configurator → Global Styles → Font
   - In VS Code: File → Preferences → Settings → Font Family

4. **The DOCX files should display correctly in Microsoft Word or LibreOffice.**

---

## 📄 License

MIT License

Copyright (c) 2025 Adham Eltantawi

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

## 🙏 Credits

**Braille Vision** was created to support accessibility and inclusivity in digital content.

### Author

**Adham Eltantawi**
- GitHub: [@adham-eltantawi](https://github.com/adham-eltantawi)
- Email: adhameltantawi@gmail.com

### Technologies Used

- **Python** - Core programming language
- **Tkinter** - GUI framework (included with Python)
- **pdfplumber** - PDF text extraction library
- **Tesseract OCR** - Optical character recognition engine
- **pytesseract** - Python wrapper for Tesseract
- **Pillow (PIL)** - Python Imaging Library
- **python-docx** - Microsoft Word document generation

### Braille Standards

- **English Braille** - Based on Unified English Braille (UEB) Grade 1
- **Arabic Braille** - Based on standard Arabic Braille code
- **Unicode Braille Patterns** - U+2800 to U+28FF

### Acknowledgments

- The Tesseract OCR team for their excellent open-source OCR engine
- The Python community for robust libraries and documentation
- Accessibility advocates working to make information available to everyone
- Contributors and users who provide feedback and suggestions

### Special Thanks

- To educators and accessibility professionals who inspired this project
- To the visually impaired community for their valuable insights
- To open-source contributors who make projects like this possible

---

## 📞 Support & Contributions

### Getting Help

If you encounter issues not covered in the [Troubleshooting](#-troubleshooting) section:

1. **Check existing issues:** [GitHub Issues](https://github.com/adham-eltantawi/braille-vision/issues)
2. **Open a new issue:** Provide detailed information including:
   - Operating system and version
   - Python version (`python --version`)
   - Error messages and stack traces
   - Steps to reproduce the problem
   - Sample file (if applicable and not sensitive)

### Contributing

Contributions are welcome! Here's how you can help:

**Bug Reports:**
- Use the issue tracker
- Include reproducible examples
- Attach error logs

**Feature Requests:**
- Describe the use case
- Explain expected behavior
- Suggest implementation approach

**Code Contributions:**
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Add tests if applicable
5. Commit with clear messages (`git commit -m 'Add amazing feature'`)
6. Push to your fork (`git push origin feature/amazing-feature`)
7. Open a Pull Request

**Documentation:**
- Fix typos
- Improve clarity
- Add examples
- Translate to other languages

---

## 📚 Additional Resources

### Learning Braille
- [Braille Authority of North America](http://www.brailleauthority.org/)
- [Unified English Braille (UEB)](https://en.wikipedia.org/wiki/Unified_English_Braille)
- [Arabic Braille Code](https://en.wikipedia.org/wiki/Arabic_Braille)

### Accessibility Tools
- [NVDA Screen Reader](https://www.nvaccess.org/)
- [JAWS Screen Reader](https://www.freedomscientific.com/products/software/jaws/)
- [National Braille Press](https://www.nbp.org/)

### Technical Documentation
- [Unicode Braille Patterns](https://en.wikipedia.org/wiki/Braille_Patterns)
- [Tesseract OCR Documentation](https://tesseract-ocr.github.io/)
- [python-docx Documentation](https://python-docx.readthedocs.io/)

---

<div align="center">

**Made with ❤️ for accessibility and inclusion**

⭐ Star this repository if you find it helpful!

[Report Bug](https://github.com/adham-eltantawi/braille-vision/issues) · [Request Feature](https://github.com/adham-eltantawi/braille-vision/issues)

</div>
