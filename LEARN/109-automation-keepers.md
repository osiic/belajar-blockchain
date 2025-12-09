<p align="center">
  <a href="./108-oracle-dan-data-feed.md">⬅️ Previous</a> |
  <a href="./110-analytics-dune-flipside.md">Next ➡️</a>
</p>

---


---

<p align="center">
  <a href="./108-oracle-dan-data-feed.md">⬅️ Previous</a> |
  <a href="./110-analytics-dune-flipside.md">Next ➡️</a>
</p>
# Automation & Keepers

## Learning Objectives
- Memahami job terjadwal on-chain/off-chain.
- Menggunakan Chainlink Automation/Gelato.
- Mendesain fungsi “upkeep”.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Keeper memicu fungsi berdasarkan kondisi. Fungsi upkeep harus idempotent dan ringan. Chainlink Automation memakai `checkUpkeep`/`performUpkeep`; Gelato menyediakan task serupa.

## Hands-on Practice
1) Identifikasi fungsi otomatis (mis. perpanjang langganan kadaluwarsa).
2) Tambah fungsi di kontrak:
```solidity
function checkUpkeep(bytes calldata) external view returns (bool upkeepNeeded, bytes memory) {
    upkeepNeeded = block.timestamp > expiry && price > 0;
}
function performUpkeep(bytes calldata) external {
    require(block.timestamp > expiry, "no need");
    // lakukan aksi, pastikan idempotent
}
```
3) Daftarkan job di testnet (Chainlink) atau simulasi panggilan berkala via script cron.

## Exercises / Mini Project
- Tambah rate limiter untuk upkeep (mis. hanya boleh dipanggil setiap X detik).

## Quiz
- Q1: Apa syarat fungsi upkeep?
- Q2: Mengapa idempotent penting?
- Q3: Alternatif selain Chainlink?

## Skill Checklist
- [ ] Tahu konsep keeper.
- [ ] Fungsi upkeep dirancang.
- [ ] Jadwal otomatis disiapkan/simulasi.
