# 10. Deployment ke Testnet

## Tujuan
Mempersiapkan rilis ke jaringan publik (Sepolia/Holesky).

## Konsep
- Env vars untuk RPC dan private key (jangan commit).
- Perintah deploy Hardhat ke jaringan: `--network <name>`.
- Verifikasi kontrak (jika memakai Etherscan plugin).

## Langkah Praktik
1) Pasang dotenv dan plugin etherscan (opsional):
```bash
npm install --save-dev dotenv @nomicfoundation/hardhat-verify
```
2) Perbarui `hardhat.config.ts`:
```ts
import "dotenv/config";
const { SEPOLIA_RPC, PRIVATE_KEY, ETHERSCAN_KEY } = process.env;
export default defineConfig({
  networks: {
    sepolia: {
      url: SEPOLIA_RPC,
      accounts: PRIVATE_KEY ? [PRIVATE_KEY] : [],
    },
  },
  etherscan: { apiKey: ETHERSCAN_KEY },
});
```
3) Deploy token + subscription ke Sepolia:
```bash
npx hardhat run scripts/deploy.js --network sepolia
```
4) (Opsional) Verifikasi:
```bash
npx hardhat verify --network sepolia <alamat_kontrak> "arg1" "arg2"
```

## Selesai Ketika
Kontrak terdeploy di testnet, alamat dicatat, dan (jika mungkin) terverifikasi.

---
<p align="center">
  <a href="09-frontend-dapp.md">⬅️ Previous</a> |
  <a href="11-security-gas.md">Next ➡️</a>
</p>
