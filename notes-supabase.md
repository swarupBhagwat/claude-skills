# Supabase Notes (Sample for testing skills)

## What is Supabase?

**Supabase** is an open-source backend-as-a-service platform, often described as an open-source alternative to Firebase. It bundles a hosted **PostgreSQL** database with a set of tools and APIs that let developers build applications quickly without managing their own backend infrastructure.

## Core Components

- **Database**: A full PostgreSQL database. Since it's standard Postgres, you can use SQL, extensions, foreign keys, and joins — unlike many NoSQL backend-as-a-service options.
- **Auth**: Handles user sign-up, login, and session management. Supports email/password, magic links, OAuth providers (Google, GitHub, etc.), and phone auth.
- **Storage**: An S3-compatible object storage service for files (images, videos, documents), with access controlled via policies similar to database rows.
- **Edge Functions**: Server-side TypeScript functions that run close to the user (on Deno), used for custom backend logic, webhooks, and integrations.
- **Realtime**: Allows clients to subscribe to database changes (inserts, updates, deletes) and receive live updates via WebSockets.
- **Auto-generated APIs**: Supabase automatically generates a RESTful API (via PostgREST) and GraphQL API based on your database schema.

## Row Level Security (RLS)

- **Row Level Security (RLS)** is a PostgreSQL feature that Supabase relies on heavily for securing data.
- When RLS is enabled on a table, **no rows are accessible by default** — you must write policies that explicitly allow access.
- A **policy** is a SQL rule defining who can `SELECT`, `INSERT`, `UPDATE`, or `DELETE` rows, often based on the authenticated user's ID (`auth.uid()`).
- RLS allows the same database to be safely queried directly from client-side code, since security is enforced at the database level rather than only in application code.

## Working with the Supabase Client

- The **Supabase client library** (available for JavaScript, Python, Dart, Swift, etc.) provides methods to query the database, manage auth, and interact with storage.
- Example concepts (not exact syntax):
  - `supabase.from('table').select()` — query rows from a table.
  - `supabase.auth.signUp()` / `supabase.auth.signInWithPassword()` — manage authentication.
  - `supabase.storage.from('bucket').upload()` — upload files to storage.
- Environment variables typically required: a **project URL** and an **API key** (anon/public key for client-side, service role key for trusted server-side use only).

## Migrations and Local Development

- Supabase supports a **CLI** for local development, allowing developers to run a local instance of the entire stack (database, auth, storage) using Docker.
- **Migrations** are SQL files that describe schema changes over time, allowing database structure to be version-controlled alongside application code.
- The CLI can generate TypeScript types directly from the database schema, improving type safety in client code.

## Quick Recap

- Supabase = hosted Postgres + Auth + Storage + Edge Functions + Realtime + auto-generated APIs.
- Because it's real Postgres, you get full SQL power (joins, foreign keys, extensions).
- Row Level Security (RLS) is the primary mechanism for securing data accessed directly from client apps — default is "deny all" until policies are added.
- The client library handles database queries, auth, and storage from a single SDK.
- The CLI supports local development (via Docker) and SQL migrations for version-controlled schema changes.
