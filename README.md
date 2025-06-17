# 📄 PDF Scholar Search Automator

The **PDF Scholar Search Automator** is a lightweight Python tool that extracts text from academic PDF files and uses it to perform automated searches on **Google Scholar**. Ideal for researchers, students, and analysts looking to rapidly find citations or related literature without copying text manually.

---

## 🔧 Features

* **PDF Text Extraction**: Extracts full or partial text from academic PDFs.
* **Automated Google Scholar Search**: Opens Google Scholar and runs searches using extracted content.
* **Headless Browser Option**: (Optional) Run searches in the background using Selenium.

---

## 🧰 Requirements

* Python 3.x
* Google Chrome (or any Selenium-compatible browser)
* ChromeDriver (or equivalent WebDriver)

---

## 📦 Installation

**1. Clone the Repository**

```bash
git clone https://github.com/your-username/pdf-scholar-search-automator.git
cd pdf-scholar-search-automator
```

**2. Install Required Packages**

```bash
pip install PyPDF2 selenium
```

**3. Setup WebDriver**

* Download the correct version of [ChromeDriver](https://sites.google.com/a/chromium.org/chromedriver/)
* Ensure it’s in your system PATH or reference it directly in the script.

---

## 🚀 Usage

### 1. PDF Text Extraction

```python
import PyPDF2

with open("LadopedBi22122.pdf", "rb") as PDFfile:
    pdfread = PyPDF2.PdfFileReader(PDFfile)
    text = ""
    for i in range(pdfread.getNumPages()):
        text += pdfread.getPage(i).extractText()
print(text)
```

---

### 2. Google Scholar Search Automation

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

driver = webdriver.Chrome('/path/to/chromedriver')  # Update this path
driver.get('https://scholar.google.com/')

search_box = driver.find_element(By.NAME, "q")
search_box.send_keys("Your extracted text here")
search_box.send_keys(Keys.RETURN)
```

---

### 3. Optional: Metadata & Single Page

```python
info = pdfread.getDocumentInfo()
print("Metadata:", info)

first_page = pdfread.getPage(0)
print("Page 1 Text:", first_page.extractText())

print("Number of pages:", pdfread.getNumPages())
```

---

## 📄 License

MIT License — Free for personal or commercial use.

---

## 🤝 Contribute / Extend

Want to improve this? Add batch PDF support, citation extraction, or integration with Zotero / Notion. PRs welcome.

