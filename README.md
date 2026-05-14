# Test Automation Project

This project automates UI-based testing for the PixelsSuite chat translator using Python, Playwright, and an Excel workbook of test cases.

The script reads Singlish input values from Excel, submits them to the web application, captures the Sinhala output, and writes the actual result plus test status back into the workbook.

## Project Files

- `IT23314092_test_automation.py` - main automation script
- `IT23314092_Assignment 1 - Test cases.xlsx` - test case workbook
- `Assignment 1_Test cases.rtf` - supporting document
- `IT23314092_README.md` - project documentation

## Requirements

Install the following before running the project:

- Python 3.10 or newer
- `playwright`
- `openpyxl`
- Chromium for Playwright

## Install Dependencies

```bash
pip install playwright openpyxl
playwright install chromium
```

## How To Run

From the project folder:

```bash
python IT23314092_test_automation.py --excel "IT23314092_Assignment 1 - Test cases.xlsx"
```

The script will:

- open the translator web application
- load the Excel workbook
- detect the header row if one is not provided
- read input values row by row
- capture actual Sinhala output
- write `Actual output` and `Status` values back into the workbook

## Default Behavior

The script currently uses these defaults:

- frontend URL: `https://www.pixelssuite.com/chat-translator`
- sheet name: ` Test cases`
- header scan range: first 30 rows
- wait after submit: `5000` ms
- retry count for output polling: `8`
- retry wait: `1000` ms
- typing delay: `30` ms
- timeout: `60000` ms

If the expected output column is present, rows are marked as:

- `PASS`
- `FAIL`

If no expected value exists, the row is marked:

- `COLLECTED`

If browser interaction fails for a row, the row is marked:

- `UI Error`

## Supported Command-Line Options

```bash
python IT23314092_test_automation.py --excel "IT23314092_Assignment 1 - Test cases.xlsx" --headless --keep-open
```

Available options:

- `--excel` - path to the input workbook
- `--sheet` - sheet name to use
- `--header-row` - explicit header row number
- `--max-header-scan-rows` - number of rows to scan when auto-detecting headers
- `--input-col` - custom input column name
- `--expected-col` - custom expected output column name
- `--actual-col` - custom actual output column name
- `--status-col` - custom status column name
- `--url` - custom frontend URL
- `--output` - output workbook path
- `--save-every` - save progress after every N processed rows
- `--headless` - run without showing the browser
- `--wait-ms` - wait time after submit
- `--retries` - retry attempts when waiting for translated output
- `--retry-wait-ms` - delay between retries
- `--type-delay-ms` - typing delay for text entry
- `--timeout-ms` - Playwright timeout
- `--slow-mo-ms` - slow browser actions for debugging
- `--keep-open` - keep the browser open after execution when not headless

## Excel Column Detection

The script can automatically match common column names.

Input column candidates include:

- `Singlish`
- `Input`
- `Singlish Input`
- `Test Input`
- `Source`
- `Sentence`
- `Text`

Expected output column candidates include:

- `Sinhala`
- `Expected_Output`
- `Expected Output`
- `Expected output`
- `Expected`
- `Expected Sinhala`

If `Actual output` or `Status` columns do not exist, the script creates them.

## Notes

- The workbook is updated in place unless `--output` is provided.
- In this repository, it is safest to pass `--excel "IT23314092_Assignment 1 - Test cases.xlsx"` explicitly.
- The script falls back to the active sheet if the requested sheet name is not found.
- The default sheet name includes a leading space: ` Test cases`.

## Author

- Author Name: `ARUNPRAGASH.D`
- IT No: `IT23314092`
