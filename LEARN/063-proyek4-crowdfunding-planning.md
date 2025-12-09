<p align="center">
  <a href="./062-milestone3-review.md">⬅️ Previous</a> |
  <a href="./064-proyek4-crowdfunding-kontrak.md">Next ➡️</a>
</p>

---

# Proyek 4: Crowdfunding — Perencanaan

## Learning Objectives
- Menetapkan scope kampanye crowdfunding on-chain.
- Mendesain alur create → contribute → success/fail → claim/refund.
- Menentukan parameter goal, deadline, dan metode pembayaran.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Kampanye memiliki goal (ETH), deadline, total pledged, status claimed. Sukses jika pledged >= goal sebelum deadline; jika gagal, contributor dapat refund. Dana sebaiknya ditarik (pull) untuk keamanan.

## Hands-on Practice
1) Cabang: `git checkout -b feature/crowdfunding`.
2) Tetapkan parameter di `notes.md`:
   - Pembayaran: ETH saja (sederhana).
   - Goal default (mis. 5 ETH).
   - Durasi default (mis. 30 hari).
   - Fee? (mulai dari 0 untuk sederhana).
3) Rancang struct Campaign: `{ owner, goal, pledged, start, end, claimed, canceled }`.
4) Buat checklist fitur:
   - createCampaign(goal, duration)
   - contribute(id) payable
   - claim(id) (owner, sukses)
   - refund(id) (kontributor, gagal)
   - event Created/Contributed/Claimed/Refunded/Cancelled

## Exercises / Mini Project
- Gambar sequence diagram create → contribute → (success: claim) / (fail: refund).

## Quiz
- Q1: Kapan kampanye dinyatakan sukses?
- Q2: Siapa yang boleh claim?
- Q3: Kapan refund diperbolehkan?

## Skill Checklist
- [ ] Scope kampanye jelas.
- [ ] Goal/durasi/payment ditetapkan.
- [ ] Alur dana digambar.

---

<p align="center">
  <a href="./062-milestone3-review.md">⬅️ Previous</a> |
  <a href="./064-proyek4-crowdfunding-kontrak.md">Next ➡️</a>
</p>
