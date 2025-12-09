<p align="center">
  <a href="./093-completion-certificate.md">⬅️ Previous</a> |
  <a href="./095-smart-wallet-erc4337.md">Next ➡️</a>
</p>

---

# Account Abstraction (AA)

## Learning Objectives
- Memahami konsep AA vs EOA.
- Menjelaskan manfaat UX (social recovery, batched tx, sponsorship).
- Mengerti peran EntryPoint & UserOperation.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
AA memindahkan logika validasi tx ke smart account. ERC-4337 memakai mempool khusus UserOperation, EntryPoint untuk verifikasi/eksekusi, bundler untuk memasukkan ke blok, paymaster untuk sponsor gas.

## Hands-on Practice
1) Baca ringkasan ERC-4337 (spec).
2) Catat manfaat AA untuk dApp kamu (contoh: auto-approve + paymaster untuk user baru).
3) Siapkan env untuk bundler (akan dipakai modul 095).

## Exercises / Mini Project
- Tulis sketsa flow AA dApp: user login → signer → buat UserOp → bundler → EntryPoint → smart account.

## Quiz
- Q1: Apa inti perbedaan AA vs EOA?
- Q2: Apa fungsi paymaster?
- Q3: Mengapa AA meningkatkan UX?

## Skill Checklist
- [ ] Paham konsep AA & komponen utamanya.
- [ ] Bisa menjelaskan manfaat AA ke tim.
- [ ] Siap lanjut ke praktik ERC-4337.

---

<p align="center">
  <a href="./093-completion-certificate.md">⬅️ Previous</a> |
  <a href="./095-smart-wallet-erc4337.md">Next ➡️</a>
</p>
