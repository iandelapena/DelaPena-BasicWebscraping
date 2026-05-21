# Starlink Daily Usage Extractor

This system extracts daily internet usage data from Starlink billing responses and converts it into a clean CSV report for easy tracking and analysis. It works by inspecting the Starlink account network traffic in the browser, copying the `billingCyclesAnnotated` JSON response, and processing the daily usage values with Python. The generated CSV file can be opened in Excel, Google Sheets, or any spreadsheet application to monitor bandwidth usage over time.

---

# 📂 Files

```bash
project-folder/
├── starlink_scraper.py
├── starlink_data.json
└── starlink_daily_usage.csv
```

---

# 🌐 Step 1 — Get the JSON Data

1. Go to:

```text
https://www.starlink.com/account/home
```

2. Log into your account

3. Open Developer Tools:

```bash
F12
```

4. Open the:

```text
Network
```

tab

5. Refresh the page

6. Search for:

```text
annotated
```

7. Open the:

```text
Response
```

tab

8. Copy the full JSON response

9. Create a file named:

```bash
starlink_data.json
```

10. Paste the JSON into the file

---

# 🧠 Step 2 — Create the Script

Create:

```bash
starlink_scraper.py
```

Paste:

```python
import json
import csv
from datetime import datetime, timedelta
from pathlib import Path

json_file = Path(__file__).parent / 'starlink_data.json'

with open(json_file, 'r') as file:
    payload = json.load(file)

extracted_rows = []

billing_cycles = payload.get("content", {}).get("billingCyclesAnnotated", [])

for cycle in billing_cycles:
    start_date_str = cycle.get("startDate").split("T")[0]
    start_date = datetime.strptime(start_date_str, "%Y-%m-%d")

    daily_usages = cycle.get("dailyData", [])

    for index, usage_wrapper in enumerate(daily_usages):
        current_day = start_date + timedelta(days=index)
        current_day_str = current_day.strftime("%Y-%m-%d")

        if usage_wrapper and len(usage_wrapper) > 0:
            gb_value = round(usage_wrapper[0], 2)
        else:
            gb_value = 0.0

        extracted_rows.append([current_day_str, f"{gb_value} GB"])

output_filename = "starlink_daily_usage.csv"

with open(output_filename, "w", newline="", encoding="utf-8") as f:
    writer = csv.writer(f)
    writer.writerow(["Date", "Data Usage"])
    writer.writerows(extracted_rows)

print(f"Generated '{output_filename}' with {len(extracted_rows)} entries.")
```

---

# ▶️ Step 3 — Run

```bash
python starlink_scraper.py
```

or:

```bash
python3 starlink_scraper.py
```

---

# ✅ Output

Creates:

```bash
starlink_daily_usage.csv
```

Example:

```csv
Date,Data Usage
2025-11-17,12.5 GB
2025-11-18,10.2 GB
```

---
