<p align="center">
  <a href="./079-gas-optimasi-lanjutan.md">⬅️ Previous</a> |
  <a href="./081-milestone5-review.md">Next ➡️</a>
</p>

---

# Audit Readiness

## Learning Objectives
- Menyiapkan repo untuk audit eksternal.
- Menyediakan dokumentasi arsitektur & threat model.
- Mengumpulkan bukti test/gas.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Auditor membutuhkan: spec, arsitektur, threat model, commit freeze, hasil test, dan alamat deploy. Siapkan dokumen standar agar audit efisien.

## Hands-on Practice
1) Buat `docs/ARCHITECTURE.md` (diagram alur utama, dependency kontrak).
2) Buat `docs/THREAT_MODEL.md` (aktor, aset, ancaman, mitigasi).
3) Simpan laporan test & gas (output `npx hardhat test` dan gas-reporter) di `artifacts/reports/`.
4) Bekukan branch untuk audit (tidak ada perubahan fungsional selama audit).

## Exercises / Mini Project
- Tulis daftar pertanyaan untuk auditor (klarifikasi paling berisiko).

## Quiz
- Q1: Apa yang dibutuhkan auditor sebelum mulai?
- Q2: Mengapa threat model penting?
- Q3: Kenapa perlu freeze commit saat audit?

## Skill Checklist
- [ ] Dokumentasi audit-ready tersedia.
- [ ] Threat model disusun.
- [ ] Bukti test/gas tersimpan.

---

<p align="center">
  <a href="./079-gas-optimasi-lanjutan.md">⬅️ Previous</a> |
  <a href="./081-milestone5-review.md">Next ➡️</a>
</p>
