<p align="center">
  <a href="./078-security-predeploy-checklist.md">⬅️ Previous</a> |
  <a href="./080-audit-readiness.md">Next ➡️</a>
</p>

---

# Gas Optimasi Lanjutan

## Learning Objectives
- Menerapkan teknik lanjut: unchecked blocks, custom errors, calldata packing.
- Memahami trade-off keamanan vs gas.
- Mengukur dampak dengan benchmark.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
`unchecked` untuk loop terkontrol, custom error hemat gas dibanding string, gunakan `immutable/constant`, kurangi SSTORE, packing variabel kecil dalam slot. Selalu pastikan keamanan tidak dikorbankan.

## Hands-on Practice
1) Audit kontrak utama dan terapkan ≥2 optimasi:
   - Ganti revert string menjadi custom error.
   - Gunakan `unchecked` pada increment loop yang terkontrol.
   - Packing struct (mis. `uint64 end`, `uint64 start`, `uint128 goal`).
2) Jalankan gas reporter sebelum & sesudah: `npx hardhat test`.
3) Catat selisih gas di `notes.md`.

## Exercises / Mini Project
- Tambah benchmark sederhana (snapshot gas) untuk fungsi termahal dan bandingkan.

## Quiz
- Q1: Kapan aman memakai unchecked?
- Q2: Mengapa custom error hemat gas?
- Q3: Bagaimana packing membantu?

## Skill Checklist
- [ ] Optimasi aman diterapkan.
- [ ] Dampak gas terukur.
- [ ] Keamanan tidak dikorbankan.

---

<p align="center">
  <a href="./078-security-predeploy-checklist.md">⬅️ Previous</a> |
  <a href="./080-audit-readiness.md">Next ➡️</a>
</p>
