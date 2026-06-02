# foodie-co 
# Foodie & Co. · AM Workspace

A single-file, interactive product prototype that contrasts a conventional B2B account-management tool with an AI-agent-powered reimagining of the same workflows. It's framed as the internal "AM Workspace" of **Foodie & Co.**, a fictional Italian specialty-food distributor, and is built to be opened, clicked through, and demoed — no build step, no backend.

The whole experience is a guided **before / after** argument: every screen has a *Current* state (the inert, A–Z, activity-tracking tool) and a *Proposed* state (the same job, reorganized around relationship context, an agent that drafts and learns, and outcome-first reporting). Flip the toggle and the same data tells a different story.

## What it demonstrates

The prototype is organized around two personas and a Current ↔ Proposed toggle.

**Account Manager (Nicholas Rath)** sees the day-to-day workflow screens:

- **Home** — In *Current*, a flat A–Z book of 48 accounts. In *Proposed*, an attention-ranked cockpit that triages the day: buyers waiting on a reply, accounts worth reaching out to, and the quiet healthy ones tucked away, with any active campaign surfaced inline.
- **Inbound Requests** — Reactive replies. *Current* jumps straight to a technically-correct but relationally flat draft. *Proposed* opens with relationship context first (order patterns, preferences, past rejections, open threads), then drafts, including harder cases like a reorder paired with a repeat-complaint.
- **Outbound Campaigns** — A bulk pre-order campaign (Alba white truffle) across the book. *Proposed* adds guardrails that flag buyers contacted too recently so you can skip the send instead of over-emailing.
- **Proactive Outreach** *(Proposed only)* — A "new workflow" that surfaces accounts cooling off, going overdue, or hitting a moment worth a touch (an anniversary, a requested item arriving), each with its trigger, relationship health, and a ready draft.

**VP of Customer Operations** sees the leadership view:

- **PulseBoard** — *Current* shows blended activity metrics. *Proposed* leads with the outcome that matters, explains the trend in a line, and splits effort and accuracy by inbound vs. outbound workflow.

### Cross-cutting mechanics

- **Agent memory (learning loop)** — In *Proposed*, the agent captures every edit and phrasing change you make, reinforces repeated ones into higher-confidence memories, and surfaces them in a memory panel you can inspect, pause, or forget from. A toast with Undo fires on each capture.
- **Onboarding tour** — Two persona-scoped guided tours (AM and VP) that auto-launch on first entry to *Proposed* and are replayable from the header.
- **Editable drafts, product substitutions, regenerate** — Inline editing of draft fields and stock details, recommended substitutions that respect prior rejections, and a regenerate cycle that deliberately shows what tone the tool can and can't fix on its own.

## Tech stack

- **React 18** via UMD CDN — no bundler
- **Babel Standalone** — JSX compiled in the browser
- **Tailwind CSS** via Play CDN, with a custom warm-paper editorial theme configured inline
- **Google Fonts** — Fraunces (display serif), Hanken Grotesk (sans), Spline Sans Mono (data/mono)
- A single self-contained `index.html` — all data, components, and styles live in one file

No external API calls, no network dependencies beyond the CDNs, and all state is in-memory (nothing persists between reloads).

## Running it

Because everything is in one file with CDN dependencies, you have a few options:

```bash
# Simplest: open the file directly
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows

# Or serve it locally (recommended, avoids any file:// quirks)
python3 -m http.server 8000
# then visit http://localhost:8000
```

You'll need an internet connection on first load so the CDN scripts and fonts can fetch.

## How to explore

1. Start on **Home** in the *Current* state to see the baseline tool.
2. Flip the **Current → Proposed** toggle in the header. The AM onboarding tour launches automatically the first time.
3. Walk the workflow tabs: Home → Inbound Requests → Outbound Campaigns → Proactive Outreach. Edit a draft and watch the **memory** panel pick up the change.
4. Switch the persona to **VP of Customer Operations** to see the PulseBoard, then toggle Current ↔ Proposed there too.
5. Hit the **?** in the header anytime to replay the tour for whichever persona you're in.

## Notes

- The data — accounts, buyers, campaigns, briefs, and metrics — is fictional and crafted to make the before/after contrast legible, not to be statistically realistic.
- Accessibility was a design goal: keyboard focus rings on all interactive controls, WCAG-AA-tuned text colors, 44px touch targets on coarse pointers, and reduced-motion fallbacks for the animations.
- Layout is responsive, with an off-canvas nav drawer below the `lg` breakpoint.

## License

Add your license of choice here (e.g. MIT).
