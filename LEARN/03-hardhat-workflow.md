# 3. Alur Kerja Hardhat

## Tujuan
Lancar memakai task Hardhat, console, dan eksekusi script.

## Konsep Kunci
- Hardhat Network: jaringan lokal in-memory, auto-mine.
- Task: bawaan (`compile`, `test`, `node`, `run`) dan kustom.
- Script: `npx hardhat run` mengeksekusi JS/TS terhadap jaringan tertentu.

## Coba
1) Cek `hardhat.config.ts` (versi Solidity 0.8.28).
2) Jalankan node lokal:
```bash
npx hardhat node
```
3) Di terminal lain, deploy pakai script yang ada:
```bash
npx hardhat run scripts/deploy.js --network localhost
```
4) Interaksi via console:
```bash
npx hardhat console --network localhost
> const storage = await ethers.getContractAt("Storage", "<alamat dari deploy>");
> await storage.setNumber(42);
> (await storage.number()).toString();
```

## Selesai ketika
Kamu bisa start/stop `npx hardhat node`, deploy, dan baca/tulis state lewat console.
