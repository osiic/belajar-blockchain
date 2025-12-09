<p align="center">
  <a href="./065-proyek4-crowdfunding-testing.md">⬅️ Previous</a> |
  <a href="./067-milestone4-review.md">Next ➡️</a>
</p>

---

# Proyek 4: Frontend Crowdfunding

## Learning Objectives
- Membuat UI create campaign, kontribusi, klaim/refund.
- Menampilkan status kampanye (progress, countdown).
- Menangani transaksi dengan notifikasi jelas.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Gunakan wagmi/viem: `useReadContract` untuk campaign(id), `useWriteContract` untuk create/contribute/claim/refund. Progress = pledged/goal. Waktu tersisa: end - now; status (active/success/fail/cancelled).

## Hands-on Practice
1) Halaman `/crowdfund`:
   - Form create (goal ETH, durasi hari/detik).
   - List kampanye: loop id kecil, tampilkan owner, goal, pledged, end, status.
   - Tombol Contribute (writeContract), Claim (owner, sukses), Refund (kontributor, gagal/cancel).
2) Progress bar: `pledged/goal`; badge status; countdown waktu.
3) Notifikasi: toast untuk pending/sukses/gagal dengan link explorer.

## Exercises / Mini Project
- Filter kampanye milik user (owner) dan tampilkan tombol Cancel.

## Quiz
- Q1: Data apa diperlukan untuk progress?
- Q2: Kapan tombol Claim muncul?
- Q3: Bagaimana menampilkan waktu tersisa?

## Skill Checklist
- [ ] UI create/contribute/claim/refund berfungsi.
- [ ] Status kampanye dan countdown jelas.
- [ ] Notifikasi transaksi tampil.

---

<p align="center">
  <a href="./065-proyek4-crowdfunding-testing.md">⬅️ Previous</a> |
  <a href="./067-milestone4-review.md">Next ➡️</a>
</p>
