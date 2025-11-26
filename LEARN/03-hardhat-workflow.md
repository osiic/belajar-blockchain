# 3. Hardhat Workflow

## Goal
Get fluent with Hardhat tasks, console, and script execution.

## Key Concepts
- Hardhat Network (in-memory, auto-mines).
- Tasks: built-ins (`compile`, `test`, `node`, `run`) and custom.
- Scripts: `npx hardhat run` executes JS/TS scripts against a network.

## Try it
1) Inspect `hardhat.config.ts` (already targets Solidity 0.8.28).
2) Start a local node:
```bash
npx hardhat node
```
3) In another terminal, deploy using the existing script:
```bash
npx hardhat run scripts/deploy.js --network localhost
```
4) Use the console to interact:
```bash
npx hardhat console --network localhost
> const storage = await ethers.getContractAt("Storage", "<address from deploy>");
> await storage.setNumber(42);
> (await storage.number()).toString();
```

## Done when
You can start/stop `npx hardhat node`, deploy, and read/write state via console.
