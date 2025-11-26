# 03. Hardhat Runner (v2)

## Konsep
- Runner: CLI utama (`npx hardhat <task>`).
- Konfigurasi: `hardhat.config.ts` berisi `networks`, `solidity`, plugin.
- Network bawaan: `hardhat` (in-memory), `localhost` (node yang kamu jalankan), testnet/mainnet bila ditambah.
- Artifacts: ABI + bytecode hasil kompilasi disimpan di `artifacts/`.

## Langkah Praktik
1) Lihat daftar task:
```bash
npx hardhat
```
2) Jalankan compile dan lihat output: `npx hardhat compile` lalu cek `artifacts/contracts/Storage.sol/Storage.json`.
3) Tambah komentar penjelas di `hardhat.config.ts` tentang jaringan yang tersedia.
4) Catat perbedaan `hardhat` vs `localhost` di notes.

## Selesai Ketika
Kamu tahu task-task bawaan, paham di mana ABI berada, dan konfigurasi tidak membingungkan.

---
<p align="center">
  <a href="02-solidity-primer.md">⬅️ Previous</a> |
  <a href="04-tasks-scripts.md">Next ➡️</a>
</p>
