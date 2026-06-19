# CoverScope - AI Plant Coverage Measurement

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![HTML5](https://img.shields.io/badge/HTML-5-orange.svg)]
[![CSS3](https://img.shields.io/badge/CSS-3-blue.svg)]
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow.svg)]

A web-based application that measures plant coverage in images using AI-powered computer vision techniques. Replicates the functionality of coverscope.whacka.app with a complete HTML web interface.

## Features

- **Drag & Drop Image Upload** - Easily upload images from your device
- **Three AI Analysis Modes**: Green Detection, NDVI Simulation, Edge Detection
- **Real-time Results** with visual feedback and statistics
- **📊 Comparable Results Section** - Save and compare previous analyses over time
- **📁 Excel Export** - Download all results as an Excel file (.xlsx)
- **Responsive Design** - Works on desktop and mobile
- **No Backend Required** - Runs entirely client-side

## How to Use

```bash
# Direct file open
open index.html  # macOS
xdg-open index.html  # Linux

# Or with local server
python -m http.server 8000
# Then open http://localhost:8000
```

## New Features Added

### 1. Excel File Download
- Download button generates a professional `.xlsx` file
- Uses SheetJS library (loaded from CDN)
- Contains two sheets: "Current Analysis" and "Comparison History"
- Opens in Excel, Google Sheets, or any spreadsheet application

### 2. Comparable Results Section
- **Save Results** button stores current analysis
- **Previous Analyses** section displays historical results as cards
- Shows coverage percentage, mode, timestamp, and pixel count
- **Comparison to Current**: Displays difference from current analysis
- Results persist in localStorage between browser sessions
- Delete individual results
- Toggle section visibility
- Stores up to 10 previous results

## Project Structure

```
coverscope-web/
├── index.html    # Complete web app with all features
├── README.md     # Documentation
├── LICENSE       # MIT License
└── .gitignore    # Git ignore
```

## Technical Stack

- HTML5 Canvas for image processing
- Vanilla JavaScript (no frameworks)
- CSS3 with CSS variables
- SheetJS for Excel generation
- localStorage for data persistence

## Repository Status

The repository is ready at `/tmp/coverscope-web` with:
- 2 commits
- Complete implementation of requested features
- Full documentation
