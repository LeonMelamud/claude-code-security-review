# Claude Code Security Review - Agent Instructions

## Testing the Skill Locally

Before pushing a new version to Git or publishing it to the registries, you should validate the skill's structure and contents using the Tessl CLI.

1. **Install the Tessl CLI** (if not already installed):
   ```bash
   curl -fssl https://get.tessl.io | sh
   ```
2. **Validate the skill against best practices**:
   ```bash
   tessl skill lint .
   ```
   This checks the `SKILL.md` format, required frontmatter fields, and markdown validity.
3. **Get a comprehensive review**:
   ```bash
   tessl skill review .
   ```
   This provides detailed recommendations for improving the skill.

Fix any errors reported by these commands before proceeding to publish.

## Publishing a New Version

When a new version of this skill is created, it needs to be published and updated in the following AI agent skill registries:

### 1. skills.sh / tessl.io (Tessl ecosystem)
This registry uses a decentralized telemetry model. To publish or update the skill, run the following command locally to trigger the telemetry and index it on their leaderboard and registry:
```bash
npx skills add LeonMelamud/claude-code-security-review -a claude-code -y
```

### 2. skillsmp.com
This marketplace automatically indexes skills from GitHub based on repository topics.
- **Requirement:** Ensure the GitHub repository has the topics `claude-skills` and `claude-code-skill` (already added).
- **Action:** No manual action is required for updates. Their crawler runs a daily sync and will automatically pick up changes from the `main` branch.

### 3. skillsdirectory.com
This directory requires manual submission and authentication.
- **Action:** Go to [https://www.skillsdirectory.com/submit](https://www.skillsdirectory.com/submit)
- **Requirement:** You must sign in with your GitHub account to submit or update the repository. This step cannot be automated by an AI agent.
