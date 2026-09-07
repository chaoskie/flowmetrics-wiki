# CONV-001: Module layout

- Status: current
- Owner: Mara Visser
- Date: 2024-03-01

`app/src/clients/` talks to other systems. `app/src/lib/` holds shared
helpers with no business logic. `app/src/routes/` maps HTTP to services.
Business logic lives in `app/src/*.ts` (today: `billing.ts`). Tests mirror
the source tree under `app/test/`.

Before writing a helper, search `lib/` for one that exists (CONV-004).
