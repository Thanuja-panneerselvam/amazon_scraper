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


## Code Overview
This Python script is designed to scrape product information from Amazon India using Selenium WebDriver and BeautifulSoup4. The script automates the process of collecting product data from search results and individual product pages.

## Technical Components

### 1. Dependencies and Setup
```python
import csv
from selenium import webdriver
from bs4 import BeautifulSoup, NavigableString
```
- `selenium`: Used for browser automation and dynamic page loading
- `BeautifulSoup4`: Used for HTML parsing
- `csv`: Handles data export to CSV format

### 2. Core Functions

#### URL Generation (`get_urls`)
```python
def get_urls(url_list):
    for page in range(2,21):
        next_url = URL + f"&page={page}"
        url_list.append(next_url)
```
- Generates URLs for pages 2-20 of search results
- Appends URLs to a master list for processing

#### Basic Data Extraction (`get_data`)
```python
def get_data(item):
    # Extracts: Product URL, Name, Price, Rating, Reviews
```
Key operations:
- Extracts product name and URL from `h2` tags
- Retrieves price from `span` with class `a-offscreen`
- Collects rating and review count with error handling
- Returns data as a dictionary

#### Main Processing Function (`main`)
The main function performs three key operations:

1. **Search Results Processing**
```python
for i in pages:
    driver.get(i)
    soup = BeautifulSoup(driver.page_source, 'html.parser')
    results = soup.find_all('div', {'data-component-type': "s-search-result"})
```

2. **Detailed Product Information**
```python
for row in answer:
    url = row['Product URL']
    driver.get(url)
    # Process product details...
```

3. **Data Export**
```python
with open('Scraped_Data.csv', 'w', encoding='utf-8') as csvfile:
    writer = csv.DictWriter(csvfile, fieldnames=field_name)
    writer.writeheader()
    writer.writerows(scraped_data)
```

## Data Collection Methods

### Search Results Page
- Extracts basic product information from search results grid
- Uses BeautifulSoup to parse product cards
- Handles missing data through try-except blocks

### Product Detail Page
The script handles two different layout types:

1. **List Layout**
```python
info = soup2.find_all('div', {'id': "detailBullets_feature_div"})
```

2. **Table Layout**
```python
info = soup2.find_all('table', {'id': "productDetails_techSpec_section_1"})
info2 = soup2.find_all('table', {'id': "productDetails_detailBullets_sections1"})
```

## Data Structure

### Collected Fields
- Product URL
- Product Name
- Product Price
- Rating
- Number of reviews
- Manufacturer
- ASIN (Amazon Standard Identification Number)

### Output Format
Data is saved in CSV format with the following structure:
```csv
Product URL,Product Name,Product Price,Rating,Number of reviews,Manufacturer,ASIN
```

## Error Handling

The script includes error handling for:
- Missing product prices
- Absent ratings and reviews
- Different page layouts
- Navigation issues

## Technical Considerations

### Performance
- Processes 20 pages of search results
- Visits each product page individually
- No implemented delay between requests (consider adding for production use)

### Limitations
- Dependent on Amazon's HTML structure
- No retry mechanism for failed requests
- Single-threaded execution
- No proxy support

## Future Improvements
Consider implementing:
1. Request rate limiting
2. Multi-threading for parallel processing
3. Proxy rotation
4. Robust error recovery
5. Data validation
6. Session management
7. Log handling

## Usage Notes
- ChromeDriver version should match Chrome browser version
- Monitor Amazon's robots.txt and terms of service
- Consider implementing delays between requests
- Validate output data for completeness




