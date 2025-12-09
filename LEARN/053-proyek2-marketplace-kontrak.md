<p align="center">
  <a href="./052-proyek2-nft-kontrak.md">⬅️ Previous</a> |
  <a href="./054-proyek2-nft-testing.md">Next ➡️</a>
</p>

---

# Proyek 2: Kontrak Marketplace Sederhana

## Learning Objectives
- Membuat kontrak listing/buy NFT dengan ETH.
- Menggunakan interface ERC721 dengan approval.
- Menangani fee marketplace secara aman (anti-reentrancy).

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Listing disimpan per ID. Beli memindahkan NFT + dana. Gunakan `ReentrancyGuard` dan pola pull (saldo pending) untuk penjual & fee agar aman dari reentrancy.

## Hands-on Practice
1) Buat `contracts/SimpleMarket.sol`:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.28;
import "@openzeppelin/contracts/security/ReentrancyGuard.sol";
import "@openzeppelin/contracts/token/ERC721/IERC721.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract SimpleMarket is ReentrancyGuard, Ownable {
    struct Listing { address seller; address nft; uint256 tokenId; uint256 price; bool active; }
    Listing[] public listings;
    mapping(address => uint256) public pending; // saldo yang bisa ditarik
    uint256 public feeBps = 250; // 2.5%

    event ListingCreated(uint256 id, address seller, address nft, uint256 tokenId, uint256 price);
    event Bought(uint256 id, address buyer);
    event Cancelled(uint256 id);

    function createListing(address nft, uint256 tokenId, uint256 price) external {
        require(price > 0, "price 0");
        IERC721(nft).transferFrom(msg.sender, address(this), tokenId); // membutuhkan approval
        listings.push(Listing(msg.sender, nft, tokenId, price, true));
        emit ListingCreated(listings.length - 1, msg.sender, nft, tokenId, price);
    }

    function buy(uint256 id) external payable nonReentrant {
        Listing storage lst = listings[id];
        require(lst.active, "inactive");
        require(msg.value >= lst.price, "underpay");
        lst.active = false;
        uint256 fee = (msg.value * feeBps) / 10_000;
        pending[owner()] += fee;
        pending[lst.seller] += msg.value - fee;
        IERC721(lst.nft).safeTransferFrom(address(this), msg.sender, lst.tokenId);
        emit Bought(id, msg.sender);
    }

    function cancel(uint256 id) external {
        Listing storage lst = listings[id];
        require(lst.active, "inactive");
        require(msg.sender == lst.seller, "not seller");
        lst.active = false;
        IERC721(lst.nft).safeTransferFrom(address(this), lst.seller, lst.tokenId);
        emit Cancelled(id);
    }

    function withdraw() external nonReentrant {
        uint256 amt = pending[msg.sender];
        require(amt > 0, "none");
        pending[msg.sender] = 0;
        (bool ok, ) = msg.sender.call{value: amt}("");
        require(ok, "transfer fail");
    }

    function setFeeBps(uint256 newFee) external onlyOwner {
        require(newFee <= 500, "fee too high"); // max 5%
        feeBps = newFee;
    }
}
```
2) Compile: `npx hardhat compile`.

## Exercises / Mini Project
- Tambah fungsi `getActiveListings()` yang mengembalikan ID aktif (atau lakukan via frontend filter).

## Quiz
- Q1: Mengapa perlu approval/transfer ke market saat listing?
- Q2: Bagaimana pending balance membantu mitigasi reentrancy?
- Q3: Risiko apa jika feeBps tanpa batas?

## Skill Checklist
- [ ] Listing/buy/cancel berjalan.
- [ ] Fee tercatat aman.
- [ ] Guard reentrancy terpasang.

---

<p align="center">
  <a href="./052-proyek2-nft-kontrak.md">⬅️ Previous</a> |
  <a href="./054-proyek2-nft-testing.md">Next ➡️</a>
</p>
