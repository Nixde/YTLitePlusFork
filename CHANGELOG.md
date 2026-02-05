# Changelog

All notable changes to this YTLitePlus Fork will be documented in this file.

## [Unreleased] - improvements branch

### Added
- **Crash Protection Layer**
  - Added `safeRespondsToSelector()` helper function for safe method checking
  - Added `safeValueForKey()` helper function with try-catch wrapper
  - Wrapped critical code paths in try-catch blocks

- **YouTube 21.x Compatibility Hooks**
  - Added `YTVersionUtils` hook to improve version compatibility
  - Added section markers and documentation throughout codebase

- **Re-enabled Google Sign-in Fix**
  - The `isSelf()` function has been re-enabled with additional safety checks
  - `NSBundle` hooks now have try-catch protection
  - Fixes Google Sign-in for sideloaded apps

### Changed
- **YTLite Version**: Upgraded from 5.0.1 → 5.2b4
  - Includes fixes for Shorts playback
  - Includes fixes for general playback stability
  - Built-in hold-to-speed feature (replaces YTHoldForSpeed tweak)

- **Build Workflow Updates**
  - Updated `buildapp-compatible.yml` to use YTLite 5.2b4
  - Fixed hardcoded version strings throughout workflow
  - Updated release naming conventions

- **README.md**: Complete rewrite for fork-specific documentation
  - Added compatibility information
  - Listed removed/included tweaks
  - Added build instructions for compatible version

### Removed
- **YTUHD**: Causes crashes on YouTube 21.x
- **YTHoldForSpeed**: Incompatible (functionality now in YTLite 5.2b4)
- **Return YouTube Dislikes**: Causes crashes in Shorts tab

### Fixed
- Fixed nil bundle crash by ensuring `lang/YTLitePlus.bundle` is embedded
- Fixed leftover commented code from disabled Google Sign-in section
- Fixed duplicate code blocks in YTLitePlus.xm

---

## [yt21-compatible] - 2026-02-05

### Added
- Created `Makefile.compatible` for YouTube 21.x builds
- Created `buildapp-compatible.yml` GitHub Actions workflow
- Added `lang/YTLitePlus.bundle` to EMBED_BUNDLES

### Changed
- Removed incompatible tweaks from build configuration
- Updated submodules to latest versions:
  - YouPiP: 1.12.10
  - YTVideoOverlay: 2.3.5
  - YTABConfig: 1.9.1
  - DontEatMyContent: v1.1.11

### Fixed
- Fixed `*** -[NSPlaceholderString initWithFormat:locale:arguments:]: nil argument` crash
- Added null safety to `LOC()` macro in YTLitePlus.h

---

## Original YTLitePlus

For the original YTLitePlus changelog, see the [upstream repository](https://github.com/YTLitePlus/YTLitePlus).
