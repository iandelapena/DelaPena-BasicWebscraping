# 🎮 Starink Webscraping

A Python-based web scraper that collects game information from **PCGamingWiki** using **Playwright** and **BeautifulSoup**.

The scraper:
- 📂 Fetches game subcategories
- 🎯 Extracts game pages from each subcategory
- 🧠 Scrapes key data:
  - 🏷️ Title
  - 👨‍💻 Developer
  - 🏢 Publisher
  - 🎮 Genre
  - 🖥️ Platform release dates
- 📊 Exports results into a clean HTML table

---

## ✨ Features

- 🌐 Browser automation with Playwright
- 🧾 HTML parsing using BeautifulSoup
- ⚡ Dynamic page rendering support
- 📄 HTML report generation
- 🔧 Easy to customize and extend

---

## 🧰 Requirements

- 🐍 Python 3.9+
- 🌍 Chromium browser (installed via Playwright)

---

## 📦 Installation

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/starink-webscraping.git
cd starink-webscraping
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Install Playwright browsers

```bash
playwright install
```

---

## 🚀 Usage

Run the scraper:

```bash
python scraper.py
```

After execution, results will be saved as:

```bash
📄 SCRAPE_RESULTS.html
```

---

## 📊 Example Output

| 📂 Subcategory | 🏷️ Title | 👨‍💻 Developer | 🏢 Publisher | 🎮 Genre | 🖥️ Platforms |
|---|---|---|---|---|---|
| Action games | Example Game | Example Dev | Example Publisher | FPS | Windows: 2020 |

---

## 🗂️ Project Structure

```text
.
├── 🐍 scraper.py
├── 📦 requirements.txt
├── 📘 README.md
└── 📄 SCRAPE_RESULTS.html
```

---

## ⚙️ How It Works

### 1. 📂 Fetch Category Pages
Uses Playwright to load dynamic pages from PCGamingWiki.

### 2. 🧭 Extract Subcategories
Collects links from:
- `#mw-subcategories`

### 3. 🎯 Extract Games
Collects game links from:
- `#mw-pages`

### 4. 🧠 Scrape Game Information
Extracts structured data from:
- `#infobox-game`

### 5. 📊 Export Results
Generates a clean HTML report for viewing.

---

## 🛠️ Configuration

### 🎮 Change number of games scraped

```python
game_links = get_games_from_subcategory(sub_url, limit=5)
```

### 📂 Change number of subcategories scraped

```python
for sub_name, sub_url in subcategories[:1]:
```

---

## ⚠️ Notes

- ⏳ Add delays responsibly to avoid rate limiting
- 🔄 Website structure may change over time
- 🎓 Intended for educational and research purposes

---

## 📜 License

MIT License
