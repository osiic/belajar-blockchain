# 1. Fondasi & Setup

## Tujuan
Punya gambaran stack dan memastikan alat siap.

## Konsep Kunci
- EVM: mesin status deterministik; eksekusi bytecode; gas mencegah loop tak hingga.
- Akun: EOA (pakai private key) vs akun kontrak (punya kode + storage).
- Transaksi: pesan bertanda tangan yang bisa kirim ETH / memicu kode.
- Jaringan: Hardhat lokal, testnet (Sepolia/Holesky), mainnet.

## Coba
1) Cek lingkungan:
```bash
node -v
npm -v
npx hardhat --version
```
2) Baca kontrak sekarang: `contracts/Storage.sol`.
3) Gambar alur data: user -> frontend -> panggil kontrak -> state berubah.

## Selesai ketika
Kamu bisa jelaskan beda EOA vs kontrak dan `npx hardhat --version` jalan tanpa error.
