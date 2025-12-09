<p align="center">
  <a href="./063-proyek4-crowdfunding-planning.md">⬅️ Previous</a> |
  <a href="./065-proyek4-crowdfunding-testing.md">Next ➡️</a>
</p>

---

# Proyek 4: Kontrak Crowdfunding

## Learning Objectives
- Membuat kontrak kampanye multi-instance.
- Menangani kontribusi, klaim, dan refund dengan aman.
- Mengeluarkan event penting untuk monitoring.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Mapping id→Campaign; kontribusi menambah pledged per kampanye. Klaim hanya owner jika goal tercapai setelah deadline dan belum diklaim. Refund untuk kontributor jika gagal. Gunakan pull pattern untuk dana agar aman dari reentrancy.

## Hands-on Practice
1) Buat `contracts/Crowdfund.sol`:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.28;
import "@openzeppelin/contracts/security/ReentrancyGuard.sol";

contract Crowdfund is ReentrancyGuard {
    struct Campaign {
        address owner;
        uint256 goal;
        uint256 pledged;
        uint64 start;
        uint64 end;
        bool claimed;
        bool cancelled;
    }
    Campaign[] public campaigns;
    mapping(uint256 => mapping(address => uint256)) public contributions;

    event CampaignCreated(uint256 id, address owner, uint256 goal, uint64 end);
    event Contributed(uint256 id, address contributor, uint256 amount);
    event Claimed(uint256 id, uint256 amount);
    event Refunded(uint256 id, address contributor, uint256 amount);
    event Cancelled(uint256 id);

    function create(uint256 goal, uint64 duration) external returns (uint256) {
        require(goal > 0, "goal 0");
        uint64 end = uint64(block.timestamp + duration);
        campaigns.push(Campaign(msg.sender, goal, 0, uint64(block.timestamp), end, false, false));
        emit CampaignCreated(campaigns.length - 1, msg.sender, goal, end);
        return campaigns.length - 1;
    }

    function contribute(uint256 id) external payable {
        Campaign storage c = campaigns[id];
        require(!c.cancelled, "cancelled");
        require(block.timestamp < c.end, "ended");
        c.pledged += msg.value;
        contributions[id][msg.sender] += msg.value;
        emit Contributed(id, msg.sender, msg.value);
    }

    function cancel(uint256 id) external {
        Campaign storage c = campaigns[id];
        require(msg.sender == c.owner, "not owner");
        require(block.timestamp < c.end, "ended");
        c.cancelled = true;
        emit Cancelled(id);
    }

    function claim(uint256 id) external nonReentrant {
        Campaign storage c = campaigns[id];
        require(msg.sender == c.owner, "not owner");
        require(!c.cancelled, "cancelled");
        require(block.timestamp >= c.end, "not ended");
        require(c.pledged >= c.goal, "goal not met");
        require(!c.claimed, "claimed");
        c.claimed = true;
        (bool ok, ) = c.owner.call{value: c.pledged}("");
        require(ok, "transfer fail");
        emit Claimed(id, c.pledged);
    }

    function refund(uint256 id) external nonReentrant {
        Campaign storage c = campaigns[id];
        require(block.timestamp >= c.end || c.cancelled, "not ended");
        require(c.pledged < c.goal, "goal met");
        uint256 bal = contributions[id][msg.sender];
        require(bal > 0, "nothing");
        contributions[id][msg.sender] = 0;
        (bool ok, ) = msg.sender.call{value: bal}("");
        require(ok, "refund fail");
        emit Refunded(id, msg.sender, bal);
    }
}
```
2) Compile: `npx hardhat compile`.

## Exercises / Mini Project
- Tambah opsi ERC20 payment (overload `contributeERC20` dengan IERC20 dan allowance).

## Quiz
- Q1: Mengapa memakai pull pattern untuk claim/refund?
*- Q2: Bagaimana memvalidasi deadline kampanye?*
- Q3: Siapa saja yang boleh claim?

## Skill Checklist
- [ ] create/contribute/claim/refund berfungsi.
- [ ] Event tercatat.
- [ ] Guard goal/deadline aman.

---

<p align="center">
  <a href="./063-proyek4-crowdfunding-planning.md">⬅️ Previous</a> |
  <a href="./065-proyek4-crowdfunding-testing.md">Next ➡️</a>
</p>
