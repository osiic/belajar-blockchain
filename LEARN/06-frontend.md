# 6. Frontend Integration

## Goal
Connect a React/Vite front end to your contract using ethers.js.

## Key Concepts
- ABI + contract address are required for clients.
- `window.ethereum` (MetaMask) provides a provider; wrap with `new ethers.BrowserProvider`.
- Write vs read calls: writes need signer; reads can use provider only.

## Try it
1) Export ABI and address after deploy: save to `artifacts/Storage.json` or a custom `frontend/contractInfo.json`.
2) In a front-end (can be a new Vite app), connect:
```ts
const provider = new ethers.BrowserProvider(window.ethereum);
const signer = await provider.getSigner();
const storage = new ethers.Contract(address, abi, signer);
await storage.setNumber(99);
const current = await storage.number();
```
3) Add minimal UI: input box + button to set number, display current value.

## Done when
You can read/write the contract from a browser and explain signer vs provider.
