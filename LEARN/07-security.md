# 7. Keamanan & Efisiensi Gas

## Tujuan
Memakai prinsip aman sebelum mainnet.

## Konsep Kunci
- Risiko umum: reentrancy, overflow (sudah dicek di 0.8+), salah akses kontrol, loop tak terbatas.
- Pola Checks-Effects-Interactions; lebih aman gunakan pola tarik dana (pull) daripada push.
- Tips gas: hindari pertumbuhan state tak terbatas, pack storage bila masuk akal, gunakan string revert singkat.

## Coba
1) Tambah akses kontrol sederhana ke `setNumber` (mis. hanya pemilik) dengan `address public owner;` dan `constructor() { owner = msg.sender; }`.
2) Buat modifier `onlyOwner` dan pakai di fungsi mutasi.
3) Jalankan test dan tambahkan test yang memastikan non-owner revert.
4) Jalan `npx hardhat test` dan catat gas jika mengaktifkan plugin gas reporter di masa depan.

## Selesai ketika
Kamu bisa menjelaskan bagaimana Checks-Effects-Interactions mengurangi risiko dan test non-owner revert lulus.
