<p align="center">
  <a href="./096-intent-based-architecture.md">⬅️ Previous</a> |
  <a href="./098-privacy-zk-basics.md">Next ➡️</a>
</p>

---

# Cross-Chain Messaging

## Learning Objectives
- Memahami konsep pesan lintas chain.
- Mengetahui protokol umum (LayerZero, Axelar, Wormhole).
- Menilai risiko keamanan.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Messaging mengirim payload antar chain lewat relayer + verifikasi (light client/guardian/validator set). Risiko: bridge hack, replay, konsensus lemah. Bedakan asset bridge vs messaging saja.

## Hands-on Practice
1) Baca docs LayerZero “Hello World”.
2) Diagramkan alur: app → endpoint sumber → relayer → endpoint tujuan → kontrak target.
3) Catat mitigasi replay (nonce/chainId) dan validasi pengirim.

## Exercises / Mini Project
- Rancang pesan sederhana: sinkronkan expiry langganan ke L2 (konsep).

## Quiz
- Q1: Bedanya bridge aset vs messaging?
- Q2: Risiko terbesar messaging?
- Q3: Bagaimana mencegah replay?

## Skill Checklist
- [ ] Mengerti alur messaging.
- [ ] Tahu protokol populer.
- [ ] Menyadari risiko keamanan.

---

<p align="center">
  <a href="./096-intent-based-architecture.md">⬅️ Previous</a> |
  <a href="./098-privacy-zk-basics.md">Next ➡️</a>
</p>
