# FitMorph AI

A premium AI-powered fitness and body transformation mobile app built with Expo React Native.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- Mobile: Expo SDK 54, Expo Router (file-based routing)
- UI: React Native, LinearGradient, BlurView, Reanimated
- State: AsyncStorage (local), React Query (server)
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/mobile/` — Expo mobile app
- `artifacts/mobile/app/` — file-based routes (Expo Router)
- `artifacts/mobile/components/` — shared UI components (GlassCard, GradientButton, StatCard, ProgressRing, WorkoutCard)
- `artifacts/mobile/context/AppContext.tsx` — global state (user profile, stats, chat, meals, weight log)
- `artifacts/mobile/constants/colors.ts` — brand color tokens (dark + light)
- `artifacts/mobile/assets/images/` — app icon, hero-bg, body-scan

## Architecture decisions

- Dark mode forced via `userInterfaceStyle: "dark"` in app.json and background color `#07070E`
- Glassmorphism cards use `expo-blur` BlurView + `rgba` background layering
- All data is persisted to AsyncStorage — no backend needed for first build
- AI coach uses client-side pattern matching for fitness responses (upgradeable to real LLM)
- Onboarding flow uses stack navigation; main app uses 5-tab layout

## Product

FitMorph AI helps users transform their bodies using:
1. **Welcome + Onboarding** — cinematic dark intro, goal selection (Fat Loss / Muscle / Lean / Athletic / Six-Pack), body type selection (Ecto / Meso / Endo), AI analysis animation
2. **Dashboard** — body score ring, calorie/protein/water stats, AI insight card, quick actions, today's workout, macro summary
3. **Workout Planner** — 6 pre-built plans, category filter (All / Strength / HIIT / Fat Loss / Mobility / Home), expandable exercise lists with start button
4. **AI Coach Chat** — inverted FlatList chat UI, pattern-matched AI responses, quick suggestion chips
5. **Nutrition Tracker** — calorie ring, macro tracking (protein/carbs/fat), water glass tracker, meal log, quick-add meal sheet
6. **Progress Tracker** — body score, weight trend chart (SVG), body stats grid, goal progress bar, achievement badges, photo comparison CTA

## User preferences

- Dark mode default with premium aesthetic
- Design: glassmorphism + gradient accents, neon purple (#8B5CF6) + electric cyan (#06B6D4) + pink (#EC4899)
- Target audience: Gen Z / Millennials, beginners, South Asian users

## Gotchas

- `useNativeDriver: true` animations fall back to JS on web (harmless warning)
- Run `pnpm install` before restarting the mobile workflow if node_modules are missing

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
