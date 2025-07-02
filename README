# **Web Scraping of Used Car Data from Carpages.ca**

**Developed By:** [M Aqeel Zafar](https://github.com/maqeelzafar047)\
**Purpose:** Educational Use Only

---

## **Overview**

This project focuses on **web scraping used car listings** from [Carpages.ca](https://www.carpages.ca), a popular Canadian automotive marketplace. The main objective is to collect relevant information such as:

- **Title**
- **Subtitle**
- **Color**
- **Price**
- **Dealer**
- **Mileage**
- **City**

This data is extracted from multiple pages of listings using **Python**, specifically the `requests` and `BeautifulSoup` libraries, and is stored in a structured format using `pandas`.

---

## **Libraries Used**

```python
import requests
from bs4 import BeautifulSoup
import time
import pandas as pd
```

- `requests`: For sending HTTP GET requests to fetch page content.
- `BeautifulSoup`: To parse and extract data from HTML.
- `time`: Used to implement delay (polite scraping).
- `pandas`: For organizing the data into a tabular format and saving it as CSV.

---

## **Scraping Logic**

The script loops through **6 pages** of car listings. For each page:

1. Constructs the URL dynamically.
2. Sends an HTTP request to fetch the HTML.
3. Parses the page using `BeautifulSoup`.
4. Extracts car details (title, price, kms, time posted).
5. Appends the data to a list of dictionaries.

```python
car_data = []

for page in range(1, 6):
    url = f"https://www.carpages.ca/used-cars/search/?pg={page}"
    response = requests.get(url)
    soup = BeautifulSoup(response.text, "html.parser")

    for listing in soup.select(".media.soft.push-none.rule"):
        title = listing.select_one(".h5").get_text(strip=True) if listing.select_one(".h5") else None
        price = listing.select_one(".price").get_text(strip=True) if listing.select_one(".price") else None
        kms = listing.select_one(".kms").get_text(strip=True) if listing.select_one(".kms") else None
        time_posted = listing.select_one("small").get_text(strip=True) if listing.select_one("small") else None

        car_data.append({
            "Title": title,
            "Price": price,
            "KMs": kms,
            "Time Posted": time_posted
        })

    print(f"Page {page} scraped successfully!")
    time.sleep(2)
```

---

## **Data Storage**

After scraping, the data is converted into a `pandas` DataFrame and saved to a `.csv` file.

```python
df = pd.DataFrame(car_data)
df.to_csv("carpages_data.csv", index=False)
```

---

## **Output File**

- **Output CSV:** `carpages_data.csv`
- This file contains structured data scraped from all 20 pages of car listings.

---

## **Key Highlights**

- Used polite scraping with `time.sleep(2)` between requests.
- Implemented dynamic page traversal with a `for` loop.
- Ensured code handles missing data safely using conditional checks.
- Saved data in a clean and structured format.

---

## **Disclaimer**

> This project is created by [**M Aqeel Zafar**](https://github.com/maqeelzafar047) and is intended **for educational purposes only**. It is not affiliated with or endorsed by **Carpages.ca**. Do not use this script for any commercial or abusive activities. Always respect websites' terms of service.

---

