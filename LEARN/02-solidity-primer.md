# 02. Dasar Solidity

## Konsep
- Tipe: uint256, address, bool, string, array, mapping.
- Visibilitas: public/external/internal/private.
- State mutability: view, pure, payable.
- Event & indexed parameter.
- Error handling: require/revert/assert; custom error lebih hemat gas.

## Langkah Praktik
1) Buat ulang kontrak sederhana `contracts/Storage.sol` bila hilang:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.28;

contract Storage {
    uint256 public number;

    event NumberUpdated(uint256 indexed previous, uint256 indexed current, address indexed caller);

    function setNumber(uint256 _num) external {
        require(_num <= 1_000_000, "Too big");
        uint256 prev = number;
        number = _num;
        emit NumberUpdated(prev, _num, msg.sender);
    }
}
```
2) Kompilasi: `npx hardhat compile`.
3) Catat arti error/peringatan yang muncul.

## Selesai Ketika
Kontrak ter-compile tanpa error dan kamu bisa menjelaskan kenapa event berguna.

---
<p align="center">
  <a href="01-evm-basics.md">⬅️ Previous</a> |
  <a href="03-hardhat-runner.md">Next ➡️</a>
</p>
