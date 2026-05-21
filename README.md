# Starlink Data Usage Scraper

A Python tool that extracts **Starlink internet usage data** from saved HTML reports and converts it into a clean CSV file.

It automatically:
- Detects HTML files in the folder
- Lets you choose which file to process
- Extracts usage bar data from the Starlink dashboard UI
- Detects billing cycle start date
- Converts pixel values into GB usage estimates
- Exports results into CSV format

---

## Features

- Auto-detects `.html` usage files
- Parses Starlink dashboard HTML reports
- Converts bar chart heights into estimated GB usage
- Auto-detects billing cycle start date
- Outputs clean `data_usage.csv`
- Simple command-line interface

---

## Requirements

- Python 3.9+
- BeautifulSoup4
- lxml

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/starlink-data-scraper.git
cd starlink-data-scraper
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

---

## Usage

### Step 1: Add your Starlink HTML report(s)
Place your exported **Starlink usage `.html` files** in the same folder as the script.

### Step 2: Run the script

```bash
python scraper.py
```

### Step 3: Select file

Example prompt:

```
Found the following files:
[1] starlink_report.html
[2] usage.html
```

Enter the number of the file you want to process.

---

## Output

After execution, the script generates:

```text
data_usage.csv
```

### Example:

| Date | Data Usage (GB) |
|------|-----------------|
| 05/17/2026 | 3.42 |
| 05/18/2026 | 4.10 |

---

## How It Works

### 1. File Detection
Scans directory for `.html` files.

### 2. HTML Parsing
Uses BeautifulSoup to extract:
- Total Starlink data usage
- Bar chart elements from dashboard

### 3. Data Conversion
Converts pixel bar heights into GB values using proportional scaling.

### 4. Billing Cycle Detection
Attempts to detect Starlink billing cycle start date (default: 17th of month).

### 5. CSV Export
Exports structured daily usage into `data_usage.csv`.

---

## Notes

- Works with Starlink dashboard HTML exports only
- Accuracy depends on UI structure consistency
- If Starlink updates their UI, selectors may need adjustments

---

## License

MIT License
