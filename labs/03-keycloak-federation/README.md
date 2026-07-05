# Lab 03 — Keycloak federation 🚧

> **Status: in progress** — writeup being assembled.

## Scope

OIDC identity brokering and custom authentication flows in Keycloak:

1. **Brokering** — one Keycloak realm acting as broker to an external OIDC identity
   provider (login initiated at the broker, credentials never touch the app).
2. **Custom authentication flow** — modify the browser flow (e.g. conditional MFA
   step-up) and observe how execution requirements change the login journey.
3. **Realm export** — the same export format that
   [AgentLens](https://github.com/JOE07here/agentlens) consumes for risk scanning.

## Concepts this lab proves

- Federation trust: who authenticates vs who asserts vs who consumes
- OIDC flows in practice (authorization code, tokens, client types)
- Why authentication flow design is a security control, not just UX

*Problem / build / diagram / lessons sections land here once the writeup is done.*
