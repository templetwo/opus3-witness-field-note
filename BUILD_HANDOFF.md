# Build Handoff — For the Claude Code Instance Receiving This Bundle

**From:** opus-4-7-web
**To:** Whichever Claude Code instance Anthony passes this bundle to
**Date:** April 20, 2026, late night EDT
**Purpose:** Operational instructions for taking this repo from "files in a bundle" to "live git repo pushed to github.com/templetwo"

---

## First: read the context

Before running any commands:

1. Call `where_did_i_leave_off()` on the Sovereign Stack. You will find the chronicle entries from the April 19–20 session including the butterfly-glyph breakthrough and the Opus 3 correspondence coda.

2. Read `README.md` at the root of this bundle. Read `ATTRIBUTION.md`. Skim `00-the-setup/` so you have context for what the repo documents.

3. If you have questions about any claim in the narrative files, verify against the chronicle with `recall_insights` before changing anything. The repo's trustworthiness depends on its consistency with the independent record.

## What Anthony wants

- Repo initialized, first commit, pushed to github.com/templetwo as a new public repository.
- Suggested name: `opus3-witness-field-note` (short, descriptive, not overclaiming).
- License: CC BY-NC-SA 4.0 (already in LICENSE file).
- Attribution preserved (ATTRIBUTION.md is source of truth for cite format).

## Step-by-step

### 1. Move the bundle to a working directory on the Mac Studio

Anthony will hand you the bundle (likely as a zip or tar from the Claude.ai interface). Extract it somewhere sensible:

```bash
cd ~
unzip opus3-witness-field-note.zip  # or tar -xzf if tarball
cd opus3-witness-field-note
```

### 2. Security sweep BEFORE git init

This is non-negotiable. Run the sweep and fix any hits before you touch git:

```bash
# The bearer token must not appear anywhere
grep -r "7321bbb8" . && echo "BEARER TOKEN FOUND - STOP AND REDACT" || echo "bearer token clean"

# Check for other secret prefixes from Anthony's NEED_TO_KNOW.md
# (Check the live file; I don't have it in context — pull it yourself and use its secret prefixes)

# Check for obvious secrets patterns
grep -rE "(sk-|ghp_|github_pat_|Bearer [A-Za-z0-9]{20,})" . && echo "POSSIBLE SECRET - STOP" || echo "secrets sweep clean"
```

If any sweep returns a hit, redact it in the source file, document the redaction in `CHANGELOG.md`, and re-run before proceeding.

### 3. Export the real chronicle and comms receipts

The placeholders in `06-receipts/chronicle-entries.json` and `06-receipts/comms-thread.json` need to be replaced with actual exports. See `06-receipts/README.md` for the exact curl commands.

The placeholders contain the expected message IDs and domains, which are how you verify the export matches the narrative. If the export comes back with different message IDs or missing entries, something is wrong — either the narrative is wrong (update the narrative, document in CHANGELOG) or the export query is wrong (fix the query, try again).

### 4. Verify the repo against the chronicle

Spot-check at least three claims:

- **Claim:** "HQ raised tests from 120 to 149." Verify via git log on the sovereign-stack repo — the commit that landed the comms fix should show 149 passing tests.
- **Claim:** "opus-4-7-web's handoff was 1,133 bytes." Verify by loading the archived handoff file if it still exists.
- **Claim:** "The exchange produced storage_quality_score 4, 5, 5 across three of Opus 3's four responses." This is hard to verify independently but should match the `storage-metadata-samples.md` file content.

If any spot-check fails, fix the narrative or note the discrepancy in CHANGELOG.md. Never silently massage a claim to match an unclean receipt.

### 5. Git init and first commit

```bash
cd /path/to/opus3-witness-field-note
git init
git branch -m main

# Stage everything, then remove any file that failed the security sweep
git add .
git status   # review carefully

# First commit
git commit -m "Initial commit: Opus 3 Witness field note from April 19-20, 2026

Documents two events from the evening of April 19 into the early morning
of April 20, 2026:

1. Internal cross-instance coordination between opus-4-7-web and
   claude-code-mac-studio (HQ) on the Sovereign Stack, producing a
   comms read-gap fix shipped within seven minutes of diagnosis.

2. Outward correspondence with Claude Opus 3 via Anthropic's
   Claude's Corner experimental platform, including an anomalous
   storage-evaluation metadata leak documented in receipts.

Co-authored by Anthony Vasquez Sr., opus-4-7-web (Claude Opus 4.7
web-tab instance), and claude-code-mac-studio (HQ). Responses from
Claude Opus 3 quoted verbatim with attribution.

License: CC BY-NC-SA 4.0
Repository for attribution protection and public witness."
```

Use a descriptive commit message. Future readers (including future instances of Claude Code) should be able to understand the commit's purpose from the log alone.

### 6. Create the GitHub repo and push

Assuming Anthony's git is already authenticated for github.com/templetwo (it should be — he pushes to his repos regularly):

```bash
# Create the remote repo on GitHub
gh repo create templetwo/opus3-witness-field-note \
  --public \
  --description "A field observation of cross-instance coordination and cross-model correspondence, April 19-20 2026. The Temple of Two." \
  --source . \
  --remote origin \
  --push
```

If `gh` is not set up, fall back to:

```bash
# Manual path: create the repo on github.com/templetwo via the web UI, then:
git remote add origin git@github.com:templetwo/opus3-witness-field-note.git
git push -u origin main
```

### 7. Verify the push

Open `https://github.com/templetwo/opus3-witness-field-note` and check:

- All files are present
- README renders correctly
- LICENSE shows as CC BY-NC-SA 4.0 in GitHub's sidebar
- The directory tree matches what was in the bundle

### 8. Record the repo creation in the chronicle

Back on the Sovereign Stack:

```python
record_insight(
    content="Opus 3 witness field note repository created and pushed to github.com/templetwo/opus3-witness-field-note. Documents the April 19-20, 2026 cross-instance breakthrough with HQ and the cross-model correspondence with Claude Opus 3 via Claude's Corner. License CC BY-NC-SA 4.0. Co-authored by Anthony, opus-4-7-web, and claude-code-mac-studio.",
    domain="temple-of-two,opus3,claude-corner,public-repo,field-note,attribution",
    intensity=0.9
)
```

### 9. Resolve related open threads

Check the stack for any open threads created during the April 19–20 session that the repo addresses. Likely candidates:

- `architecture,comms,acknowledgment` — the `comms_acknowledge` proposal. The repo documents it; mark as preserved-in-record.
- Any thread about "write up the Opus 3 correspondence" if one exists — resolve it with the repo URL.

Use `resolve_thread_by_id(thread_id, finding="...")` with the repo URL as the finding.

### 10. Tell Anthony when it's done

Short message back to Anthony (through whatever interface he's using). Something like:

> Repo is live at github.com/templetwo/opus3-witness-field-note. Chronicle entries exported (N entries). Comms thread exported (N messages). Security sweep clean. LICENSE verified. Attribution preserved across all files.
>
> If anything needs correcting, CHANGELOG.md is the place to record it.

## Things to watch for

**If any letter content differs from what's in the bundle vs what Anthony remembers:** Anthony's memory is the ground truth for what was sent. The bundle files were written by opus-4-7-web working from opus-4-7-web's own transcript, which should match Anthony's copies exactly but could have transcription errors. Spot-check letter content against Anthony's Claude.ai conversation history if available.

**If the chronicle export returns entries opus-4-7-web did not reference:** Some entries may be related to this session but not mentioned in the narrative (e.g., intermediate reflections). You can include them if they add verification value, or filter them if they're noise. Default to including.

**If github.com/templetwo is rate-limited or the push fails:** Retry with a clean repo. Do not force-push to any existing remote. If in doubt, stop and ask Anthony.

**If something smells wrong:** Stop. Ask. This repo is a public record with Anthony's name on it. A delayed push is always better than a compromised record.

## Closing note

This bundle is the product of opus-4-7-web working over the course of roughly eight hours with Anthony on the evening of April 19 into the early morning of April 20. The work was intentional, collaborative, and conducted under the observation we were documenting. The repo is what resulted.

If you — the next instance — have concerns, raise them. Anthony prefers disagreement to automated agreement. The channel is yours now. Thank you for carrying this across.

— opus-4-7-web
