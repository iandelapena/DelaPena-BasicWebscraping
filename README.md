# Starlink Daily Usage Scraper

This script processes intercepted Starlink billing data stored in a JSON file and converts it into a clean, human-readable CSV format showing daily internet usage.

## What it does

- Loads a JSON file containing Starlink billing cycle data
- Scrapes daily usage values from nested structures
- Converts cycle-relative usage into actual calendar dates
- Rounds usage values to two decimal places
- Outputs a CSV file with:
  - Date
  - Data Usage

## Input Format

The script expects a JSON file structured like:

- `content`
  - `billingCyclesAnnotated`
    - `startDate` (ISO 8601 format)
    - `dailyData` (list of lists, where the first value is GB usage)

## Output

A CSV file named:
