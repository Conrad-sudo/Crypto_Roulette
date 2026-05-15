# Crypto Roulette

A web-based European Roulette game built with React and integrated with the Ethereum blockchain via the [thirdweb](https://thirdweb.com/) SDK.

## Overview

Players connect their Web3 wallet, place bets on the roulette table, and spin the wheel. The app tracks spins, wins, losses, and a coin balance entirely on the frontend. The thirdweb `ConnectWallet` button handles wallet connection on the Ethereum mainnet.

## Features

- Animated roulette wheel rendered on an HTML5 Canvas
- Full betting table supporting all standard bet types:
  - Straight (single number) — 35:1
  - Split (2 numbers) — 17:1
  - Street (3 numbers) — 11:1
  - Corner (4 numbers) — 8:1
  - Six-line (6 numbers) — 5:1
  - Dozens (1st/2nd/3rd 12) — 1:1
  - Columns (2:1) — 2:1
  - Even-money bets: Red/Black, Odd/Even, 1–18/19–36 — 1:1
- Chip placement and coin balance tracking
- thirdweb wallet connection (Ethereum)
- Deployable to IPFS via `thirdweb upload`

## Tech Stack

| Layer | Library / Tool |
|---|---|
| UI Framework | React 18, React Bootstrap |
| Blockchain | thirdweb v3, ethers v5 |
| Styling | Bootstrap 4.6, custom CSS |
| Icons | react-icons |
| Deployment | thirdweb IPFS upload |

## Getting Started

### Prerequisites

- Node.js 16+
- npm or yarn

### Install

```bash
npm install
# or
yarn
```

### Run locally

```bash
npm start
# or
yarn start
```

Opens at [http://localhost:3000](http://localhost:3000).

### Build

```bash
npm run build
```

### Deploy to IPFS (thirdweb)

```bash
yarn deploy
# equivalent to: yarn build && npx thirdweb@latest upload build
```

## Project Structure

```
src/
  App.js                  # Root component — game state and bet resolution logic
  components/
    weel/Weel.js          # Canvas roulette wheel + spin animation
    table/Table.js        # Betting table layout
    table/rows/           # JSON definitions for each table row/column/border
    chips/Chips.js        # Chip selector component
  index.js                # ThirdwebProvider setup (activeChain: ethereum)
```

## Environment Variables

| Variable | Description |
|---|---|
| `GENERATE_SOURCEMAP` | Set to `false` to disable source maps in production builds |

## Known Limitations / TODO

- Basket bet (0, 00, 1, 2, 3 — 6:1) is not yet implemented
- Coin balance and stats are in-memory only (no on-chain persistence)
- No smart contract integration yet — bets are resolved client-side
