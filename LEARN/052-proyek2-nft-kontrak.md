<p align="center">
  <a href="./051-proyek2-nft-planning.md">⬅️ Previous</a> |
  <a href="./053-proyek2-marketplace-kontrak.md">Next ➡️</a>
</p>

---

# Proyek 2: Kontrak NFT

## Learning Objectives
- Mengimplementasi ERC721 mint berbayar dengan baseURI/URI per token.
- Menyimpan hasil mint untuk owner (withdraw).
- Menambahkan allowlist opsional.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Pakai OZ `ERC721URIStorage` atau `ERC721` + baseURI. Fungsi mint: cek harga, supply, optional allowlist. Simpan hasil ke owner; gunakan `pull payment` atau langsung ke owner (lebih aman pakai withdraw).

## Hands-on Practice
1) Buat `contracts/MarketNFT.sol`:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.28;
import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract MarketNFT is ERC721URIStorage, Ownable {
    uint256 public mintPrice;
    uint256 public maxSupply;
    uint256 private _nextId = 1;
    mapping(address => bool) public allowlist;
    bool public allowlistOnly;

    constructor(uint256 _price, uint256 _max) ERC721("Market NFT", "MNFT") {
        mintPrice = _price;
        maxSupply = _max;
    }

    function setAllowlist(address user, bool ok) external onlyOwner { allowlist[user] = ok; }
    function setAllowlistOnly(bool v) external onlyOwner { allowlistOnly = v; }

    function mint(string memory uri) external payable returns (uint256) {
        if (allowlistOnly && !allowlist[msg.sender]) revert("not allowlisted");
        require(msg.value >= mintPrice, "fee");
        require(_nextId <= maxSupply, "sold out");
        uint256 id = _nextId++;
        _safeMint(msg.sender, id);
        _setTokenURI(id, uri);
        return id;
    }

    function withdraw(address payable to) external onlyOwner {
        to.transfer(address(this).balance);
    }
}
```
2) Compile: `npx hardhat compile`.
3) Catat mintPrice/maxSupply ke `notes.md`.

## Exercises / Mini Project
- Tambah royalti (ERC2981) sederhana: set default royalty ke owner.

## Quiz
- Q1: Mengapa memakai withdraw alih-alih transfer langsung di mint?
- Q2: Bagaimana cara membatasi supply?
- Q3: Apa risiko jika allowlistOnly diaktifkan tanpa daftar?

## Skill Checklist
- [ ] Kontrak NFT mendukung mint berbayar & optional allowlist.
- [ ] Supply dan harga dicatat.
- [ ] Hasil mint bisa di-withdraw owner.

---

<p align="center">
  <a href="./051-proyek2-nft-planning.md">⬅️ Previous</a> |
  <a href="./053-proyek2-marketplace-kontrak.md">Next ➡️</a>
</p>
