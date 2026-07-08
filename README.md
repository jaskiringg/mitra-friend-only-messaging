# Mitra — Friend-Only Messaging

Messaging only after a friend request is **sent and accepted**. Chat UI + realtime come from [CometChat](https://www.cometchat.com); pending-request lifecycle and backend enforcement live in this repo.

## Demo users

**Aarav Mehta**, **Priya Iyer**, **Kabir Shah**, **Diya Nair** — open two windows and walk: discover → request → accept → chat.

## What this repo owns

| Concern | Owner |
|---|---|
| Tokens, presence, chat UI | CometChat UI Kit |
| Pending friend requests | This backend (Prisma + SQLite) |
| Hard messaging gate | CometChat Custom Moderation → `/api/cc-moderation` |

Non-friends cannot keep messages even via raw SDK calls — the moderation webhook deletes them.

## Stack

**Client:** React 18 · Vite · TypeScript · CometChat UI Kit  
**Server:** Express · TypeScript · Prisma · SQLite

## Run

```bash
cp server/.env.example server/.env
cp client/.env.example client/.env
cd server && npm i && npx prisma migrate deploy && npm run dev
cd client && npm i && npm run dev
```

Server `http://localhost:3001` · Client `http://localhost:5173`

More detail in [`docs/architecture.md`](docs/architecture.md).
