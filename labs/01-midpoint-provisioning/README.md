# Lab 01 — MidPoint end-to-end provisioning (HR → midPoint → LDAP)

Built while working through **MID301 – MidPoint Deployment: First Steps** (midPoint 4.8-LTS),
then rebuilt locally as a Docker stack I could break and fix on my own.

## Problem

A company hires, moves and fires people in an HR system, but accounts live in a directory.
Without an IdM hub in the middle, every joiner/mover/leaver event becomes a manual ticket —
slow for joiners, dangerous for leavers (orphaned accounts with live credentials).

The lab: stand up a complete identity pipeline where **HR is the source of truth** and the
directory is a managed target, with midPoint enforcing the lifecycle in between.

## What I built

A six-container Docker stack:

| Role | Service | Image |
| --- | --- | --- |
| Source system | `hr` + `hr-db` | `tomcat:9.0.80-jre11-temurin` + `postgres:11-alpine3.17` |
| IdM hub | `midpoint-server` + `midpoint-data` | `evolveum/midpoint:4.8-alpine` + `postgres:16-alpine` |
| Target system | `ad` (OpenLDAP) | `osixia/openldap:1.5.0` |
| Target admin UI | `phpldapadmin` | `osixia/phpldapadmin:stable` |
| Navigation portal | `portal` | `nginx:1.24.0-alpine` → http://localhost |

Identity flow: **HR (source) → midPoint → OpenLDAP (target)**

- The HR app writes employees to its own PostgreSQL database.
- midPoint reads them through a **source resource** (DatabaseTable connector), turning HR
  rows into midPoint users via **inbound mappings**.
- A **target resource** (LDAP connector) projects those users into OpenLDAP via
  **outbound mappings** — account creation, attribute sync, and deactivation follow the
  user's lifecycle state automatically.

## How it maps to real IAM concepts

- **JML (Joiner–Mover–Leaver):** a new HR row = joiner → account provisioned in LDAP; an
  HR attribute change = mover → attributes synced; HR termination = leaver → account
  disabled/deprovisioned. Nobody touches the directory by hand.
- **Source vs target authority:** HR is authoritative for identity data; the directory is
  never edited directly. This is the single most common real-world IGA pattern.
- **Connectors & mappings:** the same mental model as any commercial IGA tool
  (SailPoint, Saviynt, One Identity) — midPoint just makes the machinery visible.
- **Reconciliation:** midPoint can compare its view against the target and flag/fix drift —
  the answer to "someone created an account directly in LDAP."

## Diagram

[`stack-architecture.drawio`](stack-architecture.drawio) — open with
[app.diagrams.net](https://app.diagrams.net/).

## What broke & what I learned

<!-- TODO(Joe): fill in your own war stories from running the stack, e.g. container
     start-order issues, connector configuration errors, a mapping that didn't fire,
     LDAP schema mismatches. 3–5 bullets in your own words make this section the most
     credible part of the writeup. -->

*Being written up — notes are on paper, moving them here.*
