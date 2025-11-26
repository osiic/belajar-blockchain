# 4. Testing Smart Contract

## Tujuan
Menulis test Mocha/Chai dan membangun kepercayaan kode.

## Konsep Kunci
- Hardhat memakai Mocha (runner) + Chai (assertion) + ethers.js untuk call.
- Pola Arrange/Act/Assert menjaga test tetap jelas.
- Gunakan fixture atau `beforeEach` untuk deploy ulang kontrak.

## Coba
1) Buat `test/storage.ts`:
```ts
import { ethers } from "hardhat";
import { expect } from "chai";

describe("Storage", () => {
  async function deploy() {
    const Storage = await ethers.getContractFactory("Storage");
    const storage = await Storage.deploy();
    return { storage };
  }

  it("menyetel dan membaca number", async () => {
    const { storage } = await deploy();
    await storage.setNumber(7);
    expect(await storage.number()).to.equal(7n);
  });

  it("menolak nilai terlalu besar", async () => {
    const { storage } = await deploy();
    await expect(storage.setNumber(2_000_000)).to.be.revertedWith("Too big");
  });
});
```
2) Jalankan test: `npx hardhat test`.
3) Tambah test lain: pastikan event `NumberUpdated` emit dengan argumen benar.

## Selesai ketika
Test lulus dan kamu bisa jelaskan bagaimana fixture membuat state terisolasi per test.
