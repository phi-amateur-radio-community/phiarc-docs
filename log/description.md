# phiarc-docs
**Document Log Specification**

This repository is used for long-term document and log management.
The log directory is dedicated to year-based, structured financial records.

All records follow a unified directory structure and field specification to ensure consistency, traceability, and long-term maintainability.

## Directory Structure

Financial logs are stored under Document/log, organized by year → category → monthly files.


Document/

    └── log
        ├── 2025
        │   └── finance
        │       ├── 01.md
        │       ├── 02.md
        │       └── ...
        ├── 2026
        │   └── finance
        │       ├── 01.md
        │       └── ...
        └── ...


## Structure Rules

log/

    Root directory for all logs

log/[year]/

    Logs grouped by year (e.g. 2025, 2026)


log/[year]/finance/

    Financial log category
(additional categories may be added later)

***Monthly log files***

File names use two-digit months: 01.md – 12.md

Each file contains all records for that month

***Monthly Log Format***

Each financial record occupies one line.
Field order and meaning are fixed and must not be altered.

***Field Order***

    ID | Purpose | Amount | Currency | Processor | Date

## Field Definition

***Field	Description***

ID	Three-digit number, zero-padded (000–999), resets each month
Purpose	Description of the expense or income
Amount	Numeric value only, no currency symbols
Currency	Standard currency unit
Handler	Person who decided or approved the expense
Status	Current processing status
Day	Day of the month only (no year or month)
Currency Units

Currency units must use standard abbreviations:

    CNY, USD, JPY, EUR

Currency symbols (¥, $, €, etc.) are not allowed.

Example

    000 | Office supplies | 350 | CNY | Alice | 3
    001 | Cloud service   | 20  | USD | Bob   | 5


## Notes:

IDs are sequential within the same month
The Day field represents the day number of the current month only
Status values must be semantically clear

***Annual Archiving***

At the end of each year, logs from the previous year must be archived
Archive the entire yearly directory as a compressed file

Example:

    tar -czf log-2025.tgz log/2025


***After archiving:***

Keep the compressed file for long-term storage
The original yearly directory may be removed or marked read-only