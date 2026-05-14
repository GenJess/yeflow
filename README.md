# Yep — Talk through your life.

> *"I talked naturally and my life organized itself."*

![Yep Design System](docs/design-system.png)

Yep is a **conversational AI life organizer** — not a task manager, not a chatbot. It's an ambient layer that turns the way you already think and talk into a clean, prioritized plan. Zero typing. Zero friction.

---

## The Problem

Everyone wants to be organized. Nobody wants to maintain a to-do list.

Writing things down is friction. Checking things off is friction. Setting priorities, due dates, reminders — all friction. The irony: **maintaining a to-do list is itself one of the most burdensome tasks in your week.**

Current "voice" solutions just remove the typing part. That's not enough. The real cognitive load is:
- Figuring out *what* the task actually is ("I need to clean my car before the road trip" → task: **Clean car**)
- Identifying dependencies (clean car *before* packing, not after)
- Knowing when to do what
- Remembering to check things off
- Smart, non-intrusive reminders

Yep solves all of it.

---

## How It Works

### Two Modes

**Stream** — Brain dump mode. Just talk. Live transcription shows draft tasks as you speak. Hit finish, Yep extracts and scopes everything into a clean task list with priorities, dates, and dependencies.

**Flow** — Conversation mode. An agent facilitates — like a scrum master asking the right questions. "What's on your plate this week? Any blockers? What needs to happen first?" It prods gracefully, never intrusively.

### The Weekly Check-in
Sunday push notification: *"Hey, five minutes — what's your week look like?"*
You talk. Yep structures. Done.

### Smart Follow-ups
No more setting reminders at arbitrary times. Yep checks back in at the most logical moment — *after* you've had time to complete something, not when you're at the dentist. Powered by ML that learns your patterns over time.

### Live Conversational Corrections
While talking, just say:
- *"Actually, scratch that."* → Task removed
- *"Move that to tomorrow."* → Date updated
- *"Make that a priority."* → Priority updated

No manual editing. No tapping around. Just talk.

---

## Core Insight

The scrum master analogy: stand-up every morning — *what did you do yesterday, what are you doing today, any blockers?* — is the most natural task management format humans have. Yep is that, on your terms, at your cadence, with AI doing the organizing.

The dependency problem is huge. Most people know "I need to study before the test" but they never write it down as a *dependency*. They just add both items to a list. Yep infers the dependency from natural speech and slots tasks into the right order automatically.

---

## Design Philosophy

Yep should feel like: **a calm intelligent companion.**

Never: a task manager, a chatbot, an AI gimmick, a productivity grinder.

- **Soft confidence.** Minimal words. Human. Clear. Never verbose.
- **Interface should feel almost invisible.** The focus is mental clarity.
- **Speech first.** Typing is fallback.
- **Organization should emerge naturally.** Users talk. Yep structures.

Design references: Apple Reminders × Reflect × Arc × Headspace × Superhuman × Linear

Core emotion: **"Your brain exhaling."**

---

## Brand System

### Color Palette
| Role | Name | Hex |
|------|------|-----|
| Primary BG | Warm Off-White | `#F7F6F3` |
| Surface | Soft Gray | `#ECEAE6` |
| Text Primary | Near-Black | `#111111` |
| Text Secondary | Muted Graphite | `#6E6A64` |
| Accent Primary | Soft Indigo | `#6E6BFF` |
| Accent Secondary | Dusty Lavender | `#B6B3FF` |
| Success | Muted Sage | `#B8D8C0` |
| Warning | Soft Amber | `#E7C98B` |
| Error | Muted Clay | `#D89A8C` |

### Typography
- **Display:** SF Pro Display — clean, spacious, elegant
- **Body:** SF Pro Text — high readability
- Medium weights preferred. High line-height. Large breathing room.

### The Orb
The visual heart of Yep. A particle orb that breathes with you:
- **Quiet** — slow gentle pulse
- **Listening** — active waveform ring
- **Thinking** — slow morphing movement
- **Complete** — soft settling with checkmark

---

## MVP Screens

1. Welcome / Onboarding
2. Home — Conversational screen with orb
3. Recording state — Live transcription + extraction
4. Plan — Organized weekly calendar view
5. Tasks — Priority list view
6. Task detail sheet
7. Settings / Preferences (touch level: Low / Balanced / High)

---

## Tech Stack

- **Platform:** iOS-first (React Native / Expo or SwiftUI)
- **Auth:** Supabase (OAuth / magic link)
- **Database:** Supabase Postgres
- **Voice:** OpenAI Realtime API / Deepgram for transcription
- **AI Organizer:** Gemini / OpenAI GPT-4o
- **Deployment:** Vercel (web preview) / Replit (prototyping)

---

## Repo Structure

```
yeflow/
├── docs/                    # Design assets, screenshots
│   ├── design-system.png    # Full Yep design system overview
│   ├── orb-states.png       # Orb visual states
│   └── logo.png             # Logo variants
├── brand/
│   ├── BRAND_SYSTEM.md      # Full brand + design system doc
│   └── VOICE_MEMOS.md       # Original product vision voice memos (transcribed)
├── swift/
│   └── Yep_SwiftHandoff.md  # Full SwiftUI implementation handoff
└── README.md
```

---

## Product Vision (Voice Memo — Transcribed)

> *"No one wants to type. That's why people don't maintain to-do lists. Just write it down or type it — that right there sucks. It's friction. Writing your to-do list and crossing off are like two extra steps... The most seamless experience for task management — it takes away all the friction. Everyone wants to be organized. It's very hard. It's almost a complete job to just maintain a good, well-managed task list. One little small voice dump or conversation, and then throughout the week, we'll check in."*

See [`brand/VOICE_MEMOS.md`](brand/VOICE_MEMOS.md) for the full unedited product vision.

---

## Status

🚧 **In development** — iOS MVP build in progress.

---

*Yep. Talk through your life.*
