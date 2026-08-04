# Architecture summary

This document describes the product architecture without exposing private source code, operational configuration, or data.

## Design goals

- Keep business data under the user's control
- Make the application easy to run locally
- Preserve relationship history
- Provide useful recommendations without requiring an external AI service
- Protect data during imports, edits, and restores
- Keep workflows understandable to a non-technical operator

## Application layers

### Browser interface

Server-rendered pages provide dashboards, work queues, record views, forms, timelines, briefings, search, and reports. A shared responsive visual system supports desktop and mobile use.

### Application layer

The Python application handles routing, validation, business rules, rendering, analytics, imports, exports, and backup workflows.

### Relationship and sales intelligence

Deterministic logic turns structured CRM history into health, momentum, risk, coverage, readiness, and next-action signals. An AI provider abstraction allows optional AI features while retaining a no-AI operating mode.

### Data layer

SQLite stores canonical CRM records and normalized history. Records can be visible in multiple workspaces without requiring duplicate copies. Additive migrations preserve compatibility as the schema grows.

### Safety layer

The system includes duplicate checks, import preview, field mapping, backup-first changes, restore confirmation, and restrictive relationships between dependent records.

## Core product areas

- Contacts and companies
- Interactions and relationship timelines
- Tasks, follow-ups, and work queues
- Opportunities and products
- Meetings and meeting preparation
- Research and knowledge
- Campaigns and outreach drafts
- Briefings, reviews, reports, and analytics
- AI-assisted recommendations
- Imports, exports, backups, and settings

## Current engineering tradeoffs

The dependency-light design keeps installation simple and the local runtime understandable. The current application is intentionally compact, but future work will separate large internal modules, add browser end-to-end coverage, and optimize list and analytics queries for larger datasets.

