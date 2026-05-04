# Test Automation Project

This project automates frontend testing for the PixelsSuite chat translator using Python, Playwright, and an Excel test case file.  
The script reads Singlish input values from the Excel sheet, enters them into the web application, captures the Sinhala output, and writes the actual result and test status back into the Excel file.

## Project Files

- `test_automation.py` - Main automation script
- `Assignment 1 - Test cases.xlsx` - Excel file containing test cases

## Requirements

Make sure the following are installed before running the project:

- Python 3.10 or newer
- `playwright`
- `openpyxl`
- Chromium browser for Playwright

## Install Dependencies

Run these commands:

```bash
pip install playwright openpyxl
playwright install chromium
```

## How to Start the Project

From the project folder, run:

```bash
python test_automation.py
```

This will:

- Open the translator web application
- Read test data from the Excel file
- Execute the test cases
- Save actual outputs and pass/fail status back into the Excel sheet

## Default Behavior

The script uses these default settings:

- Excel file: `Assignment 1 - Test cases.xlsx`
- Default URL: `https://www.pixelssuite.com/chat-translator`
- Default sheet name: ` Test cases`

## Optional Run Example

You can also run the script with extra options:

```bash
python test_automation.py --headless --keep-open
```

Some supported arguments include:

- `--excel` - Specify a custom Excel file
- `--sheet` - Specify a sheet name
- `--url` - Specify a custom frontend URL
- `--headless` - Run without opening the browser UI
- `--keep-open` - Keep the browser open after execution

## Output

After execution, the script updates the Excel file with:

- Actual output
- Test status such as `PASS`, `FAIL`, `COLLECTED`, or `UI Error`

## Author

- Author Name: `ARUNPRAGASH.S`
- IT No: `IT23314092`
