# Ink Island — Capacitor iOS Setup

## What's in this folder
```
inkisland-capacitor/
├── www/
│   └── index.html        ← Your complete game (ready to go)
├── capacitor.config.json ← Capacitor settings
├── package.json          ← Node dependencies
└── README.md             ← This file
```

---

## Step-by-step: Mac + Xcode required

### 1. Install Prerequisites (once only)
```bash
# Install Node.js if you don't have it
# Download from https://nodejs.org (LTS version)

# Install Xcode from the Mac App Store (free, ~7GB)
# Then install Xcode command line tools:
xcode-select --install
```

### 2. Set up the project
```bash
# Navigate into this folder
cd inkisland-capacitor

# Install dependencies
npm install

# Add iOS platform (creates the Xcode project)
npx cap add ios
```

### 3. Open in Xcode
```bash
npx cap open ios
```

### 4. In Xcode — before building:

**Change Bundle ID** (must be unique):
- Click the project name (top of left panel) → "Ink Island" target
- Under "Signing & Capabilities" → change `com.yourname.inkisland`
  to something like `com.amy.inkisland` (must be unique in App Store)

**Set your Team**:
- Same screen → "Team" → select your Apple Developer account
  (needs $99/year Apple Developer Program membership)

**Set version**:
- "General" tab → Version: `1.0` | Build: `1`

### 5. Add App Icon
You need a 1024×1024 PNG (no rounded corners, no transparency — Apple adds those).

In Xcode:
- Open `App/Assets.xcassets` → `AppIcon`
- Drag your 1024×1024 PNG into the slot

**Quick icon idea**: screenshot the title screen on your phone, 
crop to square, use https://www.appicon.co to generate all sizes.

### 6. Add Launch Screen (optional but recommended)
- In Xcode → `App/LaunchScreen.storyboard`
- Change background color to black (`#000000`) to match game

### 7. Test on your iPhone
- Plug in your iPhone via USB
- Select your device from the device picker (top of Xcode)
- Press ▶ Run
- Trust the developer certificate on your phone:
  Settings → General → VPN & Device Management → trust your Apple ID

### 8. Archive & Submit
When ready to submit to App Store:

```
Xcode menu → Product → Archive
```

Once archived:
- Click "Distribute App" → "App Store Connect" → follow prompts
- Go to https://appstoreconnect.apple.com
- Create a new app entry with:
  - Name: Ink Island
  - Bundle ID: (what you set above)
  - SKU: inkisland-1
- Fill in description, screenshots, age rating (4+)
- Submit for review (takes 1–3 days)

---

## App Store Listing Copy (ready to paste)

**Name:** Ink Island

**Subtitle:** Paint · Claim · Conquer

**Description:**
Paint your way across 7 unique worlds in this addictive territory game!

Loop around land to claim it as yours. Outsmart robot opponents across 7 handcrafted levels — from peaceful meadows to blazing lava worlds, outer space, candy land, and a neon cyber city.

FEATURES
• 7 unique themed worlds — Meadow, Shopping Mall, Space, Lava, Ice, Candy & Cyber City
• Smooth 360° drag-to-steer controls
• Dramatic robot elimination effects
• Progressive difficulty — go from training to survival mode
• Beautiful procedurally generated islands every game

**Keywords:** territory, paint, puzzle, casual, arcade, robot, island, drawing

**Age Rating:** 4+ (no objectionable content)

**Category:** Games → Casual

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| "No signing certificate" | Sign in to Xcode with your Apple ID → Preferences → Accounts |
| App crashes on launch | Check that `www/index.html` exists and opens in Safari first |
| Touch doesn't work | In `capacitor.config.json` make sure `scrollEnabled: false` is set |
| Black screen | Open Safari → Develop → your iPhone → inspect the WebView for JS errors |

---

## Debug on device (Safari Web Inspector)
1. iPhone: Settings → Safari → Advanced → Web Inspector → ON
2. Mac Safari: Develop menu → your iPhone name → Ink Island
3. Full browser console + element inspector works on the live game!
