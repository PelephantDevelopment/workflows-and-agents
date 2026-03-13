# LinkedIn Profile Comparison Extended

Extended version of the LinkedIn profile comparison workflow that includes conditional logic to detect when fields have changed.

## What's Different

This workflow adds:
- **IF node** - Checks if any field has changed (not an exact match)
- **Format Changes node** - Outputs only the changed fields in a clean format
- **No Changes node** - Separate path when all fields match

## Workflow Structure

```
Start → Your Known Data → Fetch Profile (PDL) → Compare Data → Has Changes?
                                                                    ├─ true → Format Changes
                                                                    └─ false → No Changes
```

## How It Works

1. Compares your known data with fetched LinkedIn data (same as basic version)
2. **IF node** checks the `has_changes` boolean field
3. If changes detected → **Format Changes** node outputs only the changed fields
4. If no changes → **No Changes** node (no action needed)

## Output When Changes Detected

```json
{
  "linkedin_url": "https://ch.linkedin.com/in/ramona-schindler",
  "summary": "3 of 5 fields match",
  "changes_detected": 2,
  "changed_fields": [
    {
      "field": "Position",
      "known": "Chief Executive Officer",
      "fetched": "Managing Director",
      "status": "Different"
    },
    {
      "field": "Location",
      "known": "Zurich, Switzerland",
      "fetched": "Not found",
      "status": "Data missing"
    }
  ]
}
```

## Next Steps

After the **Format Changes** node, you can add:
- **Email node** (requires Gmail/SMTP credentials setup)
- **Slack node** to post to a channel
- **Webhook node** to send to another system
- **Database node** to log changes

## Setup

Same as the basic version - import the JSON, add your PDL API key, and edit the known data fields.
