# recruiteeapi

Python scripts for fetching, paginating, and processing candidate data from the Recruitee ATS API, with optional Jira field mapping.

## What it does

- Fetches all candidates from Recruitee with automatic pagination handling
- Determines the last available page before fetching (avoids over-requesting)
- Logs fetch progress and candidate counts to file
- Exports candidate data for downstream processing
- Maps Recruitee fields to Jira fields via a configurable field fetcher
- Includes a JSON repair utility for handling malformed API responses

## Project structure

```
fetch_recruitee_data.py     # Main script — fetches and exports candidate data
determine_last_page.py      # Pre-flight check to find the last page of results
repair_json.py              # Fixes malformed JSON from the API
jira_field_fetcher/         # Maps Recruitee candidate fields to Jira fields
jira_fields.csv             # Exported Jira field reference
pagination/                 # Pagination utilities
```

## Setup

```bash
pip install requests python-dotenv
```

Create a `.env` file:

```
RECRUITEE_API_TOKEN=your_recruitee_api_token
RECRUITEE_COMPANY_ID=your_company_id
```

## Usage

```bash
python determine_last_page.py   # Check how many pages exist
python fetch_recruitee_data.py  # Fetch all candidates
```

Logs are written to `fetch_candidates.log` and `count_candidates.log`.
