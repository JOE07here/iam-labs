# IAM Labs

Hands-on Identity & Access Management labs by [Joemon Johnson](https://github.com/JOE07here) —
IAM Engineer (Okta · Microsoft Entra ID · Keycloak · MidPoint), Leipzig.

Every writeup follows the same format:

> **Problem → What I built → How it maps to a real IAM concept (JML / RBAC / SoD / ZTA) → Diagram → What broke & what I learned**

The goal is proof of work, not tutorials: each lab is something I actually ran, with the
mistakes left in.

## Labs

| # | Lab | Core concepts | Status |
|---|-----|---------------|--------|
| 01 | [MidPoint end-to-end provisioning](labs/01-midpoint-provisioning/) | JML, source/target resources, connectors, provisioning | ✅ Written up |
| 02 | [MidPoint RBAC + SoD](labs/02-midpoint-rbac-sod/) | Role mining, role models, SoD policy | 🚧 In progress |
| 03 | [Keycloak federation](labs/03-keycloak-federation/) | OIDC brokering, custom authentication flows | 🚧 In progress |

## Related work

- **[AgentLens](https://github.com/JOE07here/agentlens)** — browser-only risk scanner for
  non-human / AI-agent identities across MidPoint + Keycloak
  ([live demo](https://joe07here.github.io/agentlens/))
- **Zero Trust thesis** — evaluating MidPoint & Keycloak against NIST SP 800-207
