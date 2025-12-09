<p align="center">
  <a href="./046-proyek1-erc20-testing.md">⬅️ Previous</a> |
  <a href="./048-proyek1-erc20-frontend.md">Next ➡️</a>
</p>

---

# Proyek 1: Deploy Token

## Learning Objectives
- Deploy LRN ke localhost & sepolia.
- Simpan ABI/alamat untuk frontend.
- (Opsional) verifikasi di Etherscan.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Gunakan skrip deploy Hardhat dengan env: `SEPOLIA_RPC`, `PRIVATE_KEY`. Simpan output ke JSON agar frontend dapat mengonsumsi.

## Hands-on Practice
1) Update `scripts/deploy.js`:
```js
const { ethers, network } = require("hardhat");
async function main() {
  console.log("Deploying to", network.name);
  const Token = await ethers.getContractFactory("LearnToken");
  const initial = ethers.parseUnits("1000000");
  const cap = ethers.parseUnits("2000000");
  const token = await Token.deploy(initial, cap);
  await token.waitForDeployment();
  const address = await token.getAddress();
  console.log("LearnToken:", address);
  return { address, abi: Token.interface.formatJson() };
}
main().catch((e)=>{console.error(e);process.exit(1);});
```
2) Deploy:
```bash
npx hardhat run scripts/deploy.js --network localhost
npx hardhat run scripts/deploy.js --network sepolia
```
3) Simpan `frontend/src/contracts/token.json`:
```json
{ "address": "<alamat-sepolia>", "abi": [...] }
```
4) (Opsional) Verifikasi:
```bash
npx hardhat verify --network sepolia <alamat> 1000000000000000000000000 2000000000000000000000000
```

## Exercises / Mini Project
- Tambah output file terstruktur: `deployments/<network>.json` berisi address, tx hash, block, timestamp.

## Quiz
- Q1: Mengapa ABI perlu disimpan untuk frontend?
- Q2: Argumen apa yang dibutuhkan saat verify?
- Q3: Apa beda deploy ke `hardhat` vs `localhost`?

## Skill Checklist
- [ ] Deploy sukses di localhost & sepolia.
- [ ] ABI+alamat tersedia untuk frontend.
- [ ] (Opsional) Verifikasi berhasil.

---

<p align="center">
  <a href="./046-proyek1-erc20-testing.md">⬅️ Previous</a> |
  <a href="./048-proyek1-erc20-frontend.md">Next ➡️</a>
</p>
