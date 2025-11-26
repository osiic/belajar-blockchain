# 5. Deploy & Jaringan

## Tujuan
Paham konfigurasi jaringan dan kebiasaan deploy yang aman.

## Konsep Kunci
- Jaringan: `localhost`, `sepolia`, `mainnet`. Tiap jaringan butuh RPC URL + private key.
- Environment variable: simpan rahasia di `.env` (jangan commit).
- Gas & konfirmasi: estimasi dulu; tunggu konfirmasi di jaringan publik.

## Coba
1) Jika perlu, pasang dotenv:
```bash
npm install --save-dev dotenv
```
2) Tambah konfigurasi `sepolia` di `hardhat.config.ts` dengan `process.env.SEPOLIA_RPC` dan `PRIVATE_KEY` (jangan pernah commit key).
3) Update `scripts/deploy.js` untuk log nama network dan menolak jalan kalau key tidak ada.
4) Dry-run: `npx hardhat run scripts/deploy.js --network localhost` (harus tetap jalan).

## Selesai ketika
Kamu bisa jelaskan apa yang berubah antara deploy localhost dan testnet serta cara menjaga key tetap aman.
