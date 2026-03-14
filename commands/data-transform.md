Transform data using ETL pipeline.

Usage: /data-transform <source> <target> [operations]

## Operations
- `--drop-nulls` - Remove null rows
- `--fill-nulls=<method>` - Fill nulls (mean, median, ffill)
- `--drop-duplicates` - Remove duplicates
- `--aggregate=<level>` - Aggregate (daily, weekly, monthly)
- `--add-indicators` - Add trading indicators

## Process
1. Extract: Load source file
2. Transform: Apply operations
3. Validate: Check data quality
4. Load: Save to target

## Trading Data
Add technical indicators:
- SMA (20, 50)
- RSI (14)
- MACD (12, 26, 9)
- Bollinger Bands

Reference: C:\Chatgpt_Codex\_skills\data-pipeline\templates\trading-pipeline.py
