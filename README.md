# My Daily Memory

A minimalist iOS journaling app to capture your daily thoughts, moments, and memories.

## Features

- 📝 **Daily Entries**: Write and organize your daily journal entries
- 📅 **Calendar View**: Browse entries by date
- 🏷️ **Tags & Categories**: Organize memories with custom tags
- 🔒 **Privacy First**: All data stored locally on device with optional iCloud sync
- 🎨 **Rich Text**: Support for formatting, photos, and emojis
- 🔍 **Search**: Find past memories quickly
- 🌙 **Dark Mode**: Beautiful interface for day and night

## Tech Stack

- **iOS App**: SwiftUI + SwiftData
- **Minimum iOS**: 17.0
- **Storage**: Local (CoreData/SwiftData) + iCloud sync
- **Web**: Static HTML pages for landing & privacy policy

## Project Structure

```
my-daily-memory/
├── MyDailyMemory/          # iOS App
│   ├── App/                # App entry & configuration
│   ├── Models/             # Data models (Entry, Tag, etc.)
│   ├── Views/              # SwiftUI views
│   ├── ViewModels/         # Business logic
│   └── Utils/              # Helpers & extensions
├── web/                    # Static web pages
│   ├── index.html          # Landing page
│   └── privacy.html        # Privacy policy
├── docs/                   # Documentation
└── README.md
```

## Development

### Requirements
- Xcode 15.0+
- iOS 17.0+ SDK
- Swift 5.9+

### Setup
1. Open `MyDailyMemory.xcodeproj` in Xcode
2. Select your development team in Signing & Capabilities
3. Build and run on simulator or device

## Roadmap

- [x] Project setup
- [ ] Core data models
- [ ] Entry creation & editing
- [ ] Calendar view
- [ ] Tag system
- [ ] Search functionality
- [ ] iCloud sync
- [ ] Export to PDF/Markdown
- [ ] Privacy policy & landing page
- [ ] App Store submission

## Privacy

My Daily Memory is designed with privacy as a core principle:
- All journal entries are stored locally on your device
- No analytics or tracking
- Optional iCloud sync uses end-to-end encryption
- No third-party services or ads

See [Privacy Policy](web/privacy.html) for details.

## License

Copyright © 2026 Eric Lin. All rights reserved.
