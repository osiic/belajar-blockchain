<p align="center">
  <a href="./059-proyek3-voting-contract.md">⬅️ Previous</a> |
  <a href="./061-proyek3-testing.md">Next ➡️</a>
</p>

---

# Proyek 3: Frontend DAO

## Learning Objectives
- Menampilkan daftar proposal beserta status & hasil.
- Membuat proposal baru, vote, dan finalize.
- Memastikan delegasi voting power jelas di UI.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Gunakan wagmi/viem: `useReadContract` untuk `proposals(id)`, `useWriteContract` untuk `createProposal`, `vote`, `finalize`. Periksa delegasi: `delegate` GovToken harus dilakukan agar voting power > 0.

## Hands-on Practice
1) Halaman `/dao`:
   - Section delegasi: tombol `Delegate to self` memanggil `govToken.delegate(address)`.
   - Daftar proposal: loop id kecil, tampilkan desc, yes/no, end time, status (ongoing/finalized).
   - Tombol Vote Yes/No (writeContract vote).
   - Tombol Finalize jika waktu lewat.
2) Form Create Proposal: input deskripsi wajib, kirim ke `createProposal`.
3) Notifikasi: gunakan toast untuk hash pending/sukses/gagal; link ke explorer.

## Exercises / Mini Project
- Tambah filter proposal aktif vs selesai, dan sorting terbaru dulu.

## Quiz
- Q1: Mengapa delegasi diperlukan sebelum voting?
- Q2: Data apa wajib ada di kartu proposal?
- Q3: Bagaimana menandai proposal kedaluwarsa di UI?

## Skill Checklist
- [ ] Delegasi di UI jelas.
- [ ] Proposal list + vote + finalize berjalan.
- [ ] Notifikasi/status tx tampil.

---

<p align="center">
  <a href="./059-proyek3-voting-contract.md">⬅️ Previous</a> |
  <a href="./061-proyek3-testing.md">Next ➡️</a>
</p>
