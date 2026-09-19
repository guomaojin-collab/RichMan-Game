# RichMan World Backend Blueprint

This document defines the first cloud data model for the future global RichMan World platform.

## Core principle
Match Cash is temporary and belongs to one game session. Global Wealth belongs to a verified player account and can only be changed by server-side settlement rules.

## Entities

### users
- id
- display_name
- avatar_id
- created_at
- last_seen_at

### player_wallets
- user_id
- global_wealth
- updated_at

### friendships
- user_id
- friend_user_id
- status: pending | accepted | blocked
- created_at

### worlds
- id
- creator_user_id
- title
- description
- visibility: private | friends | public
- rules_json
- published_at
- play_count

### matches
- id
- world_id
- mode
- starting_cash
- started_at
- ended_at
- settlement_status

### match_players
- match_id
- user_id
- final_cash
- property_value
- stock_value
- final_net_worth
- placement

### wealth_ledger
Append-only ledger. Global Wealth should be derived/audited from this table.
- id
- user_id
- match_id nullable
- amount
- reason
- created_at

## Ranking
Global ranking should use server-side player_wallets.global_wealth. Client localStorage must never be accepted as ranking truth.

## Anti-abuse
- UGC/custom matches must use a lower or zero ranked reward multiplier.
- Ranked rewards are calculated by the server, not the browser.
- A match settlement has an idempotency key and can only credit once.
- Suspicious self-play / repeated opponent patterns can be excluded from ranked rewards.
- World creators cannot define Global Wealth payout directly.

## Cloudflare target architecture
- Static/game frontend: existing deployment
- API: Cloudflare Workers
- SQL data: Cloudflare D1
- Realtime rooms later: Durable Objects
- Uploaded map thumbnails/assets later: R2

## Migration path
1. Local RichMan ID prototype.
2. Cloud account/auth.
3. Server wallet + wealth ledger.
4. Global leaderboard.
5. Friends.
6. World Builder + published worlds.
7. Realtime multiplayer.
