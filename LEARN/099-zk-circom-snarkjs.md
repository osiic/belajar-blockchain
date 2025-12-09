<p align="center">
  <a href="./098-privacy-zk-basics.md">⬅️ Previous</a> |
  <a href="./100-mini-zk-rollup-dapp.md">Next ➡️</a>
</p>

---


---

<p align="center">
  <a href="./098-privacy-zk-basics.md">⬅️ Previous</a> |
  <a href="./100-mini-zk-rollup-dapp.md">Next ➡️</a>
</p>
# Circom & snarkjs Singkat

## Learning Objectives
- Menulis sirkuit sederhana di Circom.
- Menghasilkan proof dengan snarkjs.
- Memahami alur compile → setup → prove → verify.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Circom mendefinisikan constraint; snarkjs mengkompilasi ke R1CS, melakukan trusted setup (Groth16), generate proof, dan verifikasi. Untuk produksi, gunakan ceremony terpercaya dan audit.

## Hands-on Practice
1) Instal:
```bash
npm install -g circom
npm install -g snarkjs
```
2) Buat `circuits/less_than_10.circom`:
```
template LessThan10() {
   signal input x;
   signal output ok;
   ok <== x < 10;
}
component main = LessThan10();
```
3) Jalankan:
```bash
circom circuits/less_than_10.circom --r1cs --wasm --sym -o build
snarkjs groth16 setup build/less_than_10.r1cs pot.ptau build/less_than_10_0000.zkey
snarkjs zkey contribute build/less_than_10_0000.zkey build/less_than_10_final.zkey
snarkjs zkey export verificationkey build/less_than_10_final.zkey build/verification_key.json
node build/less_than_10_js/generate_witness.js build/less_than_10_js/less_than_10.wasm input.json witness.wtns
snarkjs groth16 prove build/less_than_10_final.zkey witness.wtns proof.json public.json
snarkjs groth16 verify build/verification_key.json public.json proof.json
```
4) Ubah sirkuit untuk memverifikasi hash (poseidon) sebagai latihan lanjutan.

## Exercises / Mini Project
- Buat sirkuit yang membuktikan penjumlahan dua angka tanpa mengungkap inputnya.

## Quiz
- Q1: Tahap trusted setup untuk apa?
- Q2: Apa output utama snarkjs?
- Q3: Mengapa proof bisa diverifikasi cepat?

## Skill Checklist
- [ ] Bisa menulis sirkuit dasar.
- [ ] Menghasilkan proof & verify.
- [ ] Paham alur setup → prove → verify.
