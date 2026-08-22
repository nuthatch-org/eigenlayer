---
name: nuthatch
description: Query this self-hosted nuthatch nest on mainnet - decoded events, balances, and read-only SQL. Use when asked about on-chain activity for these contracts.
---

# Querying the nuthatch nest

Contracts indexed on mainnet:
- `delegation` = 0x39053d51b77dc0d36036fc1fcc8cb819df8ef37a
- `strategy` = 0x858646372cc42e1a627fce94aa7a7033e7cf075a
- `eigenpod` = 0x91e677b07f7af907ec9a428aafa9fc14a0d3a338
- `avs_directory` = 0x135dda560e946695d6f155dacafc6f1f25c1f5af

Data is local - never call an external API for it.

## Preferred: MCP
If a `nuthatch` MCP server is configured, use its tools. Call `schema` first to learn the
data model, then `sql` / `entity` / `balance` / `top_balances`.

## Fallback: HTTP (a `nuthatch dev` must be running)
- Recent rows:  `curl localhost:8288/entities?limit=20`
- Read-only SQL: `curl -G localhost:8288/sql --data-urlencode 'q=SELECT count(*) FROM transfers'`

`sql` sees finalized data only; balances/entity cover the live tip.
