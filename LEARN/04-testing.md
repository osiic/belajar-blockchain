# 4. Testing Smart Contracts

## Goal
Write Mocha/Chai tests and build confidence.

## Key Concepts
- Hardhat uses Mocha (test runner) + Chai (assertions) + ethers.js for calls.
- Arrange/Act/Assert structure keeps tests readable.
- Use fixtures or beforeEach to deploy fresh contracts.

## Try it
1) Create `test/storage.ts`:
```ts
import { ethers } from "hardhat";
import { expect } from "chai";

describe("Storage", () => {
  async function deploy() {
    const Storage = await ethers.getContractFactory("Storage");
    const storage = await Storage.deploy();
    return { storage };
  }

  it("sets and reads number", async () => {
    const { storage } = await deploy();
    await storage.setNumber(7);
    expect(await storage.number()).to.equal(7n);
  });

  it("rejects oversized values", async () => {
    const { storage } = await deploy();
    await expect(storage.setNumber(2_000_000)).to.be.revertedWith("Too big");
  });
});
```
2) Run tests: `npx hardhat test`.
3) Add another test: ensure event `NumberUpdated` emits expected args.

## Done when
Tests pass and you can explain how fixtures keep state isolated per test.
