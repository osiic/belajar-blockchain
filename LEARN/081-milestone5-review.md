<p align="center">
  <a href="./080-audit-readiness.md">⬅️ Previous</a> |
  <a href="./082-proyek5-p2e-planning.md">Next ➡️</a>
</p>

---

# Milestone 5 Review

## Learning Objectives
- Mengevaluasi kesiapan produksi (post-audit readiness).
- Merangkum gap yang tersisa (keamanan, performa, UX).
- Menetapkan langkah sebelum rilis publik.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Fokus pada stabilitas: keamanan (checklist 078–080), monitoring, dokumentasi pengguna, rencana rollback. Review hasil audit internal atau checklists, bukan fitur baru.

## Hands-on Practice
1) Jalankan lagi seluruh test + gas reporter. Pastikan CI hijau.
2) Uji end-to-end di testnet dengan akun uji baru (deploy, frontend connect, transaksi utama).
3) Review docs: README, BRIDGE, SECURITY_CHECKLIST, deploy outputs; pastikan alamat terbaru.
4) Buat rencana rollback: langkah mem-pause, cara migrasi kontrak jika bug.

## Exercises / Mini Project
- Susun daftar 5 risiko tertinggi beserta mitigasi dan owner penanggung jawab.

## Quiz
- Q1: Apakah monitoring dan alert sudah aktif?
- Q2: Langkah rollback apa tersedia jika ada bug kritis?
- Q3: Apakah semua alamat/deployment dicatat dan diverifikasi?

## Skill Checklist
- [ ] Review kesiapan rilis selesai.
- [ ] Rencana rollback terdokumentasi.
- [ ] Risiko utama dan mitigasinya tercatat.

---

<p align="center">
  <a href="./080-audit-readiness.md">⬅️ Previous</a> |
  <a href="./082-proyek5-p2e-planning.md">Next ➡️</a>
</p>
