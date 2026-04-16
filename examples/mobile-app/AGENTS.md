# AGENTS.md

this file tells AI coding agents how to behave in this React Native / Expo project.

## project overview

a cross-platform mobile app built with Expo and React Native.

## tech stack

- **framework:** Expo SDK 52+
- **language:** TypeScript
- **navigation:** Expo Router
- **styling:** NativeWind (Tailwind for RN) or StyleSheet
- **state:** Zustand or React Query
- **deployment:** EAS Build

## rules

### do

- use Expo Router for navigation — file-based routing
- use TypeScript strict mode
- put screens in `app/` (Expo Router convention)
- put reusable components in `components/`
- use React Query for server state, Zustand for client state

### don't

- don't use React Navigation directly — use Expo Router
- don't put API calls in components — use custom hooks
- don't hardcode API URLs — use `process.env.EXPO_PUBLIC_API_URL`
- don't ignore safe area insets
- don't skip keyboard handling on input screens

## code style

- screens: PascalCase (`ProfileScreen.tsx`)
- components: PascalCase (`UserCard.tsx`)
- hooks: camelCase, starts with `use` (`useAuth.ts`)
- constants: UPPER_CASE

## architecture

```
app/              ← routes (Expo Router)
components/       ← reusable UI components
hooks/            ← custom hooks
lib/              ← utilities, API client, config
store/            ← Zustand stores
assets/           ← images, fonts, icons
```

## how to run

```bash
npm install
npx expo start        # dev server
npx expo run:ios      # iOS simulator
npx expo run:android  # Android emulator
eas build --platform all   # production build
```

## testing

- jest with jest-expo preset, run with `npm run test`
- tests live next to the code they test: `useAuth.test.ts`, `UserCard.test.tsx`

### what to test

- **always test:** custom hooks, utility functions, API client logic, state stores
- **usually test:** complex interactive components, navigation guards, form validation
- **skip testing:** static screens, simple layout components, third-party wrappers

### test patterns

```tsx
// hooks/useAuth.test.ts
import { renderHook, act } from "@testing-library/react-native";
import { useAuth } from "./useAuth";
test("starts logged out", () => {
  const { result } = renderHook(() => useAuth());
  expect(result.current.isLoggedIn).toBe(false);
});

// components/UserCard.test.tsx
import { render, screen } from "@testing-library/react-native";
import { UserCard } from "./UserCard";
test("displays user name", () => {
  render(<UserCard name="Alice" />);
  expect(screen.getByText("Alice")).toBeTruthy();
});
```

## security

- see `SECURITY.md`
- no secrets in client code — use a backend API
- secure storage for tokens (expo-secure-store)
- certificate pinning for production
