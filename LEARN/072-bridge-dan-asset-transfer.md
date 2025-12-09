<p align="center">
  <a href="./071-layer2-dan-rollup.md">⬅️ Previous</a> |
  <a href="./073-konfigurasi-produksi-dan-secrets.md">Next ➡️</a>
</p>

---

# Bridge & Transfer Aset

## Learning Objectives
- Memahami cara kerja bridge antar chain.
- Mengetahui risiko bridge.
- Menyiapkan panduan bridging untuk pengguna.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Bridge mengunci/membakar aset di chain asal lalu mencetak/wrap di chain tujuan. Risiko: kontrak bridge diretas, depeg wrapped asset, finality berbeda. Gunakan bridge resmi L2 jika tersedia.

## Hands-on Practice
1) Dokumentasikan bridge resmi L2 (Optimism/Arbitrum) di `docs/BRIDGE.md` (langkah & link).
2) Coba bridging testnet kecil (ETH) untuk cek UX dan biaya.
3) Tambah di README frontend: cara mendapat token di L2 (faucet + bridge).

## Exercises / Mini Project
- Buat halaman bantuan “Cara bridging” di frontend (step-by-step + link bridge).

## Quiz
- Q1: Risiko utama bridge?
- Q2: Apa yang terjadi pada aset asal saat bridging?
- Q3: Mengapa perlu panduan user?

## Skill Checklist
- [ ] Paham alur bridging.
- [ ] Sudah mencoba bridging testnet.
- [ ] Dokumentasi user tersedia.

---

<p align="center">
  <a href="./071-layer2-dan-rollup.md">⬅️ Previous</a> |
  <a href="./073-konfigurasi-produksi-dan-secrets.md">Next ➡️</a>
</p>
