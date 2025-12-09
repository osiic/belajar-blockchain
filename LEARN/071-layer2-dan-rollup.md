<p align="center">
  <a href="./070-rpc-provider-dan-rate-limit.md">⬅️ Previous</a> |
  <a href="./072-bridge-dan-asset-transfer.md">Next ➡️</a>
</p>

---

# Layer 2 & Rollup

## Learning Objectives
- Memahami perbedaan optimistic vs zk rollup.
- Menilai kapan deploy ke L2.
- Membandingkan biaya/gas dan finality.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Optimistic: asumsi benar, ada fraud-proof window; finality tertunda. zk: proof validitas, finality cepat, proof mahal off-chain. Gas L2 lebih murah; beberapa opcodes/gas berbeda.

## Hands-on Practice
1) Tambah config L2 (Optimism/Arbitrum testnet) di `hardhat.config.ts`.
2) Deploy kontrak sederhana:
```bash
npx hardhat run scripts/deploy.js --network optimismTest
```
3) Catat gas deploy vs Sepolia (lihat explorer) dan lama konfirmasi.

## Exercises / Mini Project
- Catat perubahan UX jika finality tertunda (optimistic) vs cepat (zk).

## Quiz
- Q1: Bedanya optimistic vs zk rollup?
- Q2: Mengapa gas L2 lebih murah?
- Q3: Apa dampak fraud-proof window bagi pengguna?

## Skill Checklist
- [ ] Paham konsep L2 & jenis rollup.
- [ ] Bisa deploy ke L2 testnet.
- [ ] Menilai trade-off biaya/finality.

---

<p align="center">
  <a href="./070-rpc-provider-dan-rate-limit.md">⬅️ Previous</a> |
  <a href="./072-bridge-dan-asset-transfer.md">Next ➡️</a>
</p>
