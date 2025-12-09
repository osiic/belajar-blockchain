<p align="center">
  <a href="./069-verifikasi-etherscan-ci.md">⬅️ Previous</a> |
  <a href="./071-layer2-dan-rollup.md">Next ➡️</a>
</p>

---

# RPC Provider & Rate Limit

## Learning Objectives
- Memilih penyedia RPC (Alchemy/Infura/Ankr/dll) dengan fallback.
- Menangani rate limit dengan retry/backoff.
- Mengurangi beban dengan pengaturan polling/cache.

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
RPC publik punya batas panggilan. Gunakan beberapa endpoint dengan fallback. Kurangi polling berlebihan di frontend. Simpan kunci di env, jangan di klien bila sensitif (gunakan proxy/server jika perlu).

## Hands-on Practice
1) Tambah dua RPC di config frontend (viem/wagmi):
```ts
import { createConfig, http } from "wagmi";
import { sepolia } from "wagmi/chains";
const rpcPrimary = process.env.NEXT_PUBLIC_RPC_SEPOLIA!;
const rpcFallback = process.env.NEXT_PUBLIC_RPC_SEPOLIA_FALLBACK!;
export const config = createConfig({
  chains: [sepolia],
  transports: {
    [sepolia.id]: http(rpcPrimary, { retryCount: 2, retryDelay: 500, batch: true, fallback: http(rpcFallback) })
  }
});
```
2) Kurangi polling: set `pollingInterval` (mis. 10–20s) untuk data yang tidak kritis.
3) Backend/script: gunakan provider dengan `retry` dan `timeout` (ethers v6 `new ethers.JsonRpcProvider(url, { polling: 4000 })`).

## Exercises / Mini Project
- Buat wrapper fetch RPC dengan exponential backoff dan logging error singkat.

## Quiz
- Q1: Mengapa butuh fallback RPC?
- Q2: Apa risiko menaruh RPC key di frontend?
- Q3: Bagaimana mengurangi panggilan RPC di UI?

## Skill Checklist
- [ ] RPC primary/fallback dikonfigurasi.
- [ ] Retry/backoff diterapkan.
- [ ] Polling disetel untuk mengurangi beban.

---

<p align="center">
  <a href="./069-verifikasi-etherscan-ci.md">⬅️ Previous</a> |
  <a href="./071-layer2-dan-rollup.md">Next ➡️</a>
</p>
