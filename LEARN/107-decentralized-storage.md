<p align="center">
  <a href="./106-governance-design-lanjut.md">⬅️ Previous</a> |
  <a href="./108-oracle-dan-data-feed.md">Next ➡️</a>
</p>

---

# Decentralized Storage (IPFS/Filecoin/Arweave)

## Learning Objectives
- Memahami cara simpan metadata off-chain.
- Menggunakan IPFS untuk NFT metadata.
- Menilai trade-off cost & permanence.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
IPFS: content-addressed, perlu pin untuk bertahan. Arweave: permanen dengan biaya di muka. Filecoin: penyimpanan terdesentralisasi berbasis deal. Untuk NFT, gunakan `ipfs://<cid>` dan gateway untuk fetch.

## Hands-on Practice
1) Unggah metadata contoh ke IPFS (web3.storage/Pinata):
   - JSON `{ "name": "Example", "description": "...", "image": "ipfs://<cid_gambar>" }`
2) Set `tokenURI` ke `ipfs://<cid_metadata>`.
3) Catat cara pin (Pinata/web3.storage) dan tambahkan di docs.

## Exercises / Mini Project
- Buat skrip upload JSON + gambar ke IPFS lalu set tokenURI batch (Hardhat task kecil).

## Quiz
- Q1: Apa itu CID?
- Q2: Mengapa perlu pin?
- Q3: Kapan pilih Arweave?

## Skill Checklist
- [ ] Bisa unggah ke IPFS.
- [ ] Paham CID & pinning.
- [ ] Menilai opsi penyimpanan.

---

<p align="center">
  <a href="./106-governance-design-lanjut.md">⬅️ Previous</a> |
  <a href="./108-oracle-dan-data-feed.md">Next ➡️</a>
</p>
