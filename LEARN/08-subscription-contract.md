# 08. Proyek Inti: Kontrak Langganan

## Tujuan
Membangun kontrak langganan berbayar ERC20 (project akhir on-chain backend).

## Fitur Minimal
- Admin set harga per periode (dalam LRN).
- Pengguna subscribe/unsubscribe.
- Simpan waktu kedaluwarsa per alamat.
- Event: `Subscribed(address user, uint256 expiry)`; `Cancelled(address user)`; `PriceUpdated(uint256 price)`.

## Langkah Praktik
1) Buat `contracts/Subscription.sol` menggunakan `LearnToken` sebagai token bayar.
2) Logika utama:
   - `subscribe(uint256 months)`: tarik token via `transferFrom`, perbarui expiry `max(now, expiry)+months*30days`.
   - `cancel()`: set expiry ke blok saat ini (atau hapus) dan emit event.
   - `setPrice(uint256 newPrice)`: onlyOwner.
3) Tambah modifier `onlyOwner` (bisa pakai OZ `Ownable`).
4) Tambah test `test/subscription.ts`:
   - Happy path subscribe, perpanjang sebelum habis, unsubscribe.
   - Revert jika allowance tidak cukup.
   - Hanya owner boleh ubah harga.
5) Pastikan event ter-emit dengan argumen benar.

## Selesai Ketika
Semua test subscription hijau dan kontrak siap dipakai frontend.

---
<p align="center">
  <a href="07-erc721.md">⬅️ Previous</a> |
  <a href="09-frontend-dapp.md">Next ➡️</a>
</p>
