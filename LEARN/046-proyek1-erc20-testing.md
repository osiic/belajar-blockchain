<p align="center">
  <a href="./045-proyek1-erc20-kontrak.md">⬅️ Previous</a> |
  <a href="./047-proyek1-erc20-deploy.md">Next ➡️</a>
</p>

---

# Proyek 1: Testing ERC20

## Learning Objectives
- Menulis test lengkap untuk fungsi inti, admin ops, dan cap.
- Menguji revert scenarios dan event.
- Menghasilkan laporan gas (opsional).

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Tes wajib mencakup: totalSupply awal, transfer sukses, transfer gagal saldo kurang, approve+transferFrom, mint/burn akses kontrol, cap terjaga, event Transfer/Approval.

## Hands-on Practice
1) Buat `test/erc20.dashboard.ts`:
```ts
import { expect } from "chai";
import { ethers } from "hardhat";

describe("LearnToken", () => {
  async function deploy() {
    const [owner, alice, bob] = await ethers.getSigners();
    const Token = await ethers.getContractFactory("LearnToken");
    const token = await Token.deploy(ethers.parseUnits("1000000"), ethers.parseUnits("2000000"));
    return { token, owner, alice, bob };
  }

  it("sets initial supply to owner", async () => {
    const { token, owner } = await deploy();
    expect(await token.balanceOf(owner.address)).to.equal(await token.totalSupply());
  });

  it("transfers and emits event", async () => {
    const { token, owner, alice } = await deploy();
    await expect(token.transfer(alice.address, 100n))
      .to.emit(token, "Transfer")
      .withArgs(owner.address, alice.address, 100n);
  });

  it("reverts on insufficient balance", async () => {
    const { token, alice } = await deploy();
    await expect(token.connect(alice).transfer(ethers.ZeroAddress, 1n)).to.be.revertedWith("ERC20: transfer amount exceeds balance");
  });

  it("approves and transferFrom works", async () => {
    const { token, owner, alice, bob } = await deploy();
    await token.approve(alice.address, 50n);
    await token.connect(alice).transferFrom(owner.address, bob.address, 50n);
    expect(await token.balanceOf(bob.address)).to.equal(50n);
  });

  it("only owner can mint within cap", async () => {
    const { token, owner, alice } = await deploy();
    await expect(token.mint(owner.address, ethers.parseUnits("1"))).to.not.be.reverted;
    await expect(token.connect(alice).mint(alice.address, 1n)).to.be.revertedWithCustomError(token, "OwnableUnauthorizedAccount");
  });

  it("enforces cap", async () => {
    const { token } = await deploy();
    const cap = await token.cap();
    await expect(token.mint(await token.getAddress(), cap)).to.be.revertedWith("cap exceeded");
  });
});
```
2) Jalankan test & gas (jika pakai gas-reporter): `npx hardhat test`.

## Exercises / Mini Project
- Tambah test burn: saldo berkurang, totalSupply turun, dan burn tanpa saldo harus revert.

## Quiz
- Q1: Mengapa wajib uji revert untuk cap?
- Q2: Bagaimana memverifikasi event Approval?
- Q3: Kapan memakai fixture untuk percepat test?

## Skill Checklist
- [ ] Test mencakup happy & revert path.
- [ ] Event dicek.
- [ ] Cap dan akses kontrol teruji.

---

<p align="center">
  <a href="./045-proyek1-erc20-kontrak.md">⬅️ Previous</a> |
  <a href="./047-proyek1-erc20-deploy.md">Next ➡️</a>
</p>
