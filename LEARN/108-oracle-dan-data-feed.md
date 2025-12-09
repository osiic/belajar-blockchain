<p align="center">
  <a href="./107-decentralized-storage.md">⬅️ Previous</a> |
  <a href="./109-automation-keepers.md">Next ➡️</a>
</p>

---

# Oracle & Data Feed

## Learning Objectives
- Memahami kebutuhan oracle.
- Menggunakan Chainlink/Data Feed.
- Menangani risiko oracle.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Kontrak butuh data off-chain (harga, randomness). Chainlink menyediakan feed terdesentralisasi. Risiko: manipulasi harga, staleness. Validasi timestamp & decimals.

## Hands-on Practice
1) Baca feed harga ETH/USD (Sepolia):
```solidity
interface AggregatorV3Interface {
  function latestRoundData() external view returns (uint80,int256,uint256,uint256,uint80);
  function decimals() external view returns (uint8);
}
```
2) Tambah fungsi di kontrak untuk membaca feed dan revert jika data stale (> X detik).
3) Jalankan di script testnet dan log harga.

## Exercises / Mini Project
- Tambah fallback: jika feed tidak tersedia, revert dengan pesan jelas atau gunakan feed cadangan (opsional).

## Quiz
- Q1: Mengapa on-chain data butuh oracle?
- Q2: Risiko oracle apa?
- Q3: Bagaimana cek staleness?

## Skill Checklist
- [ ] Paham konsep oracle.
- [ ] Bisa baca feed harga.
- [ ] Memperhitungkan risiko staleness/manipulasi.

---

<p align="center">
  <a href="./107-decentralized-storage.md">⬅️ Previous</a> |
  <a href="./109-automation-keepers.md">Next ➡️</a>
</p>
