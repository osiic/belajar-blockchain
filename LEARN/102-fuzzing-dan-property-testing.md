<p align="center">
  <a href="./101-formal-verification.md">⬅️ Previous</a> |
  <a href="./103-ctf-practice-guides.md">Next ➡️</a>
</p>

---


---

<p align="center">
  <a href="./101-formal-verification.md">⬅️ Previous</a> |
  <a href="./103-ctf-practice-guides.md">Next ➡️</a>
</p>
# Fuzzing & Property Testing

## Learning Objectives
- Menggunakan fuzzing untuk menemukan edge case.
- Menulis properti (invariant) dan mem-fuzz dengan Foundry/Echidna.
- Memahami coverage fuzz.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Fuzzing mengacak input untuk melanggar properti. Property-based testing mendefinisikan “selalu benar” (invariant). Foundry `forge test --fuzz`, Echidna untuk properti ERC. False positive/negative mungkin; butuh review hasil.

## Hands-on Practice
1) (Jika memakai Foundry) contoh test fuzz:
```bash
forge init fuzz-demo
```
```solidity
function testFuzz_SetNumber(uint256 x) public {
    storageContract.setNumber(x % 1_000_000);
    assertEq(storageContract.number(), x % 1_000_000);
}
```
2) Dengan Hardhat, uji property sederhana menggunakan loop random (atau gunakan echidna.yaml untuk menjalankan Echidna pada kontrak ERC20).
3) Jalankan: `forge test --fuzz runs=200` atau `echidna .`.

## Exercises / Mini Project
- Tulis properti: “totalSupply tidak berubah setelah transfer” untuk ERC20, uji dengan fuzz.

## Quiz
- Q1: Apa itu property-based testing?
- Q2: Kapan fuzzing paling berguna?
- Q3: Risiko hasil palsu (false positive/negative)?

## Skill Checklist
- [ ] Bisa menulis properti sederhana.
- [ ] Menjalankan fuzz test.
- [ ] Memahami limit dan interpretasi hasil fuzz.
