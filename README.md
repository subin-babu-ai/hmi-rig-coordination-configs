# Team Configuration

This repository contains JSON configuration files for each team. Follow the instructions below to add a new team, edit an existing one, or submit your changes.

---

## File Structure

All team configuration files live in the `/teams` folder. Each team has its own `.json` file named after the team label (e.g., `hmi.json`).

```
/teams
  ├── hmi.json
  ├── chassis.json
  └── ...
```

---

## JSON Schema

Every team file must include **all** of the following fields — they are all required.

| Field | Type | Description |
|---|---|---|
| `label` | string | Unique team identifier (should match the filename) |
| `nudge_delay_secs` | number | Seconds before a nudge reminder is sent |
| `kick_vote_delay_secs` | number | Seconds before a kick vote can be initiated |
| `auto_reminder_secs` | number | Seconds before an automatic reminder is triggered |
| `rigs` | array | List of rig objects belonging to the team |

Each object in the `rigs` array must have:

| Field | Type | Description |
|---|---|---|
| `name` | string | Unique name of the rig |
| `logo` | string | Emoji or icon representing the rig |

### Example — `teams/hmi.json`

```json
{
  "label": "hmi",
  "nudge_delay_secs": 600,
  "kick_vote_delay_secs": 1500,
  "auto_reminder_secs": 1200,
  "rigs": [
    { "name": "zeus",   "logo": "⚡" },
    { "name": "hades",  "logo": "💀" },
    { "name": "hera",   "logo": "👑" },
    { "name": "ares",   "logo": "⚔️" },
    { "name": "kbbq",   "logo": "🔥" },
    { "name": "raichu", "logo": "🐭" }
  ]
}
```

---

## Adding a New Team

1. Create a new file inside the `/teams` folder. Name it `<team-label>.json` (e.g., `teams/autopilot.json`).
2. Copy the structure from the example above and fill in **all** fields with the appropriate values for the new team.
3. Make sure every field is present — missing fields will cause validation errors.
4. Ensure the `label` value matches the filename (without the `.json` extension).

---

## Editing an Existing Team

1. Open the team's JSON file in the `/teams` folder (e.g., `teams/hmi.json`).
2. Update the properties you need to change (timing values, rigs, etc.).
3. Do **not** remove any required fields. All fields must remain present.
4. To add a new rig, append an object with `name` and `logo` to the `rigs` array.
5. To remove a rig, delete its object from the `rigs` array.

---

## Submitting Your Changes (Pull Request)

### 1. Clone the repository

```bash
git clone https://github.com/<org>/<repo-name>.git
cd <repo-name>
```

### 2. Create a new branch

Name your branch descriptively based on your change:

```bash
git checkout -b add-team-autopilot
# or
git checkout -b update-hmi-rigs
```

### 3. Make your changes

Add or edit the relevant JSON file(s) in the `/teams` folder.

### 4. Commit and push

```bash
git add teams/<your-file>.json
git commit -m "Add autopilot team config"
git push origin your-branch-name
```

### 5. Open a Pull Request

1. Go to the repository on GitHub.
2. You should see a banner prompting you to open a pull request for your recently pushed branch. Click **"Compare & pull request"**.
3. Set the base branch to **`main`**.
4. Add a clear title and description of what you changed and why.
5. Click **"Create pull request"**.

### 6. Get it reviewed and merged

- Request a review from a team member or the repo owner.
- Address any feedback by pushing additional commits to the same branch.
- Once approved, the reviewer (or you, if you have permission) can click **"Merge pull request"**.

### 7. Wait for deployment

After the pull request is merged into `main`, I will deploy a new version of the app with the changes.

---

## Quick Checklist

- [ ] File is in the `/teams` folder
- [ ] Filename matches the `label` field
- [ ] All required fields are present (`label`, `nudge_delay_secs`, `kick_vote_delay_secs`, `auto_reminder_secs`, `rigs`)
- [ ] Every rig has both `name` and `logo`
- [ ] JSON is valid (no trailing commas, proper quoting)
- [ ] Pull request targets `main`
