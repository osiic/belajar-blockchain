<p align="center">
  <a href="./105-tokenomics-dasar.md">⬅️ Previous</a> |
  <a href="./107-decentralized-storage.md">Next ➡️</a>
</p>

---

# Governance Design Lanjut

## Learning Objectives
- Menilai model voting (1 token 1 vote vs quadratic).
- Mengatur quorum, threshold, delegation.
- Mendesain parameter governansi yang sehat.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Quadratic voting menekan dominasi whale tapi butuh identitas; proposal threshold mencegah spam; quorum dan voting period menyeimbangkan partisipasi vs kecepatan. Delegasi meningkatkan partisipasi.

## Hands-on Practice
1) Tambah `proposalThreshold` pada SimpleDAO (mis. 1% supply).
2) Simulasikan perubahan quorum (10% → 20%) di spreadsheet untuk lihat dampak lulus/tidaknya proposal.
3) Catat rationale parameter (quorum, threshold, period, delay) di `docs/GOV_PARAMS.md`.

## Exercises / Mini Project
- Rancang skema quadratic voting (konsep): biaya suara = (suara^2); jelaskan kebutuhan identitas/anti-Sybil.

## Quiz
- Q1: Keuntungan & risiko quadratic voting?
- Q2: Apa itu proposal threshold?
- Q3: Mengapa delegation penting?

## Skill Checklist
- [ ] Parameter governance terdokumentasi.
- [ ] Threshold ditambahkan di kontrak.
- [ ] Risiko whale vs partisipasi dipahami.

---

<p align="center">
  <a href="./105-tokenomics-dasar.md">⬅️ Previous</a> |
  <a href="./107-decentralized-storage.md">Next ➡️</a>
</p>
