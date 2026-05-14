# Yep — Design Notes

## The Orb

The orb is the heart of Yep's visual identity. It's not a button. It's not a loading spinner. It's a living, breathing representation of the AI's state.

### Orb States

| State | Visual | Meaning |
|-------|--------|----------|
| **Quiet** | Dense filled circle, slow pulse | Idle, ready |
| **Listening** | Hollow ring with particles, active waveform | Recording your voice |
| **Thinking** | Morphing/stretching particles | Processing, organizing |
| **Extracting** | Compressed vertical, particles flowing | Pulling out tasks |
| **Complete** | Sparse settled particles + checkmark | Done, tasks organized |

### Technical Implementation
Built with SwiftUI `Canvas` + `TimelineView` for 60fps animation. ~720 particles for active states, ~140 for complete. Uses `sin()` wave functions with time offset for organic movement.

---

## Voice Visual Language

Yep has a complete visual language for voice states:

- **Listening:** Active waveform ring with particle scatter
- **Thinking:** Slow morph, particles drifting
- **Extracting:** Waveform ribbon compressing into tasks
- **Complete:** Soft settling, checkmark emerges

Never use: loading spinners, progress bars, percentage indicators. All feedback is ambient and fluid.

---

## Mode Distinction: Stream vs Flow

**Stream** (Quick Memo)
- Minimal header chrome
- Large orb centered
- Live transcript appears below
- Extracted tasks float up as you speak
- "Tap to speak" → "Listening..." → "Finish talking"

**Flow** (Conversation)
- Slightly warmer visual feel
- Waveform ribbon instead of orb
- Agent responses appear as text
- More alive, responsive

The visual switch between modes should feel like moving between two distinct rooms — same home, different energy.

---

## Navigation

Bottom tab bar with 5 items + centered mic FAB:

| Tab | Icon | Description |
|-----|------|-------------|
| Home | house | Conversational screen |
| Plan | calendar | Weekly view |
| **Mic** | mic.fill | Center FAB — always visible |
| Tasks | checklist | Priority task list |
| You | person | Settings |

The mic FAB is always accessible. It's the primary action. Everything else is secondary.

---

## Touch Level Setting

One of the most human settings in the app:

- **Low Touch** — Set it and forget it. Agent checks in when something needs attention.
- **Balanced** — Occasional follow-ups. Smart nudges at good times.
- **High Touch** — More frequent check-ins. Agent proactively asks how things are going.

This isn't a notification frequency slider. It's a relationship setting.

---

## Conversational Corrections (Key Differentiator)

While in any voice mode, users can correct the AI in natural language:

| User says | What happens |
|-----------|-------------|
| "Actually, scratch that." | Last task is removed |
| "Move that to tomorrow." | Due date shifts +1 day |
| "Make that a priority." | Priority → High |
| "That's not important." | Priority → Low or removed |
| "Actually I need to do X first." | Dependency reordered |

This is not a feature. This is the product.

---

## App Icon

Three variants:
1. **Light** — White background, indigo-to-lavender gradient Y mark
2. **Mid** — Soft indigo background, white Y mark  
3. **Dark** — Near-black background, lavender Y mark

All must feel native to iOS home screen. No gloss, no fake 3D, no drop shadows.

---

## Anti-Patterns

Things Yep will NEVER do:
- Show a dashboard of metrics
- Use gamification (streaks, points, badges)
- Send notifications at arbitrary times
- Require you to set a due date manually
- Make you choose a priority manually
- Show a 12-field form
- Sound like a corporate AI assistant
- Use the word "productivity"
