<p align="center">
  <a href="./053-proyek2-marketplace-kontrak.md">⬅️ Previous</a> |
  <a href="./055-proyek2-frontend.md">Next ➡️</a>
</p>

---

# Proyek 2: Testing NFT & Marketplace

## Learning Objectives
- Menguji alur mint, list, buy, cancel secara menyeluruh.
- Memeriksa event, saldo pending, dan fee.
- Menguji kasus gagal (tanpa approval, dana kurang, non-seller cancel).

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Gunakan fixture untuk deploy NFT + Market. Uji happy path dan revert: underpay, tanpa approval, cancel oleh non-seller, double buy. Pastikan pending balance tercatat.

## Hands-on Practice
1) Buat `test/market.ts`:
```ts
import { expect } from "chai";
import { ethers } from "hardhat";

describe("MarketNFT + SimpleMarket", () => {
  async function deploy() {
    const [owner, alice, bob] = await ethers.getSigners();
    const NFT = await ethers.getContractFactory("MarketNFT");
    const nft = await NFT.deploy(ethers.parseEther("0.01"), 1000);
    const Market = await ethers.getContractFactory("SimpleMarket");
    const market = await Market.deploy();
    return { owner, alice, bob, nft, market };
  }

  it("mints, lists, buys, and transfers ownership", async () => {
    const { alice, bob, nft, market } = await deploy();
    await nft.connect(alice).mint("ipfs://x", { value: ethers.parseEther("0.01") });
    await nft.connect(alice).approve(await market.getAddress(), 1);
    await market.connect(alice).createListing(await nft.getAddress(), 1, ethers.parseEther("0.1"));
    await expect(market.connect(bob).buy(0, { value: ethers.parseEther("0.1") }))
      .to.emit(market, "Bought");
    expect(await nft.ownerOf(1)).to.equal(bob.address);
  });

  it("reverts on underpay or missing approval", async () => {
    const { alice, bob, nft, market } = await deploy();
    await nft.connect(alice).mint("ipfs://x", { value: ethers.parseEther("0.01") });
    await expect(market.connect(alice).createListing(await nft.getAddress(), 1, 1n)).to.be.reverted; // no approval
    await nft.connect(alice).approve(await market.getAddress(), 1);
    await market.connect(alice).createListing(await nft.getAddress(), 1, 1000n);
    await expect(market.connect(bob).buy(0, { value: 10n })).to.be.revertedWith("underpay");
  });

  it("only seller can cancel; pending balances update", async () => {
    const { owner, alice, bob, nft, market } = await deploy();
    await nft.connect(alice).mint("ipfs://x", { value: ethers.parseEther("0.01") });
    await nft.connect(alice).approve(await market.getAddress(), 1);
    await market.connect(alice).createListing(await nft.getAddress(), 1, ethers.parseEther("1"));
    await expect(market.connect(bob).cancel(0)).to.be.revertedWith("not seller");
    await market.connect(alice).cancel(0);
    expect(await nft.ownerOf(1)).to.equal(alice.address);

    // relist and buy to test pending
    await market.connect(alice).createListing(await nft.getAddress(), 1, ethers.parseEther("1"));
    await market.connect(bob).buy(1, { value: ethers.parseEther("1") });
    const fee = (ethers.parseEther("1") * 250n) / 10_000n;
    expect(await market.pending(owner.address)).to.equal(fee);
    expect(await market.pending(alice.address)).to.equal(ethers.parseEther("1") - fee);
  });
});
```
2) Jalankan: `npx hardhat test`.

## Exercises / Mini Project
- Tambah test double-buy (listing sudah tidak aktif) dan ensure revert.

## Quiz
- Q1: Mengapa saldo pending penting diuji?
- Q2: Bagaimana memastikan event ListingCreated berisi ID benar?
- Q3: Kasus gagal apa paling krusial untuk marketplace?

## Skill Checklist
- [ ] Alur mint→list→buy→cancel teruji.
- [ ] Revert case (underpay, non-seller) tertangani.
- [ ] Fee/pending diverifikasi.

---

<p align="center">
  <a href="./053-proyek2-marketplace-kontrak.md">⬅️ Previous</a> |
  <a href="./055-proyek2-frontend.md">Next ➡️</a>
</p>
