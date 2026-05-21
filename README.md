# Starlink Daily Usage Extractor

## Overview

This script processes intercepted Starlink billing data stored in JSON format and converts it into a structured CSV file containing daily internet usage per billing cycle.

It extracts:
- Date of usage (calculated per day in the billing cycle)
- Data usage in GB (rounded to 2 decimal places)

The output is saved as a human-readable CSV file.

---

## Features

- Parses nested Starlink billing JSON structure
- Converts billing cycles into daily records
- Automatically calculates dates using the cycle start date
- Handles missing or empty usage values safely
- Outputs clean CSV with headers

---

## Requirements

- Python 3.8 or higher
- No external dependencies (uses only standard library: json, csv, datetime)

---

## Input Format

The script expects a JSON file with a structure like:

{
  "content": {
    "billingCyclesAnnotated": [
      {
        "startDate": "2025-11-17T00:00:00Z",
        "dailyData": [
          [1.23],
          [2.34],
          []
        ]
      }
    ]
  }
}

---

## Configuration

Update the file path in your script:

open(r'C:\Users\user\Documents\DelaPeñaJoseBrian_Basic-Webscraping\starlink_data.json', 'r')

Or use a relative path:

open('starlink_data.json', 'r')

---

## Output

The script generates:

starlink_daily_usage.csv

Example output:

Date,Data Usage
2025-11-17,1.23 GB
2025-11-18,2.34 GB

---

## How to Run

python script_name.py

---

## Notes

- Each billing cycle is expanded into daily entries based on index position.
- Missing values are stored as 0.0 GB.
- Dates are derived from the billing cycle start date.

---
