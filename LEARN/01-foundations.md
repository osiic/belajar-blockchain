# 1. Foundations & Setup

## Goal
Get a mental model of the stack and verify your tools.

## Key Concepts
- EVM: deterministic state machine; executes bytecode; gas metering prevents infinite loops.
- Accounts: EOAs (key-based) vs contract accounts (code + storage).
- Transactions: signed messages that can transfer ETH and/or trigger code.
- Networks: local Hardhat, testnets (Sepolia/Holesky), mainnet.

## Setup Checklist
- Node 18+ and npm installed (`node -v` / `npm -v`).
- Hardhat already in devDeps; TypeScript available.

## Try it
1) Verify environment:
```bash
node -v
npm -v
npx hardhat --version
```
2) Read current contract: `contracts/Storage.sol`.
3) Sketch data flow: user -> front end -> contract call -> state change.

## Done when
You can explain EOAs vs contracts and run `npx hardhat --version` without errors.
