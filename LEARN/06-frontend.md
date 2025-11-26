# 6. Integrasi Frontend

## Tujuan
Menghubungkan frontend React/Vite ke kontrak via ethers.js.

## Konsep Kunci
- Butuh ABI + alamat kontrak untuk klien.
- `window.ethereum` (MetaMask) memberi provider; bungkus dengan `new ethers.BrowserProvider`.
- Panggilan tulis vs baca: tulis butuh signer; baca cukup provider.

## Coba
1) Setelah deploy, simpan ABI + alamat ke `frontend/contractInfo.json` atau gunakan file di `artifacts/`.
2) Di frontend (mis. app Vite baru), hubungkan:
```ts
const provider = new ethers.BrowserProvider(window.ethereum);
const signer = await provider.getSigner();
const storage = new ethers.Contract(address, abi, signer);
await storage.setNumber(99);
const current = await storage.number();
```
3) Buat UI minimal: input angka + tombol set, tampilkan nilai terkini.

## Selesai ketika
Kamu bisa baca/tulis kontrak dari browser dan jelaskan beda signer vs provider.
