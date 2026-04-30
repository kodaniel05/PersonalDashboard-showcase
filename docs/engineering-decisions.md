# Engineering Decisions

## Documentation-Only Public Repository

The most important decision for this showcase was to separate public portfolio material from the private application. This repository documents the product and engineering approach without publishing the working implementation.

Why it matters:

- Protects private data and intellectual property.
- Prevents accidental exposure of API keys or tokens.
- Lets recruiters evaluate product thinking and architecture safely.
- Keeps the public repository polished without turning it into a cloneable app.

## Widget Registry Architecture

The private app uses a registry-style pattern to map widget IDs to feature modules. This allows dashboard views to compose widgets declaratively while keeping each widget independently maintainable.

Benefits:

- Easier feature growth.
- Clear ownership boundaries.
- Less coupling between dashboard layout and feature internals.
- Reusable widgets across multiple views.

## View-Based Workflows

The dashboard is organized by user workflow rather than by implementation type. For example, finance tools live together, personal reflection tools live together, and travel/food tools live together.

This makes the product easier to navigate and gives each view a clear purpose.

## Local-First Persistence

Personal information is stored locally in the browser in the private app. This fits the product’s privacy goals and keeps the dashboard lightweight.

Tradeoffs:

- Local storage is convenient and fast.
- Browser storage is not a replacement for encrypted cloud backup.
- Production-grade sync would require stronger authentication, backend storage, and export/recovery flows.

## Optional External Integrations

External services are treated as optional enhancements. If credentials are missing or requests fail, widgets should show disabled, delayed, offline, or unavailable states rather than breaking the dashboard.

This decision improves reliability and makes local development easier.

## TypeScript and Defensive Parsing

The app uses TypeScript and explicit normalization around external responses and stored data. This reduces runtime surprises as widgets evolve and as browser-stored data changes shape over time.

## Public Screenshot Strategy

Screenshots should be captured from sanitized demo data. This is especially important for finance, documents, relationships, notes, and personal records.

Public screenshots should not show:

- Real names, phone numbers, emails, addresses, account balances, documents, or private notes.
- API keys or environment values.
- Client data or proprietary workflows.
- Anything that would make the private project easy to reproduce.

## Future AI Boundary

The architecture can support AI-assisted features later, but any AI feature should respect explicit consent and privacy. Personal content should not be sent to third-party services without a clear user action and a redaction strategy.
