<p align="center">
  <a href="./054-proyek2-nft-testing.md">⬅️ Previous</a> |
  <a href="./056-milestone2-review.md">Next ➡️</a>
</p>

---

# Proyek 2: Frontend Mint & Marketplace

## Learning Objectives
- Membangun UI mint NFT + gallery.
- Membuat halaman listing & beli dengan notifikasi.
- Menampilkan metadata tokenURI dan status transaksi.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Gunakan wagmi/viem: `useWriteContract` untuk mint/list/buy, `useReadContract` untuk ownerOf/tokenURI. Metadata IPFS perlu gateway (`https://ipfs.io/ipfs/<cid>`). Pastikan approval sebelum listing.

## Hands-on Practice
1) Halaman `/nft`:
   - Form mint: input URI, tampilkan `mintPrice` dari kontrak.
   - Gallery: jika balance > 0, loop tokenId kecil atau gunakan event/list API; fetch `tokenURI` dan render gambar/judul.
2) Halaman `/market`:
   - Form create listing (tokenId, price ETH) dan tombol cancel.
   - Daftar listing aktif: baca `listings(id)` untuk rentang kecil, filter `active`.
   - Tombol buy dengan toast (sonner) menampilkan hash.
3) Tambah hook config kontrak:
```ts
export const token = { address: TOKEN_ADDR, abi: tokenAbi } as const;
export const market = { address: MARKET_ADDR, abi: marketAbi } as const;
```
4) Jalankan dev server: `npm run dev`.

## Exercises / Mini Project
- Tambah filter listing per seller dan sort by price; badge “owned by you”.

## Quiz
- Q1: Data apa perlu untuk create listing (approval, tokenId, price)?
- Q2: Bagaimana menampilkan metadata IPFS di browser?
- Q3: Bagaimana memberi tahu user saat tx pending/sukses?

## Skill Checklist
- [ ] UI mint berjalan dan menampilkan metadata.
- [ ] Listing/buy/cancel di frontend sukses.
- [ ] Notifikasi/status tx jelas.

---

<p align="center">
  <a href="./054-proyek2-nft-testing.md">⬅️ Previous</a> |
  <a href="./056-milestone2-review.md">Next ➡️</a>
</p>
