# 📸 AI Screenshot Data Extractor

A powerful web application that uses OCR (Optical Character Recognition) to extract structured data from social media screenshots and export it in multiple formats.

## 🚀 Features

- **Multi-Platform Support**: TikTok, Instagram, YouTube, Telegram, and TikTok Live Recap
- **Advanced OCR**: Powered by Tesseract.js with image preprocessing
- **Multiple Export Formats**: CSV, JSON, Excel (.xlsx), and XML
- **Batch Processing**: Process multiple screenshots simultaneously
- **Analytics Dashboard**: Visual charts and performance metrics
- **Data Validation**: Duplicate detection and error checking
- **Responsive Design**: Works on desktop and mobile devices

## 📁 Files Structure

```
├── screenshot_extractor.html  # Main application file
├── config.json               # Configuration and platform settings
├── sample_data.json          # Sample exported JSON data
├── sample_data.csv           # Sample exported CSV data
└── README.md                 # This documentation
```

## ⚙️ Configuration (config.json)

The `config.json` file contains all platform configurations, extraction patterns, and application settings:

### Platform Configuration

```json
{
  "platforms": {
    "tiktok": {
      "name": "TikTok Profiles",
      "fields": ["name", "username", "followers", ...],
      "headers": ["Name", "Username", "Followers", ...],
      "extractionPatterns": {
        "username": {
          "patterns": ["/@[\\w.]+/"],
          "description": "Extract username starting with @"
        }
      }
    }
  }
}
```

### Settings Configuration

```json
{
  "settings": {
    "ocr": {
      "maxImageSize": 1200,
      "jpegQuality": 0.8,
      "maxFileSize": 10485760
    },
    "batch": {
      "maxConcurrency": 2,
      "delayBetweenFiles": 100
    }
  }
}
```

## 🎯 Supported Platforms

### TikTok Profiles
- Name, Username, Followers, Following
- Likes, Videos, Bio, Verification Status
- Live Status, Profile Link, Engagement Rate

### Instagram Profiles  
- Name, Username, Followers, Following
- Posts, Bio, Verification, Privacy Status
- Profile Link, Category

### YouTube Channels
- Channel Name, Subscribers, Videos
- Total Views, Description, Verification
- Channel Link, Join Date

### Telegram Channels
- Channel Name, Username, Subscribers
- Description, Type, Language
- Channel Link, Verification

### TikTok Live Recap
- Username, Duration, Viewers, Peak Viewers
- New Followers, Diamonds, Gifts
- Shares, Comments, Go Live Button

## 🔧 Usage

1. **Open the Application**: Open `screenshot_extractor.html` in a web browser
2. **Select Platform**: Choose the platform type from the buttons
3. **Upload Screenshot**: Drag & drop or click to upload image files
4. **Review Data**: Check and edit the extracted information
5. **Save Data**: Click "Add to Dataset" to save the entry
6. **Export Data**: Use export buttons to download in your preferred format

## ⌨️ Keyboard Shortcuts

- **Ctrl+S**: Save current data
- **Ctrl+U**: Upload file
- **Ctrl+B**: Toggle batch mode
- **Ctrl+A**: Open analytics dashboard
- **Ctrl+I**: Import CSV file
- **Escape**: Close modals

## 📊 Export & Import Formats

### CSV Export
- **Excel Compatible**: UTF-8 with BOM for proper character encoding
- **Customizable**: Configurable delimiter and date format
- **Clean Data**: Automatic text cleanup for multi-line fields
- **Quoted Fields**: All fields wrapped in quotes for safety

### CSV Import
- **Smart Detection**: Automatically detects platform from data patterns
- **Data Validation**: Validates and cleans imported data
- **Merge Support**: Adds to existing data without overwriting
- **Error Handling**: Detailed feedback on import issues

### JSON Export
- **Developer Friendly**: Structured data with metadata
- **Complete Information**: Includes processing times and confidence scores
- **Pretty Formatted**: Indented for readability

### Excel Export (.xlsx)
- **Native Format**: True Excel format with proper cell types
- **Multi-Platform**: Separate sheets for different platforms
- **Formatted Headers**: Professional appearance

### XML Export
- **Structured Markup**: Well-formed XML for data interchange
- **CDATA Protection**: Safe handling of special characters
- **Schema Compatible**: Standard XML structure

## 🚀 Performance Features

- **Smart Image Resizing**: Automatically optimizes image size for faster OCR
- **Parallel Batch Processing**: Utilizes multiple CPU cores for batch operations
- **Memory Management**: Efficient resource cleanup and optimization
- **Processing Time Tracking**: Real-time performance monitoring

## 🛠️ Customization

### Adding New Platforms

1. Edit `config.json` to add new platform configuration:

```json
{
  "platforms": {
    "newplatform": {
      "name": "New Platform",
      "fields": ["field1", "field2"],
      "headers": ["Field 1", "Field 2", "Date Added", "Actions"],
      "extractionPatterns": {
        "field1": {
          "patterns": ["/pattern1/i"],
          "description": "Description of extraction"
        }
      }
    }
  }
}
```

2. Add platform button to HTML:

```html
<button class="platform-btn" data-platform="newplatform">
    <span class="status-indicator status-ready"></span>New Platform
</button>
```

### Customizing Extraction Patterns

Modify the `extractionPatterns` in `config.json` to improve data extraction for your specific use case:

```json
{
  "extractionPatterns": {
    "followers": {
      "patterns": [
        "/(\\d+[,.]?\\d*[KMB]?)\\s*(Followers|followers)/i",
        "/Followers[:\\s]*(\\d+[,.]?\\d*[KMB]?)/i"
      ],
      "description": "Extract follower count with K/M/B suffixes"
    }
  }
}
```

## 🔍 Troubleshooting

### Common Issues

1. **OCR Not Working**: Refresh the page and check browser console for errors
2. **Config Not Loading**: Ensure `config.json` is in the same directory as the HTML file
3. **Poor Extraction**: Try images with higher contrast and clearer text
4. **Slow Processing**: Use smaller image files (under 2MB) for faster results

### Performance Tips

- Use high-contrast screenshots for better OCR accuracy
- Keep image files under 2MB for optimal processing speed
- Process images in batches for efficiency
- Use JPEG format for smaller file sizes

## 🆕 Version History

- **v2.0.0** (2024-12-19): Added JSON configuration, enhanced platforms, improved performance
- **v1.0.0**: Initial release with basic OCR functionality

## 📝 License

This project is open source and available under the MIT License.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

---

**Built with ❤️ using Tesseract.js, Chart.js, and modern web technologies**