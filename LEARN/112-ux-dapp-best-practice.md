<p align="center">
  <a href="./111-mobile-web3-walletconnect.md">⬅️ Previous</a> |
  <a href="./113-i18n-l10n-dapp.md">Next ➡️</a>
</p>

---

# UX Terbaik untuk dApp

## Learning Objectives
- Mendesain alur transaksi jelas.
- Mengurangi kegagalan dengan preflight checks.
- Menyajikan status & biaya gas dengan ramah.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
UX dApp baik: cek jaringan, saldo, allowance sebelum submit; tampilkan estimasi biaya, status pending/sukses/gagal; error copy ramah. Network guard penting untuk multi-chain.

## Hands-on Practice
1) Tambah preflight di tombol aksi (mis. subscribe):
   - cek `chainId`, `balance`, `allowance`.
   - jika kurang, arahkan user (switch chain, approve dulu).
2) Tampilkan estimasi biaya: `gas * maxFeePerGas` → konversi ETH/USD (optional feed).
3) Tambah komponen Network Guard: bila chain mismatch, prompt switch.

## Exercises / Mini Project
- Buat komponen toast standar dengan status pending/sukses/gagal + link explorer.

## Quiz
- Q1: Mengapa preflight penting?
- Q2: Info apa harus ditampilkan sebelum tx?
- Q3: Bagaimana menangani chain mismatch?

## Skill Checklist
- [ ] Preflight diterapkan.
- [ ] UX menampilkan biaya/status.
- [ ] Network guard tersedia.

---

<p align="center">
  <a href="./111-mobile-web3-walletconnect.md">⬅️ Previous</a> |
  <a href="./113-i18n-l10n-dapp.md">Next ➡️</a>
</p>
