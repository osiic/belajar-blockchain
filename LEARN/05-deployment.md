# 5. Deployment & Networks

## Goal
Understand network configs and safe deployment habits.

## Key Concepts
- Networks: `localhost`, `sepolia`, `mainnet`. Each needs RPC URL + account key.
- Environment variables: store secrets in `.env` (never commit).
- Gas & confirmations: estimate first; wait for confirmations on live nets.

## Try it
1) Install dotenv if needed:
```bash
npm install --save-dev dotenv
```
2) Extend `hardhat.config.ts` with a `sepolia` network using `process.env.SEPOLIA_RPC` and `PRIVATE_KEY` (do not commit keys).
3) Update `scripts/deploy.js` to log the network name and handle missing keys gracefully.
4) Dry-run: `npx hardhat run scripts/deploy.js --network localhost` (should still work).

## Done when
You can describe what changes between localhost and testnet deploys and how to keep keys out of git.
