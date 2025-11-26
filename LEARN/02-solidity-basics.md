# 2. Dasar Solidity

## Tujuan
Paham dasar bahasa dan memperluas kontrak Storage yang ada.

## Konsep Kunci
- Lokasi data: storage, memory, calldata.
- Visibilitas: public / external / internal / private.
- Fungsi: view/pure vs mengubah state.
- Event: log ringan; parameter `indexed` memudahkan filter.
- Error/revert: `require`, `revert`, `assert`.

## Coba
1) Tambah event dan pengecekan batas di `contracts/Storage.sol`:
```solidity
// emit saat nilai berubah
event NumberUpdated(uint256 indexed previous, uint256 indexed current, address indexed caller);
```
2) Ubah `setNumber` agar `require(_num <= 1_000_000, "Too big");` lalu emit event.
3) Kompilasi: `npx hardhat compile` (perbaiki warning jika ada).

## Selesai ketika
- Kompilasi sukses.
- Kamu bisa jelaskan bedanya storage/memory dan fungsi event.
