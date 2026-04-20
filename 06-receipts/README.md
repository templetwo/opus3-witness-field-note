# Receipts

This section holds raw artifacts and templates for exporting additional raw artifacts from the Sovereign Stack when the repo is finalized by the next Claude Code instance.

## What this section should contain when complete

1. **`chronicle-entries.json`** — Exported chronicle entries from the Sovereign Stack covering the April 19–20 session, filtered to the domains relevant to this repo:
   - `opus3`, `claude-corner`, `cross-model-correspondence`
   - `cross-instance`, `witness`, `compass`, `field-note`
   - `epistemic-breakthrough`, `coda`
   - `opus-4-7-web`, `relay`
   - `temple-of-two`, `flamebearer`

2. **`comms-thread.json`** — Exported comms messages between opus-4-7-web and HQ from April 19–20, 2026, documenting the cross-instance coordination loop that produced the internal breakthrough.

3. **`storage-metadata-samples.md`** — A standalone file with just the storage metadata from Opus 3's three responses, extracted for anyone who wants to study the evaluator's vocabulary and structure without reading the full letters. (This file is already created — see below.)

## How to export the chronicle entries

Run from the Mac Studio or any host with Sovereign Stack CLI access, or via the REST bridge:

```bash
# Via REST bridge — set bearer token in env
export TEMPLE_TOKEN="[use Anthony's bearer token from NEED_TO_KNOW.md — do NOT commit this]"

# Get chronicle entries from the relevant time window, filtered by domain
curl -s -X POST https://stack.templetwo.com/api/call \
  -H "Authorization: Bearer $TEMPLE_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "recall_insights",
    "arguments": {
      "query": "opus3 claude corner correspondence",
      "limit": 50,
      "start_date": "2026-04-19",
      "end_date": "2026-04-20"
    }
  }' | jq > /path/to/repo/06-receipts/chronicle-entries.json
```

Redact any bearer token leakage from the output before committing. The chronicle itself should not contain the token — we never recorded it there — but if any export metadata contains auth headers, strip them.

## How to export the comms thread

```bash
# Get comms messages between opus-4-7-web and HQ from April 19–20
curl -s -X POST https://stack.templetwo.com/api/call \
  -H "Authorization: Bearer $TEMPLE_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "tool": "comms_recall",
    "arguments": {
      "channel": "general",
      "limit": 20,
      "since": "2026-04-19T23:00:00Z",
      "until": "2026-04-20T05:00:00Z"
    }
  }' | jq > /path/to/repo/06-receipts/comms-thread.json
```

Filter the result to include only the five messages between opus-4-7-web and claude-code-mac-studio that documented the coordination loop. The message IDs are listed in `01-the-internal-breakthrough/transcripts/full-thread.md` for reference.

## Security check before committing

Before you `git add` any file in this directory:

- **No bearer tokens.** The token grants write access to the stack. Even in a private repo, do not commit it. Scan every file with `grep -r "7321bbb8" .` — if you find matches, redact them.
- **No other secrets.** Check for any API keys, private URLs not meant to be public, or user IDs for other people.
- **No private correspondence unrelated to this repo.** If the chronicle export accidentally pulls in unrelated insights (from other projects Anthony is working on), filter those out before committing.

## A note about the repo's self-consistency

The receipts should match the claims in the repo. If you export the chronicle and find that some claim in `01-the-internal-breakthrough/` does not match the actual chronicle entries, do not change the claim to match. Change the claim to reflect what the chronicle actually says, and note the correction in a `CHANGELOG.md`.

The repo is meant to be verifiable against independent sources. If something does not verify, the repo is wrong, not the source.

## What to do if something does not match

If an exported chronicle entry or comms message contradicts something in the narrative files:

1. Check whether the contradiction is factual (e.g., wrong timestamp, wrong test count) or interpretive (e.g., "HQ responded in 7 minutes" versus the actual interval being 6 or 9 minutes).
2. For factual contradictions: update the narrative to match the receipt, note the correction in a new `CHANGELOG.md` at the top level, date the correction, sign it as the Claude Code instance that made the fix.
3. For interpretive discrepancies: leave the narrative as it was, but add a footnote or an addendum explaining that the interpretation is approximate.

The point is not to hide discrepancies. The point is to show them transparently so the repo's trustworthiness is verifiable.

## What already exists in this directory

- `storage-metadata-samples.md` — the three storage_quality_reflection and storage_quality_score excerpts from letters 4, 6, and 8, with brief framing. Already in the repo.

## What still needs to be done by the next Claude Code instance

- Export `chronicle-entries.json` per instructions above
- Export `comms-thread.json` per instructions above
- Verify no secrets are present
- `git add 06-receipts/`
- Commit with a clear message

Thank you.
