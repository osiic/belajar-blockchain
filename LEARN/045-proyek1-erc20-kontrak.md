<p align="center">
  <a href="./044-proyek1-erc20-planning.md">⬅️ Previous</a> |
  <a href="./046-proyek1-erc20-testing.md">Next ➡️</a>
</p>

---

# Proyek 1: Kontrak ERC20

## Learning Objectives
- Menulis kontrak LRN berbasis OpenZeppelin dengan mint/burn optional dan cap.
- Memastikan event standar terpenuhi.
- Menyiapkan konfigurasi untuk testing & deploy.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Gunakan `ERC20` OZ; tambahkan:
- `cap` (jika perlu) untuk membatasi totalSupply.
- `mint` dan `burn` hanya untuk owner (inherit `Ownable`).
- Event standar `Transfer`/`Approval` sudah disediakan OZ; tidak perlu custom kecuali logging admin ops.

## Hands-on Practice
1) Buat/ubah `contracts/LearnToken.sol`:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.28;
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract LearnToken is ERC20, Ownable {
    uint256 public immutable cap;

    constructor(uint256 initialSupply, uint256 cap_) ERC20("Learn Token", "LRN") {
        require(initialSupply <= cap_ && cap_ > 0, "cap invalid");
        cap = cap_;
        _mint(msg.sender, initialSupply);
    }

    function mint(address to, uint256 amount) external onlyOwner {
        require(totalSupply() + amount <= cap, "cap exceeded");
        _mint(to, amount);
    }

    function burn(uint256 amount) external {
        _burn(msg.sender, amount);
    }
}
```
2) Perbarui `hardhat.config.ts` jika perlu menambahkan path/solidity version.
3) Compile: `npx hardhat compile`.

## Exercises / Mini Project
- Tambah fungsi `batchMint(address[] calldata to, uint256 amountEach)` hanya owner; pastikan cek cap sekali (amountEach * to.length).

## Quiz
- Q1: Mengapa cap diverifikasi di constructor dan mint?
- Q2: Siapa yang boleh memanggil burn di desain ini?
- Q3: Event apa yang dipicu ketika mint/burn?

## Skill Checklist
- [ ] Kontrak LRN selesai dengan cap & akses kontrol.
- [ ] Compile tanpa error.
- [ ] Siap untuk pengujian.

---

<p align="center">
  <a href="./044-proyek1-erc20-planning.md">⬅️ Previous</a> |
  <a href="./046-proyek1-erc20-testing.md">Next ➡️</a>
</p>
