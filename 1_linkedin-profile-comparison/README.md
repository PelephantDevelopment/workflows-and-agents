# LinkedIn Profile Comparison - n8n Workflow

A simple n8n workflow that fetches LinkedIn profile data and compares it with information you already have about a person.

## What This Workflow Does

```
Start Flow → Your Known Data → Fetch LinkedIn Profile (PDL) → Compare Data
```

1. **Start Flow** - Manual trigger to run the workflow
2. **Your Known Data** - A Set node where you enter the LinkedIn URL and the person's details you already know (name, position, company, location, industry)
3. **Fetch LinkedIn Profile (PDL)** - Calls the [People Data Labs API](https://www.peopledatalabs.com/) to fetch current profile information from LinkedIn
4. **Compare Data** - A Code node that compares your known data with the fetched data and shows which fields match, partially match, or differ

## How to Set It Up

### Step 1: Import the Workflow

1. Open your n8n instance
2. Go to **Workflows** → click **Add Workflow** (or the `+` button)
3. Click the **three dots menu** (⋯) in the top right → **Import from File**
4. Select the file `linkedin-profile-comparison.json` from this repository
5. The workflow will appear with 4 connected nodes

### Step 2: Add Your API Key

1. Click on the **"Fetch LinkedIn Profile (PDL)"** node (the HTTP Request node)
2. Under **Query Parameters**, find the `api_key` parameter
3. Replace `YOUR_PDL_API_KEY` with your actual People Data Labs API key
4. Click **Save**

> **Get a PDL API key:** Sign up at [peopledatalabs.com](https://www.peopledatalabs.com/) — they offer free credits to get started.

TestKey: 4479aba87965e1ef0d7f5ec62cef7d4588cfd5918e8808208e566b9e992f901a

### Step 3: Enter Your Known Data

1. Click on the **"Your Known Data"** node (the Set node)
2. Edit the fields with the person you want to look up:
   - `linkedin_url` → The person's LinkedIn profile URL
   - `known_name` → The name you have on file
   - `known_position` → The job title you have on file
   - `known_company` → The company you have on file
   - `known_location` → The location you have on file
   - `known_industry` → The industry you have on file
3. Click **Save**

### Step 4: Run the Workflow

1. Click the **"Test Workflow"** button (or press `Ctrl+Enter`)
2. The workflow will execute all 4 nodes
3. Click on the **"Compare Data"** node to see the results

## Understanding the Output

The **Compare Data** node produces a result like this:

```json
{
  "summary": "4 of 5 fields match",
  "linkedin_url": "https://ch.linkedin.com/in/ramona-schindler",
  "comparison": {
    "name": {
      "known": "Ramona Schindler",
      "fetched": "Ramona Schindler",
      "result": "Exact match"
    },
    "position": {
      "known": "Managing Director",
      "fetched": "Managing Director",
      "result": "Exact match"
    },
    "company": {
      "known": "Example Advisory Group",
      "fetched": "Advisory Group AG",
      "result": "Partial match"
    },
    "location": {
      "known": "Zurich, Switzerland",
      "fetched": "Zurich, Zurich, Switzerland",
      "result": "Partial match"
    },
    "industry": {
      "known": "Management Consulting",
      "fetched": "Staffing and Recruiting",
      "result": "Different"
    }
  },
  "match_count": 4,
  "total_fields": 5
}
```

Each field shows:
- **known** — what you entered
- **fetched** — what PDL returned from LinkedIn
- **result** — `Exact match`, `Partial match`, `Different`, or `Data missing`

## Workflow Screenshot

After importing, your workflow should look like this:

```
[Start Flow] → [Your Known Data] → [Fetch LinkedIn Profile (PDL)] → [Compare Data]
```

4 nodes in a straight line, left to right.

## Notes

- Each API call uses **1 PDL credit**. Be mindful of your credit usage.
- The workflow uses only **standard n8n nodes**: Manual Trigger, Set, HTTP Request, and Code — no external plugins needed.
- The comparison is **case-insensitive** and supports partial matching (e.g., "Zurich" matches "Zurich, Switzerland").
