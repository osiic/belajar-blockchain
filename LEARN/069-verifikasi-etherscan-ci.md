<p align="center">
  <a href="./068-deploy-testnet-lanjutan.md">⬅️ Previous</a> |
  <a href="./070-rpc-provider-dan-rate-limit.md">Next ➡️</a>
</p>

---

# Verifikasi Etherscan & CI

## Learning Objectives
- Memverifikasi kontrak otomatis via Hardhat.
- Menambahkan job CI untuk verify setelah deploy.
- Menangani argumen constructor dengan benar.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Verifikasi memastikan kode sumber cocok dengan bytecode on-chain; meningkatkan transparansi. Hardhat-verify memerlukan API key. CI dapat memicu verifikasi pascadeploy (manual atau otomatis) agar konsisten.

## Hands-on Practice
1) Pastikan plugin sudah ada (`@nomicfoundation/hardhat-verify`) dan env: `ETHERSCAN_KEY`, `SEPOLIA_RPC`, `PRIVATE_KEY_STG`.
2) Tambah script npm:
```json
"scripts": { "verify:sepolia": "hardhat verify --network sepolia" }
```
3) Contoh verify (ganti argumen LRN):
```bash
npx hardhat verify --network sepolia <alamat_kontrak> 1000000000000000000000000 2000000000000000000000000
```
4) Workflow CI minimal `.github/workflows/verify.yml`:
```yaml
name: Verify
on:
  workflow_dispatch:
    inputs:
      address: { required: true }
jobs:
  verify:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: 20 }
      - run: npm ci
      - run: npx hardhat verify --network sepolia ${{ github.event.inputs.address }} 1000000000000000000000000 2000000000000000000000000
        env:
          SEPOLIA_RPC: ${{ secrets.SEPOLIA_RPC }}
          ETHERSCAN_KEY: ${{ secrets.ETHERSCAN_KEY }}
          PRIVATE_KEY_STG: ${{ secrets.PRIVATE_KEY_STG }}
```
5) Setelah verify, pastikan `deployments/sepolia.json` diperbarui dengan alamat & block untuk frontend.

## Exercises / Mini Project
- Tambah langkah check kecocokan bytecode (verify gagal jika mismatch): catat penyebab umum (versi compiler/optimizer/argumen).

## Quiz
- Q1: Mengapa verifikasi penting bagi pengguna?
- Q2: Sebutkan dua penyebab verify gagal.
- Q3: Bagaimana mengoper argumen constructor saat verify?

## Skill Checklist
- [ ] Kontrak berhasil diverifikasi.
- [ ] Job CI verify tersedia.
- [ ] ABI/alamat sinkron dengan frontend.

---

<p align="center">
  <a href="./068-deploy-testnet-lanjutan.md">⬅️ Previous</a> |
  <a href="./070-rpc-provider-dan-rate-limit.md">Next ➡️</a>
</p>
