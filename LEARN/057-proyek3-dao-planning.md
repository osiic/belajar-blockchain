<p align="center">
  <a href="./056-milestone2-review.md">⬅️ Previous</a> |
  <a href="./058-proyek3-governance-token.md">Next ➡️</a>
</p>

---

# Proyek 3: DAO Voting — Perencanaan

## Learning Objectives
- Menetapkan scope DAO (governance token + kontrak voting).
- Mendesain parameter proposal, quorum, durasi, eksekusi.
- Membuat blueprint alur proposal → vote → finalize.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Komponen:
- **Governance token** (ERC20Votes).
- **Voting contract** dengan proposal, quorum (% supply), voting period, snapshot block.
Eksekusi: sederhana (menyimpan keputusan/parameter) atau simulasi tanpa call arbitrer.

## Hands-on Practice
1) Cabang: `git checkout -b feature/dao`.
2) Tetapkan parameter di `notes.md`:
   - Quorum: mis. 10% total supply.
   - Voting period: mis. 3 hari (pakai timestamp atau block).
   - Proposal threshold: mis. 1% supply.
   - Eksekusi: set parameter (contoh: harga langganan) atau hanya status keputusan.
3) Draft struktur proposal: `{ proposer, description, yes, no, start, end, executed, snapshotBlock }`.
4) Gambar flow proposal → vote → finalize → (optional) execute.

## Exercises / Mini Project
- Buat 2 template proposal (ubah harga langganan; ubah fee marketplace) dengan quorum/threshold masing-masing.

## Quiz
- Q1: Apa fungsi proposal threshold?
- Q2: Mengapa perlu snapshot block?
- Q3: Kapan proposal dianggap lolos?

## Skill Checklist
- [ ] Scope DAO jelas.
- [ ] Quorum/period/threshold ditetapkan.
- [ ] Flowchart proses disiapkan.

---

<p align="center">
  <a href="./056-milestone2-review.md">⬅️ Previous</a> |
  <a href="./058-proyek3-governance-token.md">Next ➡️</a>
</p>
