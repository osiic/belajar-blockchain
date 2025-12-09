<p align="center">
  <a href="./077-ci-cd-pipeline.md">⬅️ Previous</a> |
  <a href="./079-gas-optimasi-lanjutan.md">Next ➡️</a>
</p>

---

# Security Pre-Deploy Checklist

## Learning Objectives
- Menyiapkan daftar cek keamanan sebelum rilis.
- Memastikan test & coverage memadai.
- Memverifikasi konfigurasi deploy.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Checklist mengurangi kelalaian: akses kontrol, reentrancy, input bounds, event lengkap, secrets/env, verifikasi bytecode, dokumen alamat.

## Hands-on Practice
1) Buat/isi `docs/SECURITY_CHECKLIST.md` dengan item:
   - [ ] Test hijau (`npx hardhat test`)
   - [ ] Gas reporter diperiksa (opsional)
   - [ ] Access control: onlyOwner/roles diuji
   - [ ] Reentrancy: CEI/nonReentrant diterapkan
   - [ ] Input bounds/require jelas, custom error
   - [ ] Event untuk aksi penting
   - [ ] Env secrets tidak bocor; `.env` diignore
   - [ ] Deploy outputs dicatat (`deployments/<network>.json`)
   - [ ] Verifikasi siap (Etherscan args)
2) Centang sebelum setiap rilis.

## Exercises / Mini Project
- Tambah langkah “simulate main flows on fork” (deploy + panggil fungsi kritis di fork testnet/mainnet).

## Quiz
- Q1: Item apa paling kritikal sebelum rilis?
- Q2: Mengapa simulasi di fork membantu?
- Q3: Mengapa event penting untuk audit?

## Skill Checklist
- [ ] Checklist disusun.
- [ ] Proses review diadopsi.
- [ ] Deploy lebih aman.

---

<p align="center">
  <a href="./077-ci-cd-pipeline.md">⬅️ Previous</a> |
  <a href="./079-gas-optimasi-lanjutan.md">Next ➡️</a>
</p>
