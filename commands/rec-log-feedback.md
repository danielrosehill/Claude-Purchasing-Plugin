---
description: Record like/dislike/nuanced feedback against a past recommendation and update the preference profile so future suggestions improve.
---

# /log-feedback

Close the loop on a previous recommendation. This is the single most important command for improving recommendation quality over time.

## Steps

### 1. Identify the recommendation

If the user named one inline (`/log-feedback "The Rest is History — Constantinople"`), match it against `recommendations/`. Otherwise:

- Run the same listing logic as `/recommendations --unrated`
- Ask the user to pick (AskUserQuestion or free-text reference)

### 2. Capture reaction

Ask the user (AskUserQuestion):

- **Reaction:** loved it / liked it / mixed / didn't like it / didn't engage
- **Why:** free-text — the *reason* matters more than the verdict for future tuning

If the user gives a nuanced answer ("loved the host, hated the topic"), capture both dimensions.

### 3. Write the feedback file

Create `feedback/YYYY-MM-DD-<rec-slug>.md` with:

```markdown
---
recommendation: <relative path to the rec file>
reaction: loved | liked | mixed | disliked | no-engage
date: YYYY-MM-DD
---

# <rec title>

**Why:** <user's reasoning>

**Tags to lean into:** <comma-separated>
**Tags to avoid:** <comma-separated>
```

### 4. Update the preference profile

This is the load-bearing step. Open `memory/preferences.md` and:

- If "loved" / "liked": add specifics to **Strong likes** (creator, theme, style, etc.)
- If "disliked" / "no-engage": add specifics to **Strong dislikes / no-go** — but only if the user's reason suggests a generalisable pattern, not a one-off
- If "mixed": update **Constraints** or note in **Open questions / experiments**
- Append a dated line to **Update log** describing the change

Be conservative — don't over-generalise from a single data point. If a single dislike isn't a clear pattern, leave the profile alone and just record the feedback file.

### 5. Confirm

Tell the user what feedback was logged and what (if anything) changed in the preference profile.
