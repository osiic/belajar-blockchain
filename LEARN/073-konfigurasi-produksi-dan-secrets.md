<p align="center">
  <a href="./072-bridge-dan-asset-transfer.md">⬅️ Previous</a> |
  <a href="./074-monitoring-logging-onchain.md">Next ➡️</a>
</p>

---

# Konfigurasi Produksi & Secrets

## Learning Objectives
- Menyimpan secrets aman (dotenv/secret manager).
- Memisahkan env dev/staging/prod.
- Menetapkan kebijakan rotasi kunci.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Jangan commit secret. Gunakan vault/secret manager di CI. Pisahkan RPC/key per environment. Rotasi berkala. `NEXT_PUBLIC_` selalu diekspos—hindari untuk secret.

## Hands-on Practice
1) Buat `.env.staging` & `.env.prod` (ignored) dan `.env.example`.
2) Tambah secrets di GitHub Actions: `PRIVATE_KEY_STG`, `PRIVATE_KEY_PROD`, `SEPOLIA_RPC`, `ETHERSCAN_KEY`.
3) Update `hardhat.config.ts` pakai `dotenv/config` dan gunakan key sesuai network.
4) Untuk frontend, pakai `.env.local` hanya untuk variabel publik; simpan private key di server, bukan di browser.

## Exercises / Mini Project
- Tulis SOP rotasi kunci di `docs/SECURITY_CHECKLIST.md` (rotasi periodik, revoke lama, audit log pemakaian).

## Quiz
- Q1: Mengapa tidak pakai NEXT_PUBLIC untuk secret?
- Q2: Bagaimana menyimpan key di CI?
- Q3: Seberapa sering rotasi kunci?

## Skill Checklist
- [ ] Env dipisah per stage.
- [ ] Secrets tidak bocor ke repo.
- [ ] SOP rotasi tersedia.

---

<p align="center">
  <a href="./072-bridge-dan-asset-transfer.md">⬅️ Previous</a> |
  <a href="./074-monitoring-logging-onchain.md">Next ➡️</a>
</p>
