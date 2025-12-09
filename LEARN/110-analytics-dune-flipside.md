<p align="center">
  <a href="./109-automation-keepers.md">⬅️ Previous</a> |
  <a href="./111-mobile-web3-walletconnect.md">Next ➡️</a>
</p>

---

# Analytics: Dune & Flipside

## Learning Objectives
- Menarik data on-chain via SQL (Dune/Flipside).
- Membuat visualisasi KPI dApp (tx, volume, holders).
- Mengaitkan metrik dengan fitur produk.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Dune/Flipside menyediakan tabel transaksi/log EVM. KPI umum: daily active users, jumlah transfer, volume, holder unik, listing/buy (marketplace), vote (DAO). Data diambil via SQL, divisualisasi jadi chart.

## Hands-on Practice
1) Query Dune hitung transfer LRN per hari (ganti alamat token):
```sql
SELECT date_trunc('day', block_time) AS day,
       COUNT(*) AS tx_count,
       SUM(value/1e18) AS total_amount
FROM erc20."ERC20_evt_Transfer"
WHERE contract_address = '\\xYourTokenAddress'
GROUP BY 1
ORDER BY 1;
```
2) Buat chart line, simpan dashboard, salin URL ke README.
3) Holder unik (kasar):
```sql
WITH addrs AS (
  SELECT to_address AS addr FROM erc20."ERC20_evt_Transfer" WHERE contract_address='\\x...'
  UNION
  SELECT from_address AS addr FROM erc20."ERC20_evt_Transfer" WHERE contract_address='\\x...'
)
SELECT COUNT(DISTINCT addr) AS unique_holders FROM addrs;
```
4) Tambah query top 10 holders dan volume 7 hari terakhir.

## Exercises / Mini Project
- Buat dashboard publik berisi 3 widget: tx harian, top holders, volume 7d; tempel link di README.

## Quiz
- Q1: Mengapa hasil holder via log bisa tidak 100% akurat?
- Q2: Data apa diperlukan untuk menghitung DAU?
- Q3: Bagaimana cara membagikan dashboard ke tim?

## Skill Checklist
- [ ] Akun Dune/Flipside siap.
- [ ] Dashboard dasar dibuat dan dibagikan.
- [ ] KPI utama dApp tercatat.

---

<p align="center">
  <a href="./109-automation-keepers.md">⬅️ Previous</a> |
  <a href="./111-mobile-web3-walletconnect.md">Next ➡️</a>
</p>
