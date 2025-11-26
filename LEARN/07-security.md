# 7. Security & Gas Hygiene

## Goal
Adopt safe defaults before mainnet.

## Key Concepts
- Common risks: reentrancy, integer overflow (checked by default in 0.8+), access control mistakes, unbounded loops.
- Checks-Effects-Interactions pattern; prefer `pull` payments.
- Gas tips: avoid unbounded state growth, pack storage where sensible, short revert strings.

## Try it
1) Add a simple access control to `setNumber` (e.g., owner-only) using `address public owner;` and `constructor() { owner = msg.sender; }`.
2) Add a modifier `onlyOwner` and protect mutating functions.
3) Run tests and add a test that non-owners revert.
4) Run `npx hardhat test` and note gas reports if enabled (consider adding the `hardhat-gas-reporter` plugin later).

## Done when
You can articulate how Checks-Effects-Interactions reduces risk and have a passing non-owner revert test.
