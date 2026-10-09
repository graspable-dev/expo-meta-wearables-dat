# Graspable's fork

This is [graspable-dev](https://github.com/graspable-dev)'s fork of
[chrisgocode/expo-meta-wearables-dat](https://github.com/chrisgocode/expo-meta-wearables-dat), itself a
fork of [circus-kitchens/expo-meta-wearables-dat](https://github.com/circus-kitchens/expo-meta-wearables-dat).
Upstream stays the source of truth: fixes made here are offered back, and the package Graspable's
templates install is upstream's `@chrisgocode/expo-meta-wearables-dat` until this fork carries something
upstream does not take.

What this fork is for: verifying the module on real glasses through Graspable's Meta glasses template,
and keeping it in step with Meta's Device Access Toolkit.

## Verified on hardware

| Glasses            | Phone                 | Toolkit         | What was tried | Date       |
| ------------------ | --------------------- | --------------- | -------------- | ---------- |
| Ray-Ban Meta Gen 2 | iPhone 15 Pro, iOS 26 | DAT 1.0.1 (SPM) | in progress    | 2026-10-09 |

Rows are added only for what was actually run; nothing here is assumed from the SDK's own list.

## Notes from verification

- **Developer Mode can switch itself off when the Meta AI app updates.** Registration then fails in Meta AI with "Internal error, the operation could not be completed". Turn it on again (Settings, App Info, tap the version five times) and register again.
- **Leave `metaAppId` empty for Developer Mode.** With an id set, Meta AI checks the app against that integration in the Wearables Developer Center; an integration version made before toolkit 1.0 does not work with a 1.0 build and fails with the same message.
- Building the example on Xcode 26.6: CocoaPods needs a UTF-8 locale (`LANG=en_US.UTF-8`), and `expo run:ios --device` cannot read this Xcode's device list; build with `xcodebuild -destination generic/platform=iOS` and install with `xcrun devicectl device install app`.
