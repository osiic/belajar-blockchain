<p align="center">
  <a href="./095-smart-wallet-erc4337.md">⬅️ Previous</a> |
  <a href="./097-cross-chain-messaging.md">Next ➡️</a>
</p>

---

# Intent-based Architecture

## Learning Objectives
- Memahami konsep intent & solver.
- Menilai perbedaan intent vs transaksi langsung.
- Mengetahui implikasi UX dan keamanan.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Intent: user mendeklarasikan hasil, solver mengeksekusi terbaik (mis. CoW Swap). Risiko: pemilihan solver, MEV, kepercayaan harga. Kelebihan: UX lebih simpel, batching optimasi.

## Hands-on Practice
1) Pelajari flow CoW Swap RFQ (intent → solver → settlement).
2) Tulis contoh intent: “tukar 1 LRN ke ETH minimal X” di `notes.md`.
3) Identifikasi risiko: front-running solver, kegagalan harga; catat mitigasi (deadline, minReturn).

## Exercises / Mini Project
- Rancang skema scoring solver (biaya, slippage, kecepatan) secara konsep.

## Quiz
- Q1: Apa itu intent?
- Q2: Mengapa solver penting?
- Q3: Risiko utama model intent?

## Skill Checklist
- [ ] Paham intent vs tx langsung.
- [ ] Mengetahui contoh produk intent.
- [ ] Menyadari risiko/insentif solver.

---

<p align="center">
  <a href="./095-smart-wallet-erc4337.md">⬅️ Previous</a> |
  <a href="./097-cross-chain-messaging.md">Next ➡️</a>
</p>
