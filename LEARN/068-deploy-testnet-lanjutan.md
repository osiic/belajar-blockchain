<p align="center">
  <a href="./067-milestone4-review.md">⬅️ Previous</a> |
  <a href="./069-verifikasi-etherscan-ci.md">Next ➡️</a>
</p>

---

# Deploy Testnet Lanjutan

## Learning Objectives
- Menambahkan beberapa jaringan (Sepolia + L2) di Hardhat.
- Memisahkan akun deploy (staging vs production).
- Menyimpan output deploy terstruktur per network.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Multi-network config memudahkan switching. Simpan hasil deploy di `deployments/<network>.json` agar frontend/ops sinkron. Gunakan env terpisah: `PRIVATE_KEY_STG`, `PRIVATE_KEY_PROD`.

## Hands-on Practice
1) Update `hardhat.config.ts`:
```ts
import "dotenv/config";
const { SEPOLIA_RPC, OPTIMISM_RPC, PRIVATE_KEY_STG } = process.env;
export default {
  solidity: "0.8.28",
  networks: {
    sepolia: { url: SEPOLIA_RPC, accounts: PRIVATE_KEY_STG ? [PRIVATE_KEY_STG] : [] },
    optimismTest: { url: OPTIMISM_RPC, accounts: PRIVATE_KEY_STG ? [PRIVATE_KEY_STG] : [] },
  },
};
```
2) Ubah `scripts/deploy.js` menulis file:
```js
const fs = require("fs");
const path = require("path");
...
const { address } = await main();
const out = { address, network: network.name, timestamp: Date.now() };
const file = path.join(__dirname, "..", "deployments", `${network.name}.json`);
fs.mkdirSync(path.dirname(file), { recursive: true });
fs.writeFileSync(file, JSON.stringify(out, null, 2));
```
3) Deploy:
```bash
npx hardhat run scripts/deploy.js --network sepolia
npx hardhat run scripts/deploy.js --network optimismTest
```

## Exercises / Mini Project
- Tambah validasi versi compiler: log `hre.config.solidity.compilers[0].version` sebelum deploy dan hentikan jika tidak sesuai.

## Quiz
- Q1: Mengapa pisahkan key staging/production?
- Q2: Bagaimana memastikan frontend memakai alamat yang benar?
- Q3: Kapan memilih L2 dibanding L1 testnet?

## Skill Checklist
- [ ] Multi-network terkonfigurasi.
- [ ] Output deploy per network tersimpan.
- [ ] Akun deploy terpisah aman.

---

<p align="center">
  <a href="./067-milestone4-review.md">⬅️ Previous</a> |
  <a href="./069-verifikasi-etherscan-ci.md">Next ➡️</a>
</p>
