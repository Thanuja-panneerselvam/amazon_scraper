README
Project Title: Amazon Product Scraper
This project is a web scraping tool that collects product information from Amazon India using Selenium and BeautifulSoup. The scraper retrieves data such as product name, URL, price, rating, number of reviews, manufacturer, and ASIN, and saves it to a CSV file.

Table of Contents
Features
Requirements
Installation
Usage
Contributing
License

Features
Scrapes multiple pages of products from Amazon.
Extracts detailed product information including:
Product Name
Product URL
Product Price
Rating
Number of Reviews
Manufacturer
ASIN
Saves the scraped data to a CSV file for easy access and analysis.
Requirements
To run this project, you need:

Python 3.x
Selenium
BeautifulSoup4
Chrome WebDriver
You can install the required Python packages using pip:

bash

Verify

Open In Editor
Edit
Copy code
pip install selenium beautifulsoup4
Make sure to have Chrome WebDriver installed and added to your system PATH.

Installation
Clone the repository:

bash

Verify

Open In Editor
Edit
Copy code
git clone https://github.com/yourusername/amazon-product-scraper.git
Navigate to the project directory:

bash

Verify

Open In Editor
Edit
Copy code
cd amazon-product-scraper
Install the required packages:

bash

Verify

Open In Editor
Edit
Copy code
pip install -r requirements.txt
Usage
Open the script file and modify the URL variable to search for the desired products on Amazon India.

Run the script:

bash

Verify

Open In Editor
Edit
Copy code
python scraper.py
The scraped data will be saved in a file named Scraped_Data.csv in the same directory.

Contributing
Contributions are welcome! If you have suggestions for improvements or features, please feel free to submit a pull request or open an issue.

License
This project is licensed under the MIT License - see the LICENSE file for details.

Note
On November 10, 2024, an error occurred during scraping due to a traffic issue on the Amazon page. Please ensure to handle such exceptions in your implementation to avoid interruptions.

