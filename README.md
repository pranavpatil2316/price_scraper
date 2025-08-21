# 📘 E-commerce Price Monitoring Scraper

This project is a **web scraping tool** built using **Python, BeautifulSoup, and Pandas**.  
It scrapes product data (book name, price, and availability) from the demo e-commerce site  
[Books to Scrape](http://books.toscrape.com/), cleans the data and visualizes the price distribution.

---

## 🎯 Features
- Scrapes **Book Title, Price (£), Availability** from multiple pages.
- Cleans data by removing duplicates and missing values.
- Saves data into **CSV file (`clean_books_data.csv`)**.
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
git clone https://github.com/pranavpatil2316/Ecommerce_Price_Monitoring_Scraper.git
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

# 🐍 `ecommerce_price_scraper.py`

```python
# ===============================
# Step 1: Install Required Libraries
# ===============================
!pip install requests beautifulsoup4 pandas matplotlib
# ===============================
# Step 2: Import Libraries
# ===============================
import requests
from bs4 import BeautifulSoup
import pandas as pd
import matplotlib.pyplot as plt

# ===============================
# Step 3: Define Scraper Function
# ===============================
def scrape_books(base_url, pages=3):  # scrape first 3 pages (can increase)
    books = []
    for page in range(1, pages+1):
        url = f"{base_url}catalogue/page-{page}.html"
        response = requests.get(url)
        soup = BeautifulSoup(response.text, "html.parser")

        for item in soup.select(".product_pod"):
            name = item.h3.a["title"]
            price = item.select_one(".price_color").text.strip()
            availability = item.select_one(".availability").text.strip()
            
            books.append({
                "Product Name": name,
                "Price (£)": price,
                "Availability": availability
            })
    return books

# ===============================
# Step 4: Scrape Data
# ===============================
BASE_URL = "http://books.toscrape.com/"
books_data = scrape_books(BASE_URL, pages=5)  # scrape 5 pages for demo
df = pd.DataFrame(books_data)

print("Sample Data:")
print(df.head())

# ===============================
# Step 5: Data Cleaning
# ===============================
df["Price (£)"] = df["Price (£)"].str.replace("£", "").astype(float)
df.drop_duplicates(inplace=True)
df.dropna(inplace=True)

# ===============================
# Step 6: Save Dataset
# ===============================
df.to_csv("clean_books_data.csv", index=False)
print("\nData saved as 'clean_books_data.csv'")

# ===============================
# Step 7: Visualization
# ===============================
plt.figure(figsize=(8,5))
df["Price (£)"].hist(bins=15, edgecolor="black")
plt.xlabel("Price (£)")
plt.ylabel("Number of Books")
plt.title("Price Distribution of Books")
plt.show()
```
