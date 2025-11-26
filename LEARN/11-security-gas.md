# 11. Keamanan & Efisiensi Gas

## Konsep
- Pola aman: Checks-Effects-Interactions, pull payment, gunakan `nonReentrant` bila perlu.
- Validasi input: gunakan custom error (`error ExceedsLimit();`) untuk hemat gas.
- Gas tips: packing storage, hindari loop tak terbatas, gunakan `immutable` untuk konstanta runtime.

## Langkah Praktik
1) Tambah custom error di `Subscription.sol` untuk kondisi gagal (mis. `error NotOwner();`).
2) Terapkan modifier `onlyOwner` dengan custom error, bukan string.
3) Tambah test untuk memastikan revert memakai custom error (Chai matcher `.to.be.revertedWithCustomError`).
4) (Opsional) Pasang gas reporter:
```bash
npm install --save-dev hardhat-gas-reporter
```
Tambah di config dan jalankan `npx hardhat test` untuk lihat biaya.

## Selesai Ketika
Kontrak punya guard aman, test custom error lulus, dan kamu tahu titik gas termahal.

---
<p align="center">
  <a href="10-deployment.md">⬅️ Previous</a> |
  <a href="12-extensions.md">Next ➡️</a>
</p>
