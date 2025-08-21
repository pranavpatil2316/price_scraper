# 📘 E-commerce Price Monitoring Scraper

This project is a **web scraping tool** built using **Python, BeautifulSoup, and Pandas**.  
It scrapes product data (book name, price, and availability) from the demo e-commerce site  
[Books to Scrape](http://books.toscrape.com/), cleans the data and visualizes the price distribution.

---

## 🎯 Features
- Scrapes **Book Title, Price (£), Availability** from multiple pages.
- Cleans data by removing duplicates and missing values.
- Saves data into **CSV file (`clean_books_data_inr.csv`)**.
- Generates a **histogram** of book price distribution in INR.

---

## 🛠 Technologies Used
- **Python 3**
- **Requests** (for HTTP requests)
- **BeautifulSoup4** (for HTML parsing)
- **Pandas** (for data cleaning & exporting)
- **Matplotlib** (for visualization)

---

## ⚡ Installation

Clone the repository:
```bash
git clone https://github.com/your-username/Ecommerce_Price_Monitoring_Scraper.git
cd Ecommerce_Price_Monitoring_Scraper
````

Install dependencies:

```bash
!pip install requests beautifulsoup4 pandas matplotlib
```
---

## 📊 Example Output

Sample CSV data:

| Product Name         | Price (£) | Price (₹) | Availability |
| -------------------- | --------- | --------- | ------------ |
| A Light in the Attic | 51.77     | 5435.85   | In stock     |
| Tipping the Velvet   | 53.74     | 5642.70   | In stock     |
| Soumission           | 50.10     | 5260.50   | In stock     |

Histogram (Price Distribution):

📈 *(Generated when you run the script)*

---

## ⚖️ Ethical Note

This scraper is built for **educational purposes only** using the practice website
[Books to Scrape](http://books.toscrape.com/).
Do **not** scrape real e-commerce websites like Amazon/Flipkart without permission.

---
