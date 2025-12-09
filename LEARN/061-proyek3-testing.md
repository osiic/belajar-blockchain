<p align="center">
  <a href="./060-proyek3-frontend.md">⬅️ Previous</a> |
  <a href="./062-milestone3-review.md">Next ➡️</a>
</p>

---

# Proyek 3: Testing DAO

## Learning Objectives
- Menulis test proposal/vote/finalize.
- Menguji quorum, threshold, dan deadline.
- Memvalidasi voting power snapshot (getPastVotes).

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Pastikan snapshot block dipakai (bukan balance terbaru). Uji quorum sukses/gagal, double vote, delegasi, dan waktu voting menggunakan time travel Hardhat.

## Hands-on Practice
1) Buat `test/dao.ts`:
```ts
import { expect } from "chai";
import { ethers } from "hardhat";

describe("SimpleDAO", () => {
  async function deploy() {
    const [owner, alice, bob] = await ethers.getSigners();
    const Gov = await ethers.getContractFactory("GovToken");
    const gov = await Gov.deploy();
    const DAO = await ethers.getContractFactory("SimpleDAO");
    const dao = await DAO.deploy(await gov.getAddress());
    await gov.delegate(owner.address);
    return { owner, alice, bob, gov, dao };
  }

  it("uses snapshot for voting power", async () => {
    const { owner, alice, gov, dao } = await deploy();
    await dao.createProposal("Test");
    await gov.transfer(alice.address, ethers.parseEther("1000")); // after snapshot
    await expect(dao.connect(alice).vote(0, true)).to.be.revertedWith("no power");
    await dao.vote(0, true); // owner votes
  });

  it("finalizes with quorum check", async () => {
    const { dao } = await deploy();
    await dao.createProposal("Quorum");
    await dao.vote(0, true);
    await ethers.provider.send("evm_increaseTime", [3 * 24 * 3600 + 1]);
    await dao.finalize(0);
    const p = await dao.proposals(0);
    expect(p.finalized).to.be.true;
  });
});
```
2) Tambah test double vote (revert) dan quorum gagal (yes+no di bawah quorum).

## Exercises / Mini Project
- Tambah test abstain jika diimplementasi; pastikan tidak dihitung ke quorum.

## Quiz
- Q1: Mengapa gunakan getPastVotes?
- Q2: Bagaimana mensimulasikan waktu lewat?
- Q3: Kasus apa jika quorum tidak terpenuhi?

## Skill Checklist
- [ ] Alur proposal→vote→finalize teruji.
- [ ] Quorum/deadline diuji.
- [ ] Snapshot voting diverifikasi.

---

<p align="center">
  <a href="./060-proyek3-frontend.md">⬅️ Previous</a> |
  <a href="./062-milestone3-review.md">Next ➡️</a>
</p>
