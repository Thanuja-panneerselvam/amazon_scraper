# Amazon Product Scraper

A Python-based web scraper that extracts detailed product information from Amazon India's search results. The script collects data such as product names, prices, ratings, reviews, and additional product details, saving them to a CSV file for further analysis.

## Features

- Scrapes multiple pages of Amazon search results (up to 20 pages)
- Extracts detailed product information including:
  - Product Name
  - Product URL
  - Price
  - Rating
  - Number of Reviews
  - Manufacturer
  - ASIN (Amazon Standard Identification Number)
- Handles different product detail page layouts (list and table formats)
- Saves data in CSV format for easy analysis

## Prerequisites

Before running the script, make sure you have the following installed:
- Python 3.x
- Chrome WebDriver
- Required Python packages:
  ```
  selenium
  beautifulsoup4
  ```

## Installation

1. Clone this repository:
   ```bash
   git clone [your-repository-url]
   ```

2. Install required packages:
   ```bash
   pip install selenium beautifulsoup4
   ```

3. Download and install ChromeDriver:
   - Visit the [ChromeDriver downloads page](https://sites.google.com/chromium.org/driver/)
   - Download the version that matches your Chrome browser
   - Add the ChromeDriver to your system's PATH

## Usage

1. Update the `URL` variable in the script if you want to search for different products:
   ```python
   URL = "https://www.amazon.in/s?k=bags&crid=2M096C61O4MLT&qid=1653308124&sprefix=ba%2Caps%2C283&ref=sr_pg_1"
   ```

2. Run the script:
   ```bash
   python amazon_scraper.py
   ```

3. The script will create a `Scraped_Data.csv` file containing the extracted information.

## Output Format

The script generates a CSV file with the following columns:
- Product URL
- Product Name
- Product Price
- Rating
- Number of reviews
- Manufacturer
- ASIN






