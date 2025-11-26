# 01. EVM & Transaksi

## Konsep
- EVM: mesin state; blok berisi transaksi; gas membatasi eksekusi.
- Akun: EOA (punya key) vs kontrak (punya kode).
- Transaksi: signed, punya nonce, gas limit, gas price/fee.
- Log/Event: dicatat di bloom filter, tidak bisa diubah.

## Langkah Praktik
1) Baca kontrak contoh `contracts/Storage.sol` (atau buat baru jika belum ada).
2) Gambar alur: User (EOA) -> RPC -> Node -> EVM -> State/storage.
3) Jalankan node lokal untuk melihat transaksi real time:
```bash
npx hardhat node
```
4) Kirim call dummy via console (terminal lain):
```bash
npx hardhat console --network localhost
> await ethers.provider.getBlockNumber();
> (await ethers.provider.getFeeData()).gasPrice;
```

## Selesai Ketika
Kamu bisa menjelaskan perbedaan call (read, tidak butuh gas) vs tx (write, butuh gas) dan melihat blok bertambah di node lokal.

---
<p align="center">
  <a href="00-roadmap.md">⬅️ Previous</a> |
  <a href="02-solidity-primer.md">Next ➡️</a>
</p>
