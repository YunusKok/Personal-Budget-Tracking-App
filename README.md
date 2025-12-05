# BudgetTracker - Personal Budget Management

A modern and stylish income/expense tracking application developed with React Native + Expo Router. Data is securely stored on-device using SQLite; it features user login, transaction management, weekly budget limits, and detailed reporting charts.

## Contents

  - Features
  - Screens
  - Installation and Running
  - Commands
  - Architecture and Folder Structure
  - Technologies
  - Development Notes

## Features

  - Add/delete income and expense transactions
  - Set weekly budget limits and view progress bar
  - Monthly total income/expense summaries
  - Line chart for income/expenses (last 7 days) and category-based bar charts
  - Simple session management with local email/password (via SQLite table)
  - Stylish UI, animations, and toast notifications

## Screens

  - **Login / Register:** Local user creation and login via simple email/password
  - **Home (Dashboard):** Balance, income, and expense cards; weekly budget progress; recent transactions list
  - **Add Transaction:** Select income/expense type, amount, description, category, and date/time
  - **Reports:** 7-day line chart, monthly category-based bar chart, category details

## Installation and Running

Prerequisites: Node.js LTS, pnpm/yarn/npm, Expo CLI (optional), Android Studio or Xcode (for native execution).

```bash
# Install dependencies
npm install

# Start development server
npm run start

# Run on Android device/emulator
npm run android

# Run on iOS simulator (macOS)
npm run ios

# Web (experimental)
npm run web
```

On first launch, the app creates `transactions` and `user` tables using `expo-sqlite`.

## Commands

  - `npm run start`: Starts the Expo Metro server
  - `npm run android`: Android build/run
  - `npm run ios`: iOS build/run
  - `npm run web`: Web target
  - `npm run lint`: Lint
  - `npm test`: Jest (watch mode)

## Architecture and Folder Structure

  - `app/_layout.tsx`: Providers and SQLite initialization
  - `app/(auth)/*`: `login.tsx`, `signup.tsx`, and stack layout
  - `app/(tabs)/*`: Tabs and pages: `index.tsx` (Dashboard), `add.tsx`, `reports.tsx`
  - `context/BudgetContext.tsx`: SQLite CRUD, totals, weekly budget
  - `context/AuthContext.tsx`: Simple user state and logout
  - `components/Toast.tsx`: Success/error notifications
  - `hooks/useFrameworkReady.ts`: Web ready signal

## Technologies

  - React Native 0.76, Expo 52, Expo Router 4
  - SQLite (expo-sqlite)
  - date-fns, react-native-chart-kit, react-native-reanimated
  - lucide-react-native icons, expo-linear-gradient, expo-blur

## Development Notes

  - **Database:** `transactions (id, amount, category, description, date, type)` and `user (id, email, password)` tables are created within `app/_layout.tsx`.
  - **Authentication:** Entirely local and simple; passwords are not hashed. A proper backend/authentication system is recommended for production security.
  - **Platform:** Web target may be limited; the primary target is mobile.

## License

This project is for educational and personal use. Add a license if necessary.
