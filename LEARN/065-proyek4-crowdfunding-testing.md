<p align="center">
  <a href="./064-proyek4-crowdfunding-kontrak.md">⬅️ Previous</a> |
  <a href="./066-proyek4-crowdfunding-frontend.md">Next ➡️</a>
</p>

---

# Proyek 4: Testing Crowdfunding

## Learning Objectives
- Menguji alur sukses dan gagal.
- Mensimulasikan waktu (deadline) di Hardhat.
- Memastikan keamanan reentrancy & pull pattern.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Gunakan time travel (`evm_increaseTime`). Pastikan claim hanya jika goal tercapai dan belum diklaim. Refund hanya jika gagal/cancelled. Nol-kan saldo sebelum transfer untuk mencegah reentrancy.

## Hands-on Practice
1) Buat `test/crowdfund.ts`:
```ts
import { expect } from "chai";
import { ethers } from "hardhat";

describe("Crowdfund", () => {
  async function deploy() {
    const [owner, alice, bob] = await ethers.getSigners();
    const CF = await ethers.getContractFactory("Crowdfund");
    const cf = await CF.deploy();
    return { cf, owner, alice, bob };
  }

  it("success path: create, contribute, claim", async () => {
    const { cf, owner, alice } = await deploy();
    await cf.create(ethers.parseEther("1"), 7 * 24 * 3600);
    await cf.connect(alice).contribute(0, { value: ethers.parseEther("1") });
    await ethers.provider.send("evm_increaseTime", [7 * 24 * 3600 + 1]);
    await expect(cf.connect(owner).claim(0)).to.emit(cf, "Claimed");
  });

  it("fail path: refund after deadline if goal not met", async () => {
    const { cf, alice } = await deploy();
    await cf.create(ethers.parseEther("2"), 1000);
    await cf.connect(alice).contribute(0, { value: ethers.parseEther("0.5") });
    await ethers.provider.send("evm_increaseTime", [1001]);
    await expect(cf.connect(alice).refund(0)).to.emit(cf, "Refunded");
    await expect(cf.connect(alice).refund(0)).to.be.revertedWith("nothing");
  });

  it("reverts contribute after deadline", async () => {
    const { cf, alice } = await deploy();
    await cf.create(1, 1);
    await ethers.provider.send("evm_increaseTime", [2]);
    await expect(cf.connect(alice).contribute(0, { value: 1 })).to.be.revertedWith("ended");
  });
});
```
2) Jalankan: `npx hardhat test`.

## Exercises / Mini Project
- Tambah test `cancel` oleh owner dan pastikan refund tetap bekerja.

## Quiz
- Q1: Bagaimana mensimulasikan waktu di Hardhat?
- Q2: Kapan claim diizinkan?
- Q3: Apa yang terjadi jika contributor refund dua kali?

## Skill Checklist
- [ ] Alur sukses/gagal teruji.
- [ ] Deadline diuji dengan time travel.
- [ ] Reentrancy dicegah (saldo nol sebelum transfer).

---

<p align="center">
  <a href="./064-proyek4-crowdfunding-kontrak.md">⬅️ Previous</a> |
  <a href="./066-proyek4-crowdfunding-frontend.md">Next ➡️</a>
</p>
