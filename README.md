<p align="center">
  <img src="https://raw.githubusercontent.com/YTLitePlus/Assets/main/Github/Banner.png" alt="YTLitePlus Banner" />
</p>

# YTLitePlus Fork - YouTube 21.x Compatible

> ⚠️ **This is a modified fork** optimized for **YouTube 21.x** compatibility. Some tweaks have been removed due to incompatibility issues.

[![Platform](https://img.shields.io/badge/Platform-iOS%20%7C%20iPadOS%2014.0%2B-black?labelColor=black&style=flat)](https://developer.apple.com/iphone/index.action)
[![YouTube](https://img.shields.io/badge/YouTube-21.x%20Compatible-red?labelColor=black&style=flat)](https://apps.apple.com/app/youtube/id544007664)
[![YTLite](https://img.shields.io/badge/YTLite-5.2b4-blue?labelColor=black&style=flat)](https://github.com/dayanch96/YTLite)

---

## 🚀 What's Different in This Fork?

This fork has been specifically modified to work with **YouTube 21.x** versions, which broke compatibility with several tweaks in the original YTLitePlus.

### ❌ Removed Tweaks (Incompatible with YouTube 21.x)

| Tweak | Reason |
|-------|--------|
| **YTUHD** | Causes crashes on YouTube 21.x |
| **YTHoldForSpeed** | Incompatible with new player (YTLite 5.2b4 has this built-in) |
| **Return YouTube Dislikes** | Causes crashes in Shorts tab |

### ✅ Included Tweaks (Working)

| Tweak | Description |
|-------|-------------|
| **YTLite 5.2b4** | Ad blocking, background playback, 60+ customizations |
| **iSponsorBlock** | Skip sponsor segments automatically |
| **YouPiP** | Picture-in-Picture support |
| **YTABConfig** | Toggle A/B features in settings |
| **YouMute** | Mute/unmute videos from player overlay |
| **DontEatMyContent** | Prevents notch/Dynamic Island from covering content |
| **YouLoop** | Loop videos easily |
| **YouQuality** | Quick video quality selection |
| **YouSpeed** | Extended playback speed options |
| **YouTimeStamp** | Timestamp button on overlay |
| **YTVideoOverlay** | Helper for overlay buttons |
| **YouGroupSettings** | Organized tweak settings |
| **FLEX** | Debug tool (for developers) |

---

## 🔧 Improvements in This Fork

### 1. **Crash Protection**
- Added try-catch wrappers for common crash points
- Null-safety checks for method swizzling
- Safe value retrieval helpers

### 2. **Re-enabled Google Sign-in Fix**
- The previously disabled Google Sign-in fix has been re-enabled
- Added additional safety checks for YouTube 21.x compatibility

### 3. **YTLite 5.2b4 Integration**
- Updated from 5.0.1 to 5.2b4
- Fixes for Shorts playback issues
- Fixed playback stability
- Built-in hold-to-speed feature (replaces YTHoldForSpeed)

### 4. **Improved Build Workflow**
- Separate GitHub Actions workflow for compatible builds
- Proper SDK version handling
- Automatic YTLite version management

---

## 📦 Building

### Using GitHub Actions (Recommended)

1. Fork this repository
2. Go to **Actions** → **Build YTLitePlus (Compatible)**
3. Click **Run workflow**
4. Provide your decrypted YouTube 21.x IPA URL
5. Download the artifact or create a release

### Manual Building

See [YTLitePlus/Building - Wiki](https://github.com/YTLitePlus/YTLitePlus/wiki/Building)

**Important:** Use `Makefile.compatible` instead of the default `Makefile`:
```bash
cp Makefile.compatible Makefile
make package SIDELOAD=1 THEOS_PACKAGE_SCHEME=rootless FINALPACKAGE=1
```

---

## 🔀 Branches

| Branch | Description |
|--------|-------------|
| `main` | Original YTLitePlus (may have compatibility issues) |
| `yt21-compatible` | YouTube 21.x compatible version |
| `improvements` | Latest improvements and fixes |

---

## 📋 Changelog

See [CHANGELOG.md](CHANGELOG.md) for detailed version history.

---

## 🙏 Credits

### Original YTLitePlus Team
- [dayanch96](https://github.com/dayanch96) - YTLite
- [Balackburn](https://github.com/Balackburn) - YTLitePlus
- [PoomSmart](https://github.com/PoomSmart) - Multiple tweaks
- [qnblackcat](https://github.com/qnblackcat) - uYouPlus
- [bhackel](https://github.com/bhackel) - Multiple features
- [arichornloverALT](https://github.com/arichornloverALT) - Multiple features

### Fork Modifications
- YouTube 21.x compatibility fixes
- Crash protection implementation
- Google Sign-in fix re-enablement

See the full credits list in the [original repository](https://github.com/YTLitePlus/YTLitePlus).

---

## ⚠️ Disclaimer

This is an unofficial fork. For the official YTLitePlus, visit [YTLitePlus/YTLitePlus](https://github.com/YTLitePlus/YTLitePlus).

---

## 📄 License

This project is licensed under the same terms as the original YTLitePlus project.
