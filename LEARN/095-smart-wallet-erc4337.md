<p align="center">
  <a href="./094-account-abstraction.md">⬅️ Previous</a> |
  <a href="./096-intent-based-architecture.md">Next ➡️</a>
</p>

---

# Smart Wallet & ERC-4337

## Learning Objectives
- Mengenal komponen ERC-4337: UserOperation, EntryPoint, bundler, paymaster.
- Menjalankan smart wallet contoh.
- Mengirim UserOp via bundler lokal/sandbox.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
UserOperation dikirim ke mempool bundler, EntryPoint memverifikasi & eksekusi. Smart account mengimplementasikan `validateUserOp`. Paymaster dapat menanggung gas. Butuh bundler (Stackup/Pimlico sandbox) dan RPC yang mendukung.

## Hands-on Practice
1) Jalankan bundler lokal (contoh Stackup/Pimlico sandbox; ikuti docs penyedia).
2) Deploy smart account contoh (dari repo referensi AA atau template bundler). Simpan alamat EntryPoint & account.
3) Kirim UserOp transfer ERC20:
   - Siapkan `userOp` payload (sender, callData, maxFeePerGas, signature).
   - Kirim ke bundler endpoint `rpc.sendUserOperation`.
   - Tunggu receipt; cek tx hash di explorer.

## Exercises / Mini Project
- Ukur biaya gas vs EOA untuk aksi transfer yang sama (catat di notes).

## Quiz
- Q1: Apa fungsi EntryPoint?
- Q2: Mengapa paymaster bisa sponsor gas?
- Q3: Mengapa UserOperation butuh mempool khusus?

## Skill Checklist
- [ ] Paham pipeline UserOp → bundler → EntryPoint.
- [ ] Berhasil kirim UserOp sederhana.
- [ ] Mengetahui perbedaan biaya dibanding EOA.

---

<p align="center">
  <a href="./094-account-abstraction.md">⬅️ Previous</a> |
  <a href="./096-intent-based-architecture.md">Next ➡️</a>
</p>
