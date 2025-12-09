<p align="center">
  <a href="./110-analytics-dune-flipside.md">⬅️ Previous</a> |
  <a href="./112-ux-dapp-best-practice.md">Next ➡️</a>
</p>

---


---

<p align="center">
  <a href="./110-analytics-dune-flipside.md">⬅️ Previous</a> |
  <a href="./112-ux-dapp-best-practice.md">Next ➡️</a>
</p>
# Mobile Web3 & WalletConnect

## Learning Objectives
- Menyambungkan mobile wallet ke dApp.
- Menggunakan WalletConnect v2 (wagmi/viem).
- Menguji UX mobile.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
WalletConnect membuat sesi antara dApp dan wallet mobile. Perlu `projectId`, daftar chain, dan connector di wagmi. UX mobile: perhatikan ruang layar, keyboard, dan deep link fallback.

## Hands-on Practice
1) Instal paket:
```bash
npm install @walletconnect/ethereum-provider
```
(wagmi v1 sudah menyertakan konektor WalletConnect)
2) Tambah konektor di wagmi config:
```ts
import { walletConnectProvider } from '@web3modal/ethereum';
// atau wagmi connector WalletConnectConnector dengan projectId
```
3) Uji koneksi dengan wallet mobile (scan QR) di testnet.

## Exercises / Mini Project
- Buat panduan cepat mobile (README section) berisi cara connect, switch network, dan tanda tangan tx.

## Quiz
- Q1: Apa fungsi projectId?
- Q2: Bagaimana menguji di perangkat nyata?
- Q3: Masalah UX mobile umum apa?

## Skill Checklist
- [ ] WalletConnect terpasang.
- [ ] Bisa connect dari mobile ke dApp.
- [ ] Panduan mobile ditulis.
