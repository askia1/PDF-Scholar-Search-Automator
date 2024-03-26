PDF Scholar Search Automator

The PDF Scholar Search Automator is a Python script designed for academics, researchers, and anyone in need of automating the extraction of text from PDF documents and subsequently performing searches on Google Scholar with the extracted text. This tool is especially useful for quickly finding scholarly articles, references, and citations related to specific content within PDF documents.

Features

PDF Text Extraction: Extracts text from PDF documents, allowing for the analysis or searching of the content.
Automated Google Scholar Searches: Performs automated searches on Google Scholar using the extracted text, facilitating easy access to related scholarly articles.


Prerequisites
Before you begin, ensure you have the following installed:

Python 3.x

Google Chrome or any Selenium-supported web browser
Corresponding WebDriver for the browser (e.g., ChromeDriver for Google Chrome)

INSTALLATION

Clone the Repository:
Start by cloning this repository to your local machine, or download the ZIP file.


git clone https://github.com/your-github-username/pdf-scholar-search-automator.git
Install Required Packages:

Navigate to the cloned directory and install the required Python packages using pip:

pip install pypdf2
pip install selenium
WebDriver Setup:

Ensure you have downloaded the WebDriver for your browser and it is accessible in your system's PATH, or you can specify its path directly in the script.

USAGE

PDF Text Extraction
Open your Python script and adjust the path to the PDF file you wish to extract text from:

import PyPDF2 as p2

PDFfile = open("path/to/your/pdf/LadopedBi22122.pdf", "rb")
pdfread = p2.PdfFileReader(PDFfile)

for i in range(pdfread.getNumPages()):
    pageinfo = pdfread.getPage(i)
    print(pageinfo.extractText())
    
Automated Google Scholar Search

Adjust the path to your WebDriver and replace 'Your extracted text here' with the text you wish to search for on Google Scholar:

from selenium import webdriver
from selenium.webdriver.common.keys import Keys

driver = webdriver.Chrome('/path/to/your/chromedriver')  # Update this path
driver.get('https://scholar.google.com/')
search_box = driver.find_element_by_css_selector('input[name=q]')

search_box.send_keys('Your extracted text here')
search_box.send_keys(Keys.ENTER)
Single Page Extraction and More


For specific operations like extracting a single page's text or accessing document information:

x = pdfread.getPage(0)
print(x.extractText())

print(pdfread.getIsEncrypted())
print(pdfread.getDocumentInfo())
print(pdfread.getNumPages())
