<p align="center">
  <a href="./057-proyek3-dao-planning.md">⬅️ Previous</a> |
  <a href="./059-proyek3-voting-contract.md">Next ➡️</a>
</p>

---

# Proyek 3: Governance Token

## Learning Objectives
- Membuat token ERC20 dengan voting power (ERC20Votes).
- Memahami delegasi untuk voting power dan snapshot.
- Menyiapkan distribusi awal.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
OZ `ERC20Votes` menambah checkpoint untuk voting. Delegasi diperlukan agar saldo dihitung sebagai voting power. `ERC20Permit` (EIP-2612) memungkinkan delegasi via signature.

## Hands-on Practice
1) Buat `contracts/GovToken.sol`:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.28;
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Votes.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract GovToken is ERC20Votes, Ownable {
    constructor() ERC20("GovToken", "GOV") ERC20Permit("GovToken") {
        _mint(msg.sender, 1_000_000e18);
    }
    function _afterTokenTransfer(address from, address to, uint256 amount)
        internal override(ERC20, ERC20Votes) { super._afterTokenTransfer(from, to, amount); }
    function _mint(address to, uint256 amount)
        internal override(ERC20, ERC20Votes) { super._mint(to, amount); }
    function _burn(address account, uint256 amount)
        internal override(ERC20, ERC20Votes) { super._burn(account, amount); }
}
```
2) Deploy dan delegate ke diri sendiri:
```js
const gov = await ethers.deployContract("GovToken");
await gov.waitForDeployment();
await gov.delegate((await ethers.getSigners())[0].address);
```
3) Catat alamat di `deployments/<network>.json`.

## Exercises / Mini Project
- Tambah fungsi airdrop sederhana (onlyOwner) untuk beberapa alamat, lalu delegasikan ke penerima.

## Quiz
- Q1: Mengapa harus delegate sebelum voting?
- Q2: Apa manfaat snapshot voting?
- Q3: Event apa dicatat ketika delegasi berubah?

## Skill Checklist
- [ ] GovToken dibuat dan bisa delegate.
- [ ] Paham checkpoint/snapshot.
- [ ] Deploy sukses.

---

<p align="center">
  <a href="./057-proyek3-dao-planning.md">⬅️ Previous</a> |
  <a href="./059-proyek3-voting-contract.md">Next ➡️</a>
</p>
