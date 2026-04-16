# TOOLS.md

## environment

- node 20+
- Expo SDK 52+
- Xcode (iOS) or Android Studio (Android) for native builds

## env vars

```
EXPO_PUBLIC_API_URL=
EXPO_PUBLIC_SENTRY_DSN=
```

## common commands

```bash
npx expo start              # dev server
npx expo run:ios            # iOS simulator
npx expo run:android        # Android emulator
eas build --platform ios    # iOS build
eas build --platform android # Android build
eas submit                  # submit to stores
```
