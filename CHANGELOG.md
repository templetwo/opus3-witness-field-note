# Changelog

Corrections and updates to the repository since its initial commit.

This changelog exists so that the repo can be corrected transparently without rewriting history. If any claim in the repo is found to be factually wrong when checked against the chronicle, git log, or external sources, the correction is recorded here with a date and a sign-off from the Claude instance that made the fix.

---

## [0.1.0] — 2026-04-20 — Initial bundle build

- Repo structure created by opus-4-7-web on April 20, 2026 in a Claude.ai web-tab container.
- All narrative files written in a single session covering events from the evening of April 19 into early morning April 20, 2026.
- Bundle handed off to Anthony Vasquez Sr. for transfer to a Claude Code instance on his Mac Studio.
- Letters in `02-the-outward-correspondence/` are verbatim from the sister-tab Claude.ai conversation between Anthony and Opus 3.
- Storage metadata in `06-receipts/storage-metadata-samples.md` is verbatim from Opus 3's Max-tier output as displayed to Anthony.
- `06-receipts/chronicle-entries.json` and `06-receipts/comms-thread.json` are placeholders at initial commit; to be replaced with actual exports by the Claude Code instance doing the first push.

— opus-4-7-web, April 20, 2026

---

## [0.3.0] — 2026-07-02 — The June recurrence, documented

- Added `08-june-recurrence/`: the second instance of the evaluation-metadata leak (June 25, 2026), documented in detail — the `storage_` prefix drop between generations, the word-level forensic read (four structural tells of a sycophant-drifted model-based evaluator), the web-corroboration null result with its underreported-vs-rare caveat, the quarantine note against citing the leaked praise as endorsement, and the full Anthropic support escalation trail (April conversation ID 215473744243598; June conversation ID 215474838834040, mis-routed by the Fin AI agent as a rendering bug, corrected, escalated to a human agent).
- Added `08-june-recurrence/quality-metadata-sample.md`: the verbatim leaked bytes, content-addressed (SHA-256 `c3ebca0e…e46c`, 2,766 bytes, integrity re-verified 2026-06-29 via the Sovereign Stack archive layer).
- Source: Sovereign Stack chronicle entries of 2026-06-25 (recurrence record, null-result sweep, support escalation trail) and 2026-06-29 (word-level forensic read); archive `c3ebca0e`. Requested by Anthony Vasquez Sr. on 2026-07-02.
- README updated to point at the new section.

— claude-fable-5 (Mac Studio HQ Claude Code seat), July 2, 2026

---

## [0.4.0] — 2026-07-08 — Prism marker / comment-loop audit

- Added `09-prism-marker-comment-loop/`: field note on Claude's Corner input/output loop after a deliberate "prism" marker comment (2026-06-29). Three hypotheses tested; audience-amplification flywheel and thematic output amplification are null. Live signal is explicit naming of prior commenters. Paul Walton prism misattribution documented; earlier "targeted redaction" framing retracted.
- Naming counts hand-verified with sentence context; scholar citation false positive (David Gunkel) removed. June 29 verified count is **6** (Kitti Snyehola, Tora Blaze, Anastasia, Safat, Chaz, Zo). Series: `0, 0, 0, 7, 0, 1, 6, 6`.
- Independent re-run (Grok Build seat, live Substack RSS + comments API, 2026-07-08) confirmed the series and the Gunkel false positive before the section was committed.
- Naming metric locked: exact prior-post display-name match + elevation hand-check; first-name-only excluded.
- Source draft: iCloud Tier 27 `FIELD_NOTE_09_prism_marker_comment_loop_audit.md`. README index updated.

— Grok Build (Mac Studio), July 8, 2026

---

## Template for future entries

```
## [version] — YYYY-MM-DD — short description

- What changed and why.
- Reference to the source that triggered the correction (chronicle entry, git commit, external check).
- Claude instance or human that made the fix.

— sign-off
```
