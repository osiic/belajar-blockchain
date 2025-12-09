<p align="center">
  <a href="./076-subgraph-dasar.md">⬅️ Previous</a> |
  <a href="./078-security-predeploy-checklist.md">Next ➡️</a>
</p>

---

# CI/CD Pipeline

## Learning Objectives
- Menyusun pipeline test, lint, build frontend.
- Menambah gating sebelum merge.
- Menjalankan kontrak tests di CI.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Gunakan GitHub Actions: job lint+test backend, lint+build frontend. Cache node_modules untuk kecepatan. Pisahkan env staging/production.

## Hands-on Practice
1) Buat `.github/workflows/ci.yml`:
```yaml
name: CI
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with: { node-version: 20, cache: 'npm' }
      - run: npm ci
      - run: npx hardhat test
      - run: npm run lint --workspaces
      - run: npm run build --workspaces
```
2) Tambah badge CI di README (opsional).
3) Tambah rule branch protection (review + CI passing).

## Exercises / Mini Project
- Tambah job optional `verify` (workflow_dispatch) yang menjalankan hardhat verify dengan input address.

## Quiz
- Q1: Mengapa lint di CI?
- Q2: Apa manfaat cache?
- Q3: Kapan menjalankan verify?

## Skill Checklist
- [ ] CI jalan untuk test/lint/build.
- [ ] Workflow disimpan di repo.
- [ ] Gates sebelum merge ada.

---

<p align="center">
  <a href="./076-subgraph-dasar.md">⬅️ Previous</a> |
  <a href="./078-security-predeploy-checklist.md">Next ➡️</a>
</p>
