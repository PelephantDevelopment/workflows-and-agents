# Workflows & Agents

Collection of n8n workflows and automation use cases for Pelephant.

## Use Cases

### 1. [LinkedIn Profile Comparison](./linkedin-profile-comparison/)
Fetch LinkedIn profile data via People Data Labs API and compare it with known person information. Shows which fields match, partially match, or differ.

**Type:** n8n workflow
**Nodes:** Manual Trigger → Set (known data) → HTTP Request (PDL API) → Code (compare)

### 2. [LinkedIn Profile Comparison Extended](./linkedin-profile-comparison-extended/)
Extended version with conditional logic. Detects when fields have changed and outputs only the changed fields. Ready to connect to email, Slack, or other notification nodes.

**Type:** n8n workflow
**Nodes:** Manual Trigger → Set → HTTP Request → Code → IF (has changes?) → Format Changes / No Changes

### 3. [Claude Projects: Person Research](./claude-projects-person-research/)
Workshop material for creating Claude Projects that research people and generate PowerPoint dossiers. 4-step tutorial with instructions, Python templates for corporate design, and photo handling.

**Type:** Claude Projects workshop
**Features:** Web research → Structured dossier → PowerPoint generation → Corporate design

### 4. [Claude Agent: File Organizer](./claude-agent-file-organizer/)
Workshop for building a Claude Cowork agent that automatically sorts 50+ files by content. Includes skills, sub-agents, and scheduled tasks. Reads file content, categorizes documents, renames files, and creates inventory lists.

**Type:** Claude Cowork agent workshop
**Features:** Content analysis → Auto-categorization → File renaming → Inventory generation → Scheduled execution

---

More use cases coming soon.
