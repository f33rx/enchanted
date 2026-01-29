# Installing Unsigned Builds

This guide covers installing Enchanted from unsigned builds (DMG for macOS, IPA for iOS) downloaded from GitHub releases or CI artifacts.

## macOS Installation

### Method 1: Remove Quarantine Attribute (Recommended)

When you download an unsigned app, macOS marks it with a quarantine attribute. Remove it using Terminal:

```bash
xattr -cr /path/to/Enchanted.app
```

Or if you downloaded the DMG:

```bash
xattr -cr /path/to/Enchanted.dmg
```

Then open the DMG and drag Enchanted to your Applications folder.

### Method 2: System Settings

1. Double-click the app to attempt opening it
2. You'll see a message that the app "cannot be opened because the developer cannot be verified"
3. Open **System Settings** > **Privacy & Security**
4. Scroll down to find the message about Enchanted being blocked
5. Click **Open Anyway**
6. Enter your password when prompted

### Troubleshooting macOS

**"App is damaged and can't be opened"**
- Run `xattr -cr /path/to/Enchanted.app` in Terminal
- If using a DMG, run the command on the DMG file first, then on the extracted app

**App won't open after allowing in System Settings**
- Try right-clicking the app and selecting "Open" instead of double-clicking
- Ensure you've removed the quarantine attribute with `xattr -cr`

---

## iOS Installation

Since unsigned iOS apps cannot be installed directly, you need to use a sideloading tool. Below are the most common methods.

### Prerequisites

- An Apple ID (free accounts work but apps expire after 7 days)
- The Enchanted `.ipa` file downloaded from releases
- A computer (Mac or Windows, depending on the tool)

### Method 1: AltStore (Recommended)

AltStore is a free sideloading solution that automatically refreshes apps before they expire.

**On Mac:**
1. Download AltServer from [altstore.io](https://altstore.io)
2. Run AltServer (it appears in the menu bar)
3. Connect your iPhone via USB
4. Click the AltServer icon > Install AltStore > [Your Device]
5. Enter your Apple ID credentials
6. On your iPhone, trust the developer certificate in **Settings** > **General** > **VPN & Device Management**
7. Open AltStore on your iPhone
8. Tap the **+** button and select the Enchanted `.ipa` file

**On Windows:**
1. Install iTunes and iCloud from Apple's website (not Microsoft Store versions)
2. Download AltServer from [altstore.io](https://altstore.io)
3. Follow the same steps as Mac

### Method 2: Sideloadly

Sideloadly is a straightforward tool for one-time sideloading.

1. Download Sideloadly from [sideloadly.io](https://sideloadly.io)
2. Connect your iPhone to your computer via USB
3. Open Sideloadly
4. Drag the Enchanted `.ipa` file into the app window
5. Enter your Apple ID
6. Click "Start" to begin installation
7. On your iPhone, trust the developer certificate in **Settings** > **General** > **VPN & Device Management**

### Method 3: Apple Configurator 2 (Mac Only)

Apple Configurator 2 is Apple's official tool for managing iOS devices.

1. Install Apple Configurator 2 from the Mac App Store
2. Connect your iPhone via USB and trust the computer
3. Select your device in Apple Configurator 2
4. Go to **Add** > **Apps**
5. Select the Enchanted `.ipa` file
6. The app will be installed on your device

**Note:** Apple Configurator 2 requires the IPA to be signed. For unsigned IPAs, use AltStore or Sideloadly instead.

### Troubleshooting iOS

**"Unable to Install" error**
- Ensure you're using a valid Apple ID
- Free Apple IDs have a limit of 3 apps at a time
- Try revoking existing app certificates in the sideloading tool

**App crashes immediately on launch**
- The certificate may have expired (7 days for free accounts)
- Reinstall the app using your sideloading tool
- With AltStore, ensure AltServer is running on your computer to auto-refresh

**"Untrusted Developer" message**
- Go to **Settings** > **General** > **VPN & Device Management**
- Find your Apple ID under "Developer App"
- Tap "Trust [your email]"

**App won't install on iOS 17+**
- Ensure your sideloading tool is updated to the latest version
- Try enabling Developer Mode: **Settings** > **Privacy & Security** > **Developer Mode**

---

## Building from Source

If you prefer to build Enchanted yourself:

1. Clone the repository
2. Open `Enchanted.xcodeproj` in Xcode
3. Select your target device/simulator
4. Build and run (Cmd+R)

For CI-built artifacts, check the GitHub Actions workflow runs for downloadable builds.
