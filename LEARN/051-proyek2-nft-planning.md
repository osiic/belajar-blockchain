<p align="center">
  <a href="./050-milestone1-review.md">⬅️ Previous</a> |
  <a href="./052-proyek2-nft-kontrak.md">Next ➡️</a>
</p>

---

# Proyek 2: NFT & Marketplace — Perencanaan

## Learning Objectives
- Menetapkan scope koleksi NFT dan marketplace sederhana.
- Menentukan model metadata, harga mint, metode pembayaran.
- Mendesain alur mint → list → buy + fee model.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Komponen:
- **NFT**: ERC721, mint berbayar (ETH), tokenURI per token (IPFS).
- **Marketplace**: listing NFT, beli dengan ETH, fee marketplace opsional.
Prinsip: transaksi inti dipisah (mint di NFT, jual-beli di marketplace), event jelas untuk indexing.

## Hands-on Practice
1) Cabang: `git checkout -b feature/nft-market`.
2) Tetapkan parameter di `notes.md`:
   - Supply max (mis. 5_000).
   - Mint price (mis. 0.01 ETH).
   - Mint model: public mint (allowlist opsional).
   - Fee marketplace: mis. 2.5% ke owner.
3) Definisikan struktur listing (untuk kontrak market):
   - `seller`, `nft`, `tokenId`, `price`, `active`.
4) Buat backlog fitur:
   - Mint, withdraw funds.
   - List, buy, cancel.
   - Event: Minted, ListingCreated, Bought, Cancelled.

## Exercises / Mini Project
- Gambar sequence diagram mint → list → buy → fee/royalty alur dana.

## Quiz
- Q1: Data minimum apa untuk listing?
- Q2: Kapan memilih bayar dengan ETH vs ERC20?
- Q3: Bagaimana membagi fee marketplace?

## Skill Checklist
- [ ] Scope NFT + marketplace jelas.
- [ ] Parameter mint & fee terdokumentasi.
- [ ] Diagram alur dibuat.

---

<p align="center">
  <a href="./050-milestone1-review.md">⬅️ Previous</a> |
  <a href="./052-proyek2-nft-kontrak.md">Next ➡️</a>
</p>
