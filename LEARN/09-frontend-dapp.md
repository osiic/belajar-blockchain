# 09. Frontend DApp

## Tujuan
Membuat dashboard sederhana (React/Vite) untuk kontrak langganan.

## Konsep
- ethers v6 di browser: `BrowserProvider`, `Contract`, signer vs provider.
- Menyimpan ABI + alamat deploy untuk frontend.
- Menangani jaringan: cek chainId, ajukan switch ke localhost/testnet.

## Langkah Praktik
1) (Opsional) Buat folder `frontend/` dengan Vite React:
```bash
npm create vite@latest frontend -- --template react-ts
cd frontend && npm install ethers
```
2) Buat file config di frontend `src/contract.ts` berisi alamat + ABI (salin dari `artifacts/...Subscription.json`).
3) Implementasi hook sederhana:
```ts
const provider = new ethers.BrowserProvider(window.ethereum);
const signer = await provider.getSigner();
const sub = new ethers.Contract(address, abi, signer);
```
4) UI minimal:
- Tombol Connect.
- Form subscribe (jumlah bulan) -> panggil `approve` LRN lalu `subscribe`.
- Tampilkan status langganan (expiry timestamp -> tanggal lokal).
- Tombol Cancel.
5) Jalankan dev server: `npm run dev` dari folder frontend.

## Selesai Ketika
Dari browser, kamu bisa connect wallet, approve token, subscribe, melihat expiry berubah.

---
<p align="center">
  <a href="08-subscription-contract.md">⬅️ Previous</a> |
  <a href="10-deployment.md">Next ➡️</a>
</p>
