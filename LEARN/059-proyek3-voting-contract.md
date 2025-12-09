<p align="center">
  <a href="./058-proyek3-governance-token.md">⬅️ Previous</a> |
  <a href="./060-proyek3-frontend.md">Next ➡️</a>
</p>

---

# Proyek 3: Voting Contract

## Learning Objectives
- Membuat kontrak proposal & voting memakai GovToken (ERC20Votes).
- Menetapkan quorum, threshold, snapshot, dan durasi voting.
- Mencatat event dan finalisasi hasil.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Voting power diambil dari `getPastVotes(voter, snapshotBlock)`. Proposal memiliki start/end, quorum (% total supply), dan threshold pembuat proposal. Eksekusi disederhanakan: hanya menyimpan keputusan (tanpa call arbitrer) untuk menjaga keamanan pemula.

## Hands-on Practice
1) Buat `contracts/SimpleDAO.sol`:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.28;
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Votes.sol";

contract SimpleDAO is Ownable {
    struct Proposal {
        address proposer;
        string description;
        uint256 yes;
        uint256 no;
        uint64 start;
        uint64 end;
        uint256 snapshotBlock;
        bool finalized;
        bool passed;
    }
    Proposal[] public proposals;
    ERC20Votes public gov;
    uint256 public quorumBps = 1000; // 10%
    uint256 public thresholdBps = 100; // 1%
    uint64 public votingPeriod = 3 days;

    event ProposalCreated(uint256 id, address proposer, string description);
    event Voted(uint256 id, address voter, bool support, uint256 weight);
    event Finalized(uint256 id, bool passed);

    constructor(address govToken) { gov = ERC20Votes(govToken); }

    function createProposal(string memory desc) external {
        uint256 supply = gov.getPastTotalSupply(block.number - 1);
        require(gov.getPastVotes(msg.sender, block.number - 1) * 10_000 / supply >= thresholdBps, "below threshold");
        proposals.push(Proposal({
            proposer: msg.sender,
            description: desc,
            yes: 0,
            no: 0,
            start: uint64(block.timestamp),
            end: uint64(block.timestamp + votingPeriod),
            snapshotBlock: block.number - 1,
            finalized: false,
            passed: false
        }));
        emit ProposalCreated(proposals.length - 1, msg.sender, desc);
    }

    function vote(uint256 id, bool support) external {
        Proposal storage p = proposals[id];
        require(block.timestamp <= p.end, "ended");
        uint256 weight = gov.getPastVotes(msg.sender, p.snapshotBlock);
        require(weight > 0, "no power");
        // Simple one-vote-per-address: weight counted once (no double vote check here; bisa ditambah mapping)
        if (support) p.yes += weight; else p.no += weight;
        emit Voted(id, msg.sender, support, weight);
    }

    function finalize(uint256 id) external {
        Proposal storage p = proposals[id];
        require(block.timestamp > p.end, "ongoing");
        require(!p.finalized, "done");
        uint256 supply = gov.getPastTotalSupply(p.snapshotBlock);
        uint256 quorum = (p.yes + p.no) * 10_000 / supply;
        p.passed = (quorum >= quorumBps) && (p.yes > p.no);
        p.finalized = true;
        emit Finalized(id, p.passed);
    }
}
```
2) Tambah cek double-vote dengan mapping (opsional) jika ingin lebih aman.
3) Compile: `npx hardhat compile`.

## Exercises / Mini Project
- Tambah opsi abstain dan simpan alasan singkat; pastikan tidak dihitung ke quorum.

## Quiz
- Q1: Mengapa memakai getPastVotes, bukan balance langsung?
- Q2: Apa syarat quorum pada finalize?
- Q3: Bagaimana mencegah double vote?

## Skill Checklist
- [ ] Proposal dapat dibuat sesuai threshold.
- [ ] Voting memakai snapshot & quorum.
- [ ] Finalisasi mencatat hasil dan event.

---

<p align="center">
  <a href="./058-proyek3-governance-token.md">⬅️ Previous</a> |
  <a href="./060-proyek3-frontend.md">Next ➡️</a>
</p>
