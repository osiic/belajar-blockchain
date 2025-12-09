<p align="center">
  <a href="./049-proyek1-erc20-analytics.md">⬅️ Previous</a> |
  <a href="./051-proyek2-nft-planning.md">Next ➡️</a>
</p>

---

# Milestone 1 Review

## Learning Objectives
- Mengevaluasi fase ERC20 dashboard.
- Mengidentifikasi gap test/UX/keamanan.
- Menyusun rencana peningkatan.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Fokus review: coverage test, cap & akses kontrol, UX transfer/approve/mint-burn, performa RPC, dokumentasi alamat/ABI. Gunakan checklist untuk menyimpulkan siap/tidak lanjut.

## Hands-on Practice
1) Jalankan ulang `npx hardhat test` (cek gas jika pakai gas-reporter). Catat coverage/gas.
2) Uji manual dashboard: transfer, approve+transferFrom, mint/burn (owner), notifikasi & explorer link.
3) Audit cepat: cap terjaga, onlyOwner di mint/burn, event lengkap, input validasi (jumlah>0).
4) Tulis di `notes.md`: bug/UX issue + prioritas (P1 kritis, P2 nice-to-have).

## Exercises / Mini Project
- Buat backlog peningkatan 3–5 item (mis. pagination log, cache read, copy error lebih jelas) dengan target rilis berikutnya.

## Quiz
- Q1: Area mana paling lemah saat ini (test, UX, security)?
- Q2: Apakah ada risiko keamanan tersisa (cap, owner leakage)?
- Q3: Perbaikan apa paling berdampak untuk rilis berikutnya?

## Skill Checklist
- [ ] Review teknis selesai.
- [ ] Backlog perbaikan dibuat.
- [ ] Capaian milestone terdokumentasi.

---

<p align="center">
  <a href="./049-proyek1-erc20-analytics.md">⬅️ Previous</a> |
  <a href="./051-proyek2-nft-planning.md">Next ➡️</a>
</p>
