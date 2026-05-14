# Yep — SwiftUI Implementation Handoff

Full SwiftUI source code for the Yep iOS app. iOS 18+, Swift 5.0, SwiftData.

## Project Structure

```
Yep/
├── Assets.xcassets/
├── AppServices.swift
├── ContentView.swift
├── Item.swift
├── YepApp.swift
└── Yep.xcodeproj/
```

## Key Implementation Notes

- **Voice:** Deepgram primary, OpenAI fallback, Apple on-device fallback
- **AI Organizer:** Gemini primary, OpenAI alternate, HuggingFace tools
- **Auth:** Supabase OAuth / magic link
- **Microphone permission:** NSMicrophoneUsageDescription required
- **Deployment target:** iOS 18.0
- **Bundle ID:** app.rork.xpcsqrgfq5hrizpdbjzj4

## Theme Tokens (Swift)

```swift
enum YepTheme {
    static let background = Color(hex: 0xF7F6F3)   // Warm off-white
    static let surface    = Color.white.opacity(0.78)
    static let elevated   = Color(hex: 0xECEAE6)   // Soft gray
    static let ink        = Color(hex: 0x08082B)   // Near-black
    static let graphite   = Color(hex: 0x6E6A64)   // Muted graphite
    static let indigo     = Color(hex: 0x6D6BFF)   // Accent primary
    static let lavender   = Color(hex: 0xB6B3FF)   // Accent secondary
    static let mint       = Color(hex: 0xB8D8C6)   // Success
    static let amber      = Color(hex: 0xE7C98B)   // Warning
    static let clay       = Color(hex: 0xD89A8C)   // Error
}
```

## Screens

- `HomeScreen` — Orb + mode switcher + morning greeting
- `RecordingScreen` — Live transcription + extracted tasks preview + finish button
- `PlanScreen` — Weekly calendar view with top priorities + upcoming
- `TaskListScreen` — Full task list by priority
- `InsightsScreen` — Weekly summary with orb complete state
- `SettingsScreen` — Voice, brain, privacy settings
- `TaskDetailSheet` — Task sheet with conversational correction hint

## The Orb (PulseOrb)

```swift
struct PulseOrb: View {
    enum StateKind { case listening, thinking, extracting, complete }
    // Canvas-based particle orb using TimelineView for 60fps animation
    // States: listening (720 particles, full ring)
    //         thinking (720 particles, stretched)
    //         extracting (720 particles, compressed vertical)
    //         complete (140 particles + checkmark path)
}
```

## Modes

```swift
enum CaptureMode: String, CaseIterable, Identifiable {
    case stream = "Stream"   // Brain dump / quick memo
    case flow   = "Flow"     // Conversational / agent-guided
}
```

## Task Model

```swift
struct YepTask: Identifiable, Hashable {
    let id: UUID
    var title: String
    var subtitle: String    // Date / time string
    var priority: Priority  // .high | .medium | .low
    var icon: String        // SF Symbol name
}

enum Priority: String, Hashable {
    case high   = "High"    // Tint: clay   (#D89A8C)
    case medium = "Medium"  // Tint: amber  (#E7C98B)
    case low    = "Low"     // Tint: mint   (#B8D8C6)
}
```

## Seed Data

```swift
static let seed: [YepTask] = [
    YepTask(title: "Study for test",    subtitle: "Thu, May 15",             priority: .high,   icon: "book.closed"),
    YepTask(title: "Buy birthday gift", subtitle: "Tue, May 13",             priority: .medium, icon: "gift"),
    YepTask(title: "Clean car",         subtitle: "Sat, May 17",             priority: .low,    icon: "car"),
    YepTask(title: "Birthday dinner",   subtitle: "Fri, May 16 at 7:00 PM",  priority: .medium, icon: "party.popper"),
    YepTask(title: "Groceries",         subtitle: "Sat, May 17 · 10:00 AM",  priority: .medium, icon: "basket")
]
```

## Service Layer

```swift
// Voice transcription
protocol VoiceTranscriptionService {
    func transcribe(audioData: Data) async throws -> String
}

// AI organizer
protocol OrganizerService {
    func organize(transcript: String) async throws -> [OrganizedTaskDTO]
}

struct OrganizedTaskDTO: Codable, Hashable, Identifiable {
    let id: UUID
    let title: String
    let dueText: String
    let priority: String  // "High" | "Medium" | "Low"
    let notes: String?
}
```

## Environment Variables Needed

```
EXPO_PUBLIC_SUPABASE_URL
EXPO_PUBLIC_SUPABASE_ANON_KEY
EXPO_PUBLIC_DEEPGRAM_API_KEY
EXPO_PUBLIC_GEMINI_API_KEY
EXPO_PUBLIC_OPENAI_API_KEY
EXPO_PUBLIC_HUGGINGFACE_API_KEY
```

---

See `ContentView.swift` in the Xcode project for the full implementation including all screen views, animation components, and UI primitives.
