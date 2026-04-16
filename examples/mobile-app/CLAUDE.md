# CLAUDE.md

claude code config for this Expo project.
imports AGENTS.md.

import AGENTS.md

## expo specific rules

### before making changes

- check `app.json` for Expo config before modifying
- read existing screens in `app/` before creating new routes
- use Expo SDK docs: https://docs.expo.dev

### expo router conventions

- file-based routing — `_layout.tsx` for layouts
- `(tabs)` and `(modal)` groups for tab and modal routes
- use `redirect()` for server-side redirects
- use `Link` component for navigation, not `react-navigation`

### mobile patterns

- always handle safe area insets
- use `KeyboardAvoidingView` on screens with text inputs
- use `FlatList` for scrollable lists, never `ScrollView` for long lists
- handle both light and dark mode
