<p align="center">
  <a href="./043-env-dan-keamanan-frontend.md">⬅️ Previous</a> |
  <a href="./045-proyek1-erc20-kontrak.md">Next ➡️</a>
</p>

---

# Proyek 1: ERC20 Dashboard — Perencanaan

## Learning Objectives
- Menetapkan spesifikasi token LRN (nama, simbol, supply, cap, peran owner).
- Menentukan fitur dashboard minimum & alur UX.
- Menyiapkan cabang kerja serta artefak kontrak/frontend.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Komponen proyek:
- **Kontrak**: ERC20 berbasis OpenZeppelin, optional mint/burn hanya owner, optional cap.
- **Frontend**: Next.js 14 + wagmi/viem untuk baca/tulis saldo, transfer, approve/allowance, mint/burn admin.
Prinsip: fokus fitur inti dulu, admin panel belakangan, uji revert eksplisit.

## Hands-on Practice
1) Buat cabang: `git checkout -b feature/erc20-dashboard`.
2) Tetapkan spesifikasi di `notes.md`:
   - Nama/Symbol: `Learn Token (LRN)`.
   - Supply awal: `1_000_000 * 1e18`.
   - Cap (opsional): mis. `2_000_000 * 1e18`.
   - Owner: deployer; hanya owner boleh mint/burn.
3) Buat backlog fitur minimum:
   - View: totalSupply, saldo user, allowance user→spender.
   - Actions: transfer, approve+transferFrom, mint/burn (owner).
   - UX: notifikasi, status tx, link explorer.
4) Siapkan placeholder `frontend/src/contracts/token.json` (akan diisi alamat+ABI setelah deploy).

## Exercises / Mini Project
- Sketsa wireframe: kartu saldo, form transfer, panel admin mint/burn, tabel allowance.

## Quiz
- Q1: Mengapa cap bisa diperlukan? Kapan tidak?
- Q2: Data apa yang dibutuhkan sebelum transfer (alamat, jumlah, chain, saldo, allowance)?
- Q3: Risiko jika mint tidak dibatasi?

## Skill Checklist
- [ ] Scope & spesifikasi token terdokumentasi.
- [ ] Backlog fitur dashboard dibuat.
- [ ] Cabang kerja siap.

---

<p align="center">
  <a href="./043-env-dan-keamanan-frontend.md">⬅️ Previous</a> |
  <a href="./045-proyek1-erc20-kontrak.md">Next ➡️</a>
</p>
