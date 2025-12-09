<p align="center">
  <a href="./100-mini-zk-rollup-dapp.md">⬅️ Previous</a> |
  <a href="./102-fuzzing-dan-property-testing.md">Next ➡️</a>
</p>

---

# Formal Verification (Konsep)

## Learning Objectives
- Memahami tujuan formal verification.
- Mengenal alat: Scribble, Certora (konsep), Echidna sebagai property checker.
- Menulis invariant sederhana.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Formal verification membuktikan properti (invariant) berlaku untuk semua eksekusi. Scribble menambah anotasi; Certora Prover memeriksa rule vs bytecode. Biaya tinggi, dipakai untuk kontrak kritikal.

## Hands-on Practice
1) Pasang Scribble (opsional):
```bash
npm install -g @eth-optimism/scribble
```
2) Tambah anotasi sederhana di kontrak (contoh saldo tidak negatif):
```solidity
/// #invariant totalSupply() >= 0;
```
3) Jalankan instrumentasi: `scribble contracts/Token.sol --output-mode files`.
4) Jalankan test di versi terinstrumentasi untuk cek invariant.

## Exercises / Mini Project
- Tulis 2 invariant untuk kontrak Subscription (mis. expiry >= block.timestamp saat subscribed; price > 0).

## Quiz
- Q1: Apa itu invariant?
- Q2: Mengapa formal verification mahal?
- Q3: Alat apa untuk anotasi spesifikasi?

## Skill Checklist
- [ ] Paham tujuan formal verification.
- [ ] Bisa menulis anotasi sederhana.
- [ ] Mengetahui alat utama.

---

<p align="center">
  <a href="./100-mini-zk-rollup-dapp.md">⬅️ Previous</a> |
  <a href="./102-fuzzing-dan-property-testing.md">Next ➡️</a>
</p>
