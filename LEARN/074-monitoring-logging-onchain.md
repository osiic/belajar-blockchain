<p align="center">
  <a href="./073-konfigurasi-produksi-dan-secrets.md">⬅️ Previous</a> |
  <a href="./075-performa-caching-dan-pooling.md">Next ➡️</a>
</p>

---

# Monitoring & Logging On-chain

## Learning Objectives
- Men-subscribe event kontrak untuk pemantauan.
- Mengirim log ke sink (stdout/webhook) dan menetapkan alert dasar.
- Memilih websocket vs polling dengan tepat.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Websocket: real-time, biaya koneksi lebih tinggi; Polling: sederhana tapi lebih lambat. Catat event penting (Subscribed/Cancelled/Claimed) dan awasi tx gagal besar. Simpan log dengan timestamp & tx hash untuk audit ringan.

## Hands-on Practice
1) Buat `scripts/watch.js`:
```js
import { ethers } from "ethers";
import fs from "fs";
const info = JSON.parse(fs.readFileSync("deployments/sepolia.json"));
const abi = JSON.parse(fs.readFileSync("artifacts/contracts/Subscription.sol/Subscription.json")).abi;
const provider = new ethers.WebSocketProvider(process.env.SEPOLIA_WSS);
const sub = new ethers.Contract(info.address, abi, provider);

sub.on("Subscribed", (user, expiry, ev) => {
  console.log(new Date().toISOString(), "Subscribed", user, expiry.toString(), ev.log.transactionHash);
});
sub.on("Cancelled", (user, ev) => {
  console.log(new Date().toISOString(), "Cancelled", user, ev.log.transactionHash);
});

process.on("SIGINT", () => { provider.destroy(); process.exit(0); });
```
2) Jalankan: `SEPOLIA_WSS=wss://... node scripts/watch.js`.
3) (Opsional) Kirim webhook:
```js
await fetch(process.env.WEBHOOK_URL, { method:"POST", headers:{ "Content-Type":"application/json" }, body: JSON.stringify({event:"Subscribed", user}) });
```

## Exercises / Mini Project
- Tambah filter event `Claimed` di Crowdfund, kirim alert jika nilai > 1 ETH.

## Quiz
- Q1: Kapan memilih websocket daripada polling?
- Q2: Event apa paling kritis untuk dApp kamu?
- Q3: Bagaimana mematikan listener dengan aman?

## Skill Checklist
- [ ] Dapat subscribe event via WS.
- [ ] Log tercetak atau dikirim ke webhook.
- [ ] Alert dasar terpasang untuk event kritis.

---

<p align="center">
  <a href="./073-konfigurasi-produksi-dan-secrets.md">⬅️ Previous</a> |
  <a href="./075-performa-caching-dan-pooling.md">Next ➡️</a>
</p>
