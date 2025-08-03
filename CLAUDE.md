# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an AI Screenshot Data Extractor - a client-side web application that uses OCR (Optical Character Recognition) to extract structured data from social media screenshots and export it in multiple formats. The application is entirely browser-based with no backend server required.

## Architecture

### Core Technology Stack
- **Frontend**: Vanilla HTML, CSS, JavaScript (ES6+)
- **OCR Engine**: Tesseract.js with multiple CDN fallbacks
- **Data Processing**: PapaParse (CSV), XLSX.js (Excel), Chart.js (analytics)
- **Architecture**: Single-page application with embedded styles and JavaScript

### Key Files
- `screenshot_extractor.html` - Main application file containing all HTML, CSS, and JavaScript
- `config.json` - Platform configurations, extraction patterns, and application settings
- `sample_data.json/csv` - Sample output files for reference
- `README.md` - User documentation and feature descriptions
- `PRD.md` - Comprehensive product requirements document
- `DEPLOYMENT_GUIDE.md` - Deployment instructions for various hosting options

### Application Structure
The main application (`screenshot_extractor.html`) is a self-contained file with:
- **OCR Processing**: Multi-platform data extraction using configurable regex patterns
- **Platform Support**: TikTok, Instagram, YouTube, Telegram, TikTok Live Recap
- **Batch Processing**: Concurrent file processing with configurable limits
- **Export Capabilities**: CSV, JSON, Excel (.xlsx), XML formats
- **Analytics Dashboard**: Performance metrics and processing statistics

## Configuration System

All platform-specific settings are externalized in `config.json`:
- **Platform Definitions**: Field mappings, headers, extraction patterns
- **OCR Settings**: Image processing parameters and file size limits
- **Validation Rules**: Required fields and data type validation
- **Export Options**: Format-specific configuration options

## Development Commands

This is a static web application with no build process. To work with the code:

### Testing Locally
```bash
# Serve files locally (Python)
python -m http.server 8000

# Or with Node.js
npx http-server

# Or with PHP
php -S localhost:8000
```

### Deployment
```bash
# Simple deployment - copy files to web server
cp *.html *.json *.md /path/to/webserver/

# For GitHub Pages
git add . && git commit -m "Deploy updates" && git push origin main
```

## Important Implementation Details

### OCR Processing
- Uses Tesseract.js with multiple CDN fallbacks for reliability
- Implements image preprocessing (resizing, quality adjustment)
- Processes files with configurable concurrency limits (default: 2)
- Maximum file size: 10MB, optimized for images under 2MB

### Data Extraction
- Platform detection via button selection (not automatic)
- Regex-based pattern matching defined in `config.json`
- Field validation using configured rules
- Support for numeric value conversion (K/M/B suffixes)

### Performance Considerations
- Client-side processing only - no server dependencies
- Memory management for large batch operations
- Processing time tracking and performance metrics
- Smart image resizing for optimal OCR speed

### Browser Compatibility
- Modern browsers required (Chrome 80+, Firefox 75+, Safari 13+, Edge 80+)
- Requires JavaScript enabled
- Needs internet connection for CDN resources
- Local storage used for configuration and temporary data

## Adding New Platforms

To add support for a new social media platform:

1. **Update config.json** - Add platform definition with fields, headers, and extraction patterns
2. **Add UI Button** - Include platform button in the HTML interface
3. **Test Extraction** - Verify regex patterns work with sample screenshots

## Security Notes

- All processing happens client-side
- No server-side data storage or transmission
- Input validation and sanitization implemented
- CSP headers recommended for production deployment