# 05. Testing dengan Mocha/Chai

## Konsep
- Struktur test: Arrange -> Act -> Assert.
- Fixture: `hre.deployments` atau fungsi helper untuk deploy ulang cepat.
- Assertion: Chai `expect`, memeriksa revert dengan `.to.be.revertedWith`.

## Langkah Praktik
1) Buat folder `test/` jika belum ada. Isi `test/storage.ts`:
```ts
import { ethers } from "hardhat";
import { expect } from "chai";

describe("Storage", () => {
  async function deploy() {
    const Storage = await ethers.getContractFactory("Storage");
    const storage = await Storage.deploy();
    return { storage };
  }

  it("menyetel dan membaca angka", async () => {
    const { storage } = await deploy();
    await storage.setNumber(7);
    expect(await storage.number()).to.equal(7n);
  });

  it("harus emit NumberUpdated", async () => {
    const { storage } = await deploy();
    await expect(storage.setNumber(8))
      .to.emit(storage, "NumberUpdated")
      .withArgs(0, 8, (await ethers.getSigners())[0].address);
  });

  it("menolak nilai terlalu besar", async () => {
    const { storage } = await deploy();
    await expect(storage.setNumber(2_000_000)).to.be.revertedWith("Too big");
  });
});
```
2) Jalankan: `npx hardhat test`.
3) Tambah test untuk kasus edge (nilai sama dua kali, dsb.).

## Selesai Ketika
Semua test hijau dan kamu nyaman menambah kasus baru.

---
<p align="center">
  <a href="04-tasks-scripts.md">⬅️ Previous</a> |
  <a href="06-erc20.md">Next ➡️</a>
</p>
