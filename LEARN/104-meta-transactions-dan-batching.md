<p align="center">
  <a href="./103-ctf-practice-guides.md">⬅️ Previous</a> |
  <a href="./105-tokenomics-dasar.md">Next ➡️</a>
</p>

---


---

<p align="center">
  <a href="./103-ctf-practice-guides.md">⬅️ Previous</a> |
  <a href="./105-tokenomics-dasar.md">Next ➡️</a>
</p>
# Meta Transactions & Batching

## Learning Objectives
- Memahami meta-transactions (relayer/sponsor).
- Membuat batch call sederhana.
- Menilai risiko reentrancy/batch.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Meta-tx: user tanda tangan pesan, relayer kirim tx dan bayar gas. Proteksi replay via nonce. Batch call (multicall) menggabung beberapa call untuk UX/gas, tapi perlu hati-hati reentrancy dan order efek.

## Hands-on Practice
1) Implementasi meta-tx sederhana (EIP-712) pada kontrak percobaan:
   - Simpan `nonces[user]`.
   - Verifikasi signature, lalu `executeCall`.
2) Tambah fungsi batch:
```solidity
function batch(bytes[] calldata calls) external {
    for (uint256 i; i < calls.length; i++) {
        (bool ok, ) = address(this).delegatecall(calls[i]);
        require(ok, "call failed");
    }
}
```
3) Uji dengan Hardhat: tanda tangan off-chain, relayer kirim tx; coba batch dua call state.

## Exercises / Mini Project
- Tambah nonce per user untuk meta-tx dan limiter panjang batch; tulis test replay.

## Quiz
- Q1: Keuntungan meta-tx?
- Q2: Mengapa perlu nonce?
- Q3: Risiko batch call?

## Skill Checklist
- [ ] Memahami meta-tx & batching.
- [ ] Implementasi dasar dibuat.
- [ ] Proteksi replay/reentrancy dipahami.
