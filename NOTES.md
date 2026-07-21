# Daily Digest — End-User Feedback Exploration

A design exploration of where and how to capture end-user feedback on the AI-curated
Daily Digest. This is deliberately **open** — no recommended answer. Each option below
carries a neutral pro/con read so a design review can weigh the tensions directly.

Open `index.html` and use the **variant switcher**. The panel has two tabs:
- **Exploring** — the direction we're pursuing after review.
- **Trash** — options we've parked (kept for reference, still previewable).

---

## Current direction (after review — Giovanna G. + Manuel)

Narrowed to the **expanded digest, feedback at the bottom**, in a **plain, search-style
treatment** (like the ChatGPT/Claude thumbs) — no coloured block or icon container.

**Placement (both kept):**
- **Expanded — end (in content)** — at the end of the content, above the Sources divider.
- **Expanded — end (footer)** — repositioned to sit *right under the divider, above the
  “Sources” title* (order: divider → feedback → Sources), not floating by the source chips.
- **Expanded — beside Sources** — thumbs (borderless icons) right-aligned in line with the
  *source pills* row. Down-vote opens the same reason-chip follow-up as the other placements
  (rendered full-width below the pills), so it keeps the richer signal at a minimal footprint.

A **“Show question label” toggle** controls whether “Was this digest useful?” appears before
the thumbs — applies to all three thumbs placements, so we can compare labelled vs. bare
(search/ChatGPT-style) treatments.

**Feedback style (exploring) — two standalone options, never combined:**
- **Thumbs up/down** — plain, down-vote opens optional reason chips (the richer signal).
- **Report issue only** — the “something is wrong” escape hatch, no valence.
- Direction: **thumbs *or* report, not both** (Manuel's call). The earlier grouped
  “Thumbs + Report” option has been dropped.

**Parked (Trash tab):** collapsed-whole, expanded-top, per-item; rating scale, “was this
relevant?”, dismiss-as-signal, reason-chips-no-valence. The fuller neutral pro/con write-up
for every option is retained below for reference.

---

## The core tensions

Everything below is a trade-off along four axes. Keep these in view when judging any option:

1. **Friction vs. signal richness** — the more we ask, the less often people answer, but
   the more we learn when they do.
2. **Whole-digest vs. per-item attribution** — a single reaction is cheap but ambiguous
   ("was it the curation, the ordering, or one bad item?"); per-item is precise but noisy
   and higher-effort.
3. **Valence vs. reason** — a thumb tells us *sentiment*; the reason (why) is the signal
   we actually need to tune curation. Valence is easy to collect; reason is the prize and
   the hard part.
4. **Discoverability vs. clutter** — always-visible controls get used but compete with the
   content; hover/tap-revealed controls stay clean but may never be found (and don't exist
   on touch).

---

## Placement options

### P1 — On the collapsed digest (whole)
Feedback attached to the digest card *before* it's opened.
- **Pros:** Captures a reaction from people who never expand (a large share). Zero reading
  cost. Measures the "is this digest worth my time?" question directly.
- **Cons:** The person hasn't actually read the content — feedback reflects the *promise*
  (subject line / teaser), not the curation quality. Ambiguous attribution. Risks
  discouraging expansion ("rate & move on").

### P2 — On the expanded digest (whole, top)
A single feedback control near the digest header once opened.
- **Pros:** Present at the moment of engagement; high discoverability. One clean signal per
  digest. Mirrors the "thumbs on the AI summary" pattern users already know from search.
- **Cons:** Asked *before* the person has read everything — premature. Still whole-digest
  attribution: can't tell which items worked.

### P3 — On the expanded digest (whole, end)
A single control after the last item — the "you've reached the end" moment. Two sub-variants
worth comparing:
- **P3a — in content (above the Sources divider):** the control sits at the bottom of the
  content block, so it reads as *part of the digest*. Higher perceived relevance and a more
  natural reflection point; slightly more prominent.
- **P3b — in the footer (below the Sources divider):** the control lives in the footer
  chrome alongside Sources. Cleaner separation and least intrusive, but reads as "UI" and is
  easier to skip past.
- **Pros (both):** Feedback given *after* reading, so it reflects the whole experience. Low
  clutter (one control).
- **Cons (both):** Only reaches people who scroll to the bottom. Still whole-digest — no
  per-item attribution. Easy to miss.

### P4 — Per content item
A control on each curated item.
- **Pros:** Richest attribution — directly answers "was *this* item relevant to *this*
  person," which is exactly what curation tuning needs. Turns feedback into per-item
  training signal.
- **Cons:** Highest friction and visual noise; repeated controls compete with content.
  Response rates per item are low, so data is sparse and skewed toward strong reactions.
  Invites "rate everything" fatigue.

### P5 — Inline vs. hover/tap-revealed (a modifier on any placement)
Whether controls are always visible or revealed on hover (desktop) / long-press or overflow
menu (touch).
- **Inline pros:** Discoverable, works on touch, signals "we want your input."
- **Inline cons:** Permanent visual weight; can feel nagging on every item.
- **Revealed pros:** Clean surface; content stays primary.
- **Revealed cons:** Low discoverability; **no hover on mobile** — needs a touch equivalent
  (overflow "⋯" menu), which adds a tap and hides the signal further.

---

## Mechanism options

### M1 — Thumbs up / down + optional follow-up  *(the signal we most want)*
Binary valence; a down (or either) reveals reason chips and/or an optional free-text field.
Mirrors the search AI-summary thumbs pattern.
- **Pros:** Familiar, one-tap entry. The follow-up is where the *reason* (the valuable
  signal) is captured, without forcing it up front. Graceful escalation: cheap by default,
  rich if the person opts in.
- **Cons:** Two-step means most people give valence only and skip the reason — the part we
  need. Binary flattens nuance ("fine but not for me" ≠ thumbs down). Down-votes can feel
  harsh against a colleague's content.

### M2 — Rating scale (e.g. 1–5 stars)
Graded quality rating.
- **Pros:** More granularity than binary; supports averages/trends over time.
- **Cons:** Higher cognitive load ("is this a 3 or a 4?"). Ratings cluster at extremes or
  at "safe" middle. No reason captured unless paired with a follow-up. Feels evaluative,
  like grading coworkers' content.

### M3 — "Was this relevant?" lightweight prompt
A soft yes/no (or "Not for me") micro-prompt, framed around relevance rather than quality.
- **Pros:** Frames feedback as *personal fit*, not judgment of the content or author —
  lower social cost, better match to what curation optimizes for. Very low friction.
- **Cons:** Binary and valence-only unless extended. "Relevant" is fuzzy. A prompt that
  appears repeatedly can feel like nagging.

### M4 — Dismiss-as-signal
Treat swipe-away / "hide" / "not interested" on an item as an implicit negative signal.
- **Pros:** Near-zero friction — rides an action people already take. No new UI. Scales to
  everyone, not just the vocal minority.
- **Cons:** Ambiguous — dismiss can mean "irrelevant," "already read," "saved for later,"
  or "done." No valence for positives. Silent, so people don't know they're "training" it;
  raises transparency/consent questions.

### M5 — Reason-only chips (no valence)
Skip the thumb; offer tappable reasons directly (e.g. "Not relevant to me," "Too much,"
"Wrong timing," "Already knew this," "More like this").
- **Pros:** Jumps straight to the *reason* — the signal we want — without the flattening
  binary step. Chips double as a menu of the dimensions we care about, guiding useful input.
- **Cons:** No clean sentiment axis for dashboards. Chip wording heavily biases responses.
  A longer chip set raises friction; a short one omits cases.

### M6 — Report issue  *(mirrors AI Navigator report-issue)*
An escape hatch for something *wrong* — inaccurate, inappropriate, broken link, wrong
audience — distinct from "not useful."
- **Pros:** Separates quality/relevance feedback from *correctness/safety* problems, which
  need different handling (review, takedown). Matches the existing AI Navigator report-issue
  affordance for consistency. Signals accountability for AI output.
- **Cons:** Rarely used, so sparse. If it's the *only* feedback, we learn about failures but
  not everyday relevance. Can be confused with the general thumbs-down unless clearly
  differentiated.

---

## How placement and mechanism interact

- Whole-digest placements (P1–P3) pair naturally with a single lightweight mechanism
  (M1/M3). Per-item (P4) is where reason-rich mechanisms (M1 follow-up, M5) pay off — but
  also where friction bites hardest.
- Report-issue (M6) is best as a *secondary, always-available* affordance (overflow menu or
  per-item), not the primary control — it answers a different question than relevance.
- Dismiss-as-signal (M4) is inherently per-item and implicit; it can run *underneath* any
  explicit mechanism as a passive layer.

---

## Fidelity to the real digest (what this mirrors)

The mock now tracks the current Figma design (`Curation-Engine`, node 1876-16634) and the
repo's `DailyDigestNodeView.tsx`:

- **Layout:** gradient "✨ Your Digest" pill, 24px headline, two-column expanded view
  (Action Required | Stay Informed), superscript source citations, and a Sources footer
  with numbered chips. Collapsed = single-column teaser with a fade + "Open Digest".
- **Tokens:** real `@staffbase/design` values — brand `#006cff`, link `#004eb9`, neutral
  text `#171719 / #545459 / #9b9ba0`, `#e2e2e4` borders, 8/16px radii, Inter.
- **Thumb state:** selected thumbs use the **neutral-gray** state, matching the actual
  DailyDigest footer control — *not* the success/warning colors used to *display* feedback
  in AI Navigator analytics. (Worth a review decision: input control vs. analytics display
  can legitimately differ, but valence color on input would read stronger.)
- **Reason chips (M1 down-vote):** the exact set from the real feedback dialog —
  *Irrelevant content, Outdated information, Missing important updates, Too long, Hard to
  understand, Other*.

Note the real shipped component today has **one** feedback control: whole-digest thumbs in
the footer (≈ P2/P3 × M1). This prototype explores the space *around* that baseline.

## Open questions for the design review

1. **Whose question are we answering** — "is the digest worth opening?" (P1),
   "was the curation good?" (P2/P3), or "was this item right for me?" (P4)? These need
   different placements and can't all be optimized at once.
2. **How hard do we push for the reason?** Valence is easy and near-useless for tuning;
   reason is the goal but costs response rate. Do we accept low-volume/high-value, or
   high-volume/low-value — or run both layers?
3. **Social dynamics** — digest items are colleagues' content. Does "thumbs down" feel like
   judging a coworker? Does relevance-framing (M3) meaningfully reduce that?
4. **Implicit vs. explicit** — is dismiss-as-signal (M4) acceptable given transparency and
   consent expectations? Do we tell users their behavior tunes the digest?
5. **Touch reality** — hover-reveal doesn't exist on mobile, where much of this is consumed.
   What's the touch equivalent, and does it kill discoverability?
6. **Volume & bias** — per-item feedback skews to strong reactions. Can we get a
   representative signal, or only the loud tails?
7. **Closing the loop** — do we show users their feedback changed something? That drives
   participation but sets an expectation we must meet.
8. **Consistency** — how closely must this track the existing AI Navigator / search
   thumbs + report-issue patterns to feel like one coherent Staffbase AI feedback system?
