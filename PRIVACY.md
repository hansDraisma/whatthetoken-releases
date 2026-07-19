# Privacy

WhatTheToken is local-first. Provider credentials stay on your device. The app stores and displays only sanitized usage status.

## What the app may read

After explicit connector consent, a connector may read only the local provider state needed to request or observe usage status.

Claude Code may use the local Claude Code credential in memory after opt-in. Codex may connect to the local Codex app-server after opt-in. WhatTheToken does not copy provider credentials into its own storage.

## What the app never collects

WhatTheToken does not collect, persist, sync, log, fixture, or ask users to paste prompts, responses, conversation content, cookies, authorization headers, bearer tokens, provider session tokens, API keys, access tokens, raw provider payloads, raw local database rows, raw browser storage dumps, or sensitive local paths.

## Local storage

WhatTheToken may store sanitized status data including provider and product identifiers, quota pool and window identifiers, utilization or credit balance, reset and update timestamps, confidence labels, stale reasons, sanitized source state, connector enabled state, and app preferences.

The Mac app stores this data locally in its Application Support directory:

- `settings.json` for connector consent, refresh and notification preferences, and menu bar preferences
- `snapshot-cache.json` for sanitized usage snapshots, refresh timestamps, and sanitized provider error/backoff state
- `notification-state.json` for sanitized notification deduplication metadata

These files do not contain copied provider credentials, raw provider payloads, prompts, responses, cookies, authorization headers, or provider session tokens.

## Consent and disconnect

Connectors are disabled by default. A connector reads local provider state only after the user explicitly connects it. Pausing disables refresh while retaining sanitized cached values. Disconnecting disables future reads and removes that provider's cached usage and notification state.

## Diagnostics and Sentry

Diagnostics are redacted and inspectable before sharing.

When an official build is configured with a Sentry DSN, the app sends a narrowly scoped error only when a Claude usage response can no longer be safely parsed. That error contains the app version, a failure category, and sanitized provider field names. It does not contain the response body, usage values, reset timestamps, credentials, headers, account identifiers, or local paths.

Automatic Sentry crash, session, performance, network, hang, swizzling, and breadcrumb collection is disabled. Builds without a configured DSN send no Sentry events.

## Telemetry

Product telemetry is off by default. Any future telemetry must be opt-in and must not include forbidden sensitive data.

## Incident response

If sensitive data is reported or found, the maintainer removes the exposure, rotates affected credentials when applicable, audits nearby code paths, and documents the fix without repeating the sensitive data.
