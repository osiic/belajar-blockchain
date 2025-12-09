<p align="center">
  <a href="./075-performa-caching-dan-pooling.md">⬅️ Previous</a> |
  <a href="./077-ci-cd-pipeline.md">Next ➡️</a>
</p>

---

# Subgraph Dasar

## Learning Objectives
- Memahami The Graph untuk indexing event.
- Menulis schema & mapping sederhana.
- Menjalankan subgraph lokal.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Subgraph mengekstrak event on-chain → store → query GraphQL. Schema mendefinisikan entity; mapping memproses event. Cocok untuk dashboard/analytics di luar RPC terbatas.

## Hands-on Practice
1) Instal CLI (opsional global):
```bash
npm install -g @graphprotocol/graph-cli
```
2) Init subgraph untuk ERC20:
```bash
graph init --from-contract <addr_token> --network sepolia token-subgraph
```
3) Ubah `schema.graphql`:
```graphql
type Transfer @entity {
  id: ID!
  from: Bytes!
  to: Bytes!
  value: BigInt!
  txHash: Bytes!
  timestamp: BigInt!
}
```
4) Tambah mapping `src/mapping.ts`:
```ts
import { Transfer as TransferEvent } from "../generated/Token/ERC20";
import { Transfer } from "../generated/schema";
export function handleTransfer(event: TransferEvent): void {
  let t = new Transfer(event.transaction.hash.toHex() + "-" + event.logIndex.toString());
  t.from = event.params.from;
  t.to = event.params.to;
  t.value = event.params.value;
  t.txHash = event.transaction.hash;
  t.timestamp = event.block.timestamp;
  t.save();
}
```
5) Jalankan lokal:
```bash
graph codegen && graph build && graph node --docker
graph create token-subgraph && graph deploy token-subgraph
```

## Exercises / Mini Project
- Tambah entity Holder dengan saldo agregat, update saat handleTransfer.

## Quiz
- Q1: Mengapa subgraph berguna dibanding RPC?
- Q2: Apa isi mapping?
- Q3: Bagaimana meng-query data?

## Skill Checklist
- [ ] Schema & mapping dibuat.
- [ ] Subgraph build & deploy lokal.
- [ ] Data dapat di-query via GraphQL.

---

<p align="center">
  <a href="./075-performa-caching-dan-pooling.md">⬅️ Previous</a> |
  <a href="./077-ci-cd-pipeline.md">Next ➡️</a>
</p>
