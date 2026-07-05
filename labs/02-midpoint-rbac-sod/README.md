# Lab 02 — MidPoint RBAC + SoD 🚧

> **Status: in progress** — lab runs on [demo.evolveum.com](https://demo.evolveum.com),
> writeup being assembled.

## Scope

Role mining → role model → separation-of-duties policy:

1. **Role mining** — start from raw entitlement assignments and identify candidate
   business roles.
2. **Role model** — build a layered model (business roles composed of application roles)
   and assign by org membership.
3. **SoD policy** — define exclusion constraints between conflicting roles (e.g. a role
   that requests payments must never be held together with one that approves them) and
   watch midPoint block/flag the violating assignment.

## Concepts this lab proves

- RBAC as a governance tool, not just a permission shortcut
- Why role explosion happens and how layering contains it
- Preventive vs detective SoD controls

*Problem / build / diagram / lessons sections land here once the writeup is done.*
