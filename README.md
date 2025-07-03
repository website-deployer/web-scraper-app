# Web Scraper & Data Analyzer

A modern Python application with a sleek PyQt5 GUI for web scraping, data analysis, and visualization. Features a clean, minimalistic design with real-time progress tracking and comprehensive data filtering capabilities.

## Features

- **Modern UI**: Clean, minimalistic design with dark theme and smooth animations
- **Web Scraping**: Multi-threaded scraping with configurable depth (max 100 levels)
- **Data Visualization**: Interactive table with sorting and filtering capabilities
- **Content Preview**: Dual preview system with both text and visual HTML rendering
- **Data Analysis**: Comprehensive statistics and domain breakdown
- **Export Functionality**: JSON export with full metadata
- **URL Normalization**: Handles www/non-www domains intelligently
- **Real-time Progress**: Live progress updates during scraping operations
- **Loop Prevention**: Advanced duplicate detection to prevent infinite loops
- **Smart Limits**: Configurable limits to prevent runaway scraping

## Loop Prevention & Duplicate Detection

The scraper includes robust protection against infinite loops and circular references:

### 🔄 URL Normalization
- Removes `www.` prefixes for consistent domain handling
- Strips URL fragments (`#section`) to prevent duplicate content
- Removes trailing slashes for consistency
- Normalizes query parameters

### 🚫 Duplicate Detection
- **Visited URL Tracking**: Maintains a set of all visited URLs
- **Unlimited Crawling**: No page limits per domain or total pages
- **Per-Page Duplicate Filtering**: Removes duplicate links within the same page

### 🛡️ Smart Restrictions
- **No Depth Limits**: Crawl as deep as the specified max_depth allows
- **Content Type Filtering**: Only scrapes HTML content
- **File Type Filtering**: Skips non-content files (PDFs, images, etc.)
- **Consecutive Empty Level Detection**: Stops if 3 consecutive levels have no new content

### 📊 Enhanced Tracking
- **Domain Page Counts**: Tracks pages scraped per domain (for statistics)
- **URL Check Counts**: Shows total URLs checked vs. pages scraped
- **Detailed Statistics**: Comprehensive reporting on scraping efficiency
- **Unlimited Processing**: No artificial limits on crawling scope

## Installation

1. **Clone or download the project files**

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application**:
   ```bash
   python web_scraper_app.py
   ```

## Visual Preview Feature

The application includes a visual HTML preview feature that renders scraped web pages in a browser-like view:

- **Requirements**: PyQtWebEngine (automatically installed with requirements.txt)
- **Functionality**: Displays HTML content with proper styling and formatting
- **Fallback**: If PyQtWebEngine is not available, shows a text-only preview
- **Error Handling**: Graceful error messages for invalid HTML content

To test the visual preview functionality:
```bash
python test_visual_preview.py
```

## Testing Duplicate Detection

Test the improved loop prevention and duplicate detection:
```bash
python test_duplicate_detection.py
```

## Usage

### 1. Scraping Configuration
- Enter a starting URL (with or without http/https)
- Set maximum crawl depth (1-100)
- Click "Start Scraping" to begin

### 2. Data View & Filtering
- View scraped data in an interactive table
- Filter by search terms or specific domains
- Double-click any row to preview content
- Export data to JSON format

### 3. Analysis & Statistics
- View comprehensive scraping statistics
- See domain breakdown and word counts
- Preview content in both text and visual formats
- Analyze load times and link counts
- Monitor duplicate detection efficiency

## Technical Details

- **Backend**: Pure Python with urllib and html.parser (no compilation required)
- **Frontend**: PyQt5 with custom modern styling
- **Threading**: Multi-threaded scraping for better performance
- **Data Storage**: Website objects with full metadata
- **URL Handling**: Intelligent normalization and domain filtering
- **Loop Prevention**: Multi-layered duplicate detection system

## File Structure

```
Testing/
├── web_scraper_app.py      # Main application
├── test_module.py          # Core scraping logic
├── test.py                 # Basic functionality tests
├── test_visual_preview.py  # Visual preview test
├── test_duplicate_detection.py  # Loop prevention test
├── requirements.txt        # Dependencies
└── README.md              # This file
```

## Troubleshooting

### Visual Preview Not Working
1. Ensure PyQtWebEngine is installed: `pip install PyQtWebEngine`
2. Run the test script: `python test_visual_preview.py`
3. Check console output for import errors

### Scraping Issues
1. Verify internet connection
2. Check URL format (add https:// if needed)
3. Try with a lower depth setting
4. Check console for error messages

### Loop Prevention
1. The scraper automatically prevents infinite loops
2. Check the analysis tab for detailed statistics
3. Monitor "Total URLs Checked" vs "Total Pages" for efficiency
4. Use lower depth settings for sites with many internal links

### Performance
- Use lower depth settings for faster scraping
- Filter data to focus on specific domains
- Close other applications to free up resources
- Monitor domain page counts to avoid hitting limits

## License

This project is open source and available under the MIT License. 