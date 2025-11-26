# 04. Task & Script Kustom

## Konsep
- Task: fungsi CLI terdaftar di Hardhat, berguna untuk operasi berulang.
- Script: file JS/TS dieksekusi dengan `npx hardhat run` terhadap jaringan tertentu.
- ethers v6: `ethers.getContractFactory`, `waitForDeployment`, dll.

## Langkah Praktik
1) Buat task sederhana di `tasks/list-accounts.ts` (buat folder `tasks/`):
```ts
import { task } from "hardhat/config";

task("accounts", "List akun default", async (_, hre) => {
  const accounts = await hre.ethers.getSigners();
  accounts.forEach((a, i) => console.log(i, a.address));
});
```
2) Daftarkan folder task di `hardhat.config.ts`:
```ts
import "./tasks/list-accounts";
```
3) Jalankan: `npx hardhat accounts` (gunakan network default `hardhat`).
4) Perbarui `scripts/deploy.js` ke TypeScript (opsional) atau tambahkan log network:
```js
console.log("Deploying to", network.name);
```
5) Deploy ke node lokal: `npx hardhat run scripts/deploy.js --network localhost`.

## Selesai Ketika
Task kustom muncul di daftar `npx hardhat`, dan script deploy berhasil jalan di localhost.

---
<p align="center">
  <a href="03-hardhat-runner.md">⬅️ Previous</a> |
  <a href="05-testing.md">Next ➡️</a>
</p>
