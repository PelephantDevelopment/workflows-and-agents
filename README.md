# Workflows & Agents

Collection of n8n workflows and automation use cases for Pelephant.

## Use Cases

### 1. [LinkedIn Profile Comparison](./linkedin-profile-comparison/)
Fetch LinkedIn profile data via People Data Labs API and compare it with known person information. Shows which fields match, partially match, or differ.

**Nodes:** Manual Trigger → Set (known data) → HTTP Request (PDL API) → Code (compare)

### 2. [LinkedIn Profile Comparison Extended](./linkedin-profile-comparison-extended/)
Extended version with conditional logic. Detects when fields have changed and outputs only the changed fields. Ready to connect to email, Slack, or other notification nodes.

**Nodes:** Manual Trigger → Set → HTTP Request → Code → IF (has changes?) → Format Changes / No Changes

---

More use cases coming soon.
