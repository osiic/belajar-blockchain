# 2. Solidity Basics

## Goal
Understand language essentials and extend the existing Storage contract.

## Key Concepts
- Data locations: storage, memory, calldata.
- Visibility: public / external / internal / private.
- Functions: view/pure vs state-changing.
- Events: lightweight logging; indexed params aid filtering.
- Errors/reverts: `require`, `revert`, `assert`.

## Try it
1) Add a getter event and bounds check to `contracts/Storage.sol`:
```solidity
// emit when value changes
event NumberUpdated(uint256 indexed previous, uint256 indexed current, address indexed caller);
```
2) Modify `setNumber` to `require(_num <= 1_000_000, "Too big");` then emit the event.
3) Recompile: `npx hardhat compile` (fix warnings).

## Done when
- Compile passes.
- You can explain difference between storage/memory and why events matter.
