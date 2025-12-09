<p align="center">
  <a href="./074-monitoring-logging-onchain.md">⬅️ Previous</a> |
  <a href="./076-subgraph-dasar.md">Next ➡️</a>
</p>

---

# Performa: Caching & Pooling

## Learning Objectives
- Mengurangi beban RPC dengan cache.
- Memahami rate limit sharing di frontend.
- Menggunakan pooling/keep-alive di server (jika ada backend).

## Prerequisites
- Selesaikan modul sebelumnya.

## Theory
Cache read yang sering (balance, metadata) dengan SWR/React Query. Pooling/keep-alive untuk server calls. Hindari thundering herd dengan staleTime & deduping.

## Hands-on Practice
1) Pasang React Query:
```bash
npm install @tanstack/react-query
```
2) Bungkus readContract:
```ts
const query = useQuery({
  queryKey: ["balance", address],
  queryFn: () => publicClient.readContract({ address, abi, functionName: "balanceOf", args: [address] }),
  staleTime: 30_000,
  refetchOnWindowFocus: false,
});
```
3) Set `batch: true` di viem transport untuk menggabung call RPC.

## Exercises / Mini Project
- Tambah debounce pada input yang memicu read (mis. search tokenId).

## Quiz
- Q1: Apa manfaat cache di dApp?
- Q2: Data apa aman untuk cache lama?
- Q3: Bagaimana mencegah thundering herd?

## Skill Checklist
- [ ] Cache read utama di frontend.
- [ ] staleTime diset sesuai data.
- [ ] Panggilan RPC berkurang.

---

<p align="center">
  <a href="./074-monitoring-logging-onchain.md">⬅️ Previous</a> |
  <a href="./076-subgraph-dasar.md">Next ➡️</a>
</p>
