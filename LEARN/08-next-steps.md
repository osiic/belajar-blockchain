# 8. Langkah Lanjut & Referensi

## Tujuan
Tahu arah setelah dasar-dasar.

## Saran
- Jelajahi standar ERC: mulai dari ERC20 (token fungible) dan ERC721 (NFT). Implementasi versi minimal dan uji transfer/approval.
- Tambah tooling: ESLint/Prettier, `hardhat-gas-reporter`, `solhint` untuk lint Solidity.
- Coba forking mainnet: `npx hardhat node --fork <ALCHEMY_OR_INFURA_URL>` lalu interaksi dengan kontrak live dalam sandbox.
- Pelajari upgrade: coba plugin OpenZeppelin Upgrades (proxy pattern) dan pahami risikonya.
- Mindset keamanan: baca post-mortem insiden terbaru; latihan di CTF seperti Ethernaut.

## Referensi
- Dokumentasi Hardhat: https://hardhat.org/hardhat-runner/docs
- Dokumentasi Solidity: https://docs.soliditylang.org
- OpenZeppelin Contracts: https://docs.openzeppelin.com/contracts
