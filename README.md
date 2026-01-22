# Status - Friend Availability Widget App

A production-ready iOS app for sharing real-time availability status with friends via home screen widgets.

## 📱 What is Status?

Status lets you share your current availability with friends in real-time. See who's free, busy, or gaming without constant messaging. Perfect for students, teams, and friend groups who want to coordinate hangouts effortlessly.

### Key Features
- 15 status options (Free, Busy, In Class, Gaming, and more)
- Real-time music activity sharing
- Custom status messages (up to 15 characters)
- Home screen widgets for quick status checks
- Privacy-focused (status only visible to accepted friends)
- Beautiful, intuitive interface

## Project Structure

```
Status/
├── Status/                    # Main app target
│   ├── Views/
│   │   ├── Onboarding/       # 5-screen onboarding flow
│   │   └── Main/             # Main app screens
│   ├── ViewModels/           # MVVM ViewModels with Combine
│   └── Resources/            # Assets, colors, etc.
├── StatusWidget/             # Widget extension target
│   └── Views/                # Widget views (Small, Medium, Large)
└── Shared/                   # Shared between app and widget
    ├── Models/               # Data models
    ├── Services/             # CloudKit, data persistence
    └── Utilities/            # Helpers, extensions

```

## Setup Instructions

### 1. Create Xcode Project

1. Open Xcode 15+
2. Create new project: iOS App
3. Name: `Status`
4. Interface: SwiftUI
5. Language: Swift
6. Minimum Deployment: iOS 17.0

### 2. Add Widget Extension

1. File → New → Target
2. Select "Widget Extension"
3. Name: `StatusWidget`
4. Include Configuration Intent: **NO** (we'll use static widgets)
5. Activate scheme when prompted

### 3. Configure App Groups

1. Select Status target → Signing & Capabilities
2. Click "+ Capability" → App Groups
3. Add: `group.com.yourcompany.status`
4. Repeat for StatusWidget target with same group ID

### 4. Configure CloudKit

1. Select Status target → Signing & Capabilities
2. Click "+ Capability" → iCloud
3. Check: CloudKit
4. Add container: `iCloud.com.yourcompany.Status`
5. Repeat for StatusWidget target

### 5. Configure Background Modes

1. Select Status target → Signing & Capabilities
2. Click "+ Capability" → Background Modes
3. Check:
   - Remote notifications
   - Background fetch

### 6. Add Files to Targets

**Shared Files** (add to BOTH Status and StatusWidget targets):
- All files in `Shared/` folder

**Status Files** (add to Status target only):
- All files in `Status/` folder

**StatusWidget Files** (add to StatusWidget target only):
- All files in `StatusWidget/` folder

### 7. Update Info.plist

Add to Status target Info.plist:
```xml
<key>NSUserTrackingUsageDescription</key>
<string>We don't track you, but iOS requires this for CloudKit.</string>
<key>NSContactsUsageDescription</key>
<string>To help you find friends by phone number.</string>
```

### 8. CloudKit Dashboard Setup

1. Go to CloudKit Dashboard (developer.apple.com/icloud/dashboard)
2. Select your container
3. Select "Schema" → "Development"
4. Create Record Types (see CLOUDKIT_SCHEMA.md)
5. Deploy to Production when ready

## Key Features

- 3 status states: Free, Busy, Do Not Disturb
- Auto-expire after 30min, 1hr, or 2hr
- Friend management with requests
- Home screen widgets (Small, Medium, Large)
- Real-time updates via CloudKit subscriptions
- Privacy-focused with blocking support

## Technical Stack

- **Platform**: iOS 17+
- **Language**: Swift 5.9+
- **UI**: SwiftUI only
- **Architecture**: MVVM with Combine
- **Backend**: CloudKit (Public + Private databases)
- **Data Sharing**: App Groups
- **Widgets**: WidgetKit

## Build Requirements

- Xcode 15.0+
- macOS 13.0+
- iOS 17.0+ device or simulator
- Apple Developer account (for CloudKit)

## Running the App

1. Select Status scheme
2. Choose target device
3. Build and run (Cmd+R)

## Running the Widget

1. Run the app first
2. Long press home screen
3. Tap "+" in top corner
4. Search for "Status"
5. Select widget size
6. Add to home screen

## Testing

- Unit tests: Status target
- Widget preview: Use Xcode Canvas in widget files
- CloudKit: Test in Development environment first

## Architecture Notes

### Data Flow

1. App updates status → CloudKit Public Database
2. CloudKit triggers subscription → Push notification
3. Widget timeline refreshes → Fetches from shared UserDefaults
4. Background task syncs CloudKit → Local cache every 15min

### Performance

- Widget uses denormalized `FriendStatusView` for fast rendering
- Shared UserDefaults cache for instant widget loads
- CloudKit queries limited to 50 friends max
- Automatic status expiration reduces stale data

## Next Steps

1. Follow setup instructions above
2. Copy all Swift files into Xcode project
3. Configure CloudKit schema
4. Test on device (widgets don't work well in simulator)
5. Submit for TestFlight/App Store review

## 📄 Legal Documents

Legal documents are hosted via GitHub Pages in the `/docs` folder:
- [Privacy Policy](docs/privacy.html)
- [Terms of Service](docs/terms.html)
- [Support Page](docs/support.html)

See [GITHUB_PAGES_SETUP.md](GITHUB_PAGES_SETUP.md) for hosting instructions.

## 🚀 Deployment

Ready to deploy? Follow the comprehensive guide in [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md) which covers:
- Code signing and certificates
- CloudKit production schema setup
- App Store Connect configuration
- TestFlight distribution
- App Store submission

## License

Proprietary - All rights reserved
