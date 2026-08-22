# Dayflow

> Your workday, simplified.

Dayflow is a mobile-first HR Management System built with Expo, React Native, TypeScript, and Expo Router. It gives employees and HR/Admin teams one clear home for attendance, leave, payroll, people operations, and reporting.

## Quick start

```bash
npm install
npm run start
```

Use Expo Go or an iOS/Android simulator. The app defaults to a mock data layer, so the full hackathon demo works without a backend.

## Demo accounts

| Role | Email | Password |
| --- | --- | --- |
| Employee | `employee@dayflow.demo` | `demo123` |
| HR | `hr@dayflow.demo` | `demo123` |
| Admin | `admin@dayflow.demo` | `demo123` |

The employee and HR accounts share Zustand state. This makes the core demo flow possible: submit leave as Employee, sign in as HR, approve it, then return to Employee and see the updated status.

## Architecture

- `app/` contains Expo Router screens only. Route files compose hooks and reusable components.
- `src/components/` contains shared UI and domain components. Employee and HR surfaces do not duplicate feature UI.
- `src/store/` owns mock-backed client state and is the replacement seam for server state during the hackathon.
- `src/api/` contains typed Axios contracts. Screens never call Axios directly.
- `src/data/` contains realistic demo fixtures that can be removed when the backend is connected.
- `src/validation/` contains Zod schemas used by React Hook Form.
- `docs/` contains screen flow, API contracts, and GitHub workflow guidance.

## Environment

Copy `.env.example` to `.env` when connecting a backend. Expo exposes public variables through `EXPO_PUBLIC_*` names. API URLs are configured only in `src/api/client.ts`.

## Quality checks

```bash
npm run typecheck
```

Before merging, check the mobile layout, role redirects, loading and error states, and the complete demo flow on a device or simulator.

## Team ownership

The work is split by domain to keep parallel changes focused. See [`docs/github-workflow.md`](docs/github-workflow.md) for branch names, commit conventions, and integration rules.
