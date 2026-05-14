# routines-relay — Claude Code Guide

A mail relay for daily-check routines. Receives routine status reports and forwards them via email.

## Conventions

- All mail credentials via environment variables — never hardcoded
- Keep the relay stateless and side-effect-free beyond sending mail
