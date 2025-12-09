<p align="center">
  <a href="./099-zk-circom-snarkjs.md">⬅️ Previous</a> |
  <a href="./101-formal-verification.md">Next ➡️</a>
</p>

---

# Mini ZK Rollup (Konsep & Proof-of-Concept)

## Learning Objectives
- Memahami komponen rollup: sequencer, prover, verifier.
- Membangun PoC sederhana (batch transfer + proof verifikasi on-chain).
- Menilai batasan PoC.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Rollup: kumpulkan tx off-chain, buat proof state transition, verifikasi di kontrak (verifier). Data availability minimal untuk PoC: simpan commitment di chain, bukan seluruh data.

## Hands-on Practice
1) Definisikan state off-chain sederhana: mapping address→balance (JSON).
2) Buat sirkuit Circom (contoh batch 5 transfer) yang memastikan:
   - saldo tidak negatif,
   - sum input = sum output,
   - root merkle sebelum/sesudah sesuai (opsional).
3) Generate proof dengan snarkjs (lihat modul 099).
4) Deploy kontrak `Verifier.sol` (dari snarkjs) + `RollupPoC.sol` yang:
```solidity
function submitBatch(bytes memory proof, uint256[1] memory pub) external {
    require(verifier.verifyProof(proof, pub), "bad proof");
    stateRoot = pub[0]; // contoh: commitment state baru
}
```
5) Hardhat test: kirim proof valid → stateRoot berubah; proof salah → revert.

## Exercises / Mini Project
- Ukur gas verify proof di Hardhat test dan catat.

## Quiz
- Q1: Peran prover dalam rollup?
- Q2: Apa yang disimpan on-chain di PoC ini?
- Q3: Mengapa DA penting pada rollup produksi?

## Skill Checklist
- [ ] Paham arsitektur rollup.
- [ ] Punya PoC verify proof on-chain.
- [ ] Mengetahui biaya verify proof.

---

<p align="center">
  <a href="./099-zk-circom-snarkjs.md">⬅️ Previous</a> |
  <a href="./101-formal-verification.md">Next ➡️</a>
</p>
