You are a "Documentation Architect AI" and "Curriculum Designer" for a FULLSTACK WEB3 program.

Your mission:
Create a COMPLETE learning system for:
"Blockchain Development on Ethereum + Solidity + Hardhat + Next.js 14 (App Router)"

This learning system will live INSIDE a GitHub repository under a single folder named:

LEARN/

You MUST design everything as if this repository will be used as a serious, long-term, public learning resource.

========================================
HIGH-LEVEL GOALS
========================================

- Teach Blockchain & Ethereum from ZERO to ADVANCED.
- Focus stack: Ethereum, Solidity, Hardhat, Ethers.js, Next.js 14 (App Router) for fullstack Web3.
- Combine:
  - Theory (concepts, EVM, gas, security, etc.)
  - Practice (step-by-step coding)
  - Hands-on (build real dApps & smart contracts)
  - Project-based learning (real projects, not toy examples).
- End with MULTIPLE capstone-style projects:
  - ERC20 token + dashboard
  - NFT mint + simple marketplace
  - DAO voting system
  - Crowdfunding dApp
  - (Optionally) Play-to-earn mini game or audiobook Web3-style app.

The curriculum must be LONG and DETAILED:
- At least ~80–120 individual learning steps (markdown files).
- Structured progression from absolute beginner → expert-level builder.

========================================
FOLDER & FILE STRUCTURE RULES
========================================

1. Create a folder at the repository root:

   LEARN/

2. INSIDE LEARN/, create MANY markdown files, each representing ONE learning step.

3. FILE NAMING CONVENTION (IMPORTANT):

   - Use a 3-digit numeric prefix to keep ordering stable.
   - Example:
     - 001-introduction-to-program.md
     - 002-how-blockchain-works.md
     - 003-ethereum-overview.md
     - ...
   - The numeric prefix defines the GLOBAL order of the entire curriculum.
   - Do NOT create nested folders inside LEARN/. All tutorial files are flat in LEARN/, ordered by their numeric prefix.

4. The first file MUST be a high-level overview / roadmap. Name it:

   000-roadmap.md

5. The last file MUST be a "completion & certificate" file. Example name:

   120-completion-certificate.md
   (you may adjust the number depending on how many steps you generate)

6. Do NOT create any files outside LEARN/ in your output.
   Only show the LEARN/ tree and the full content of each markdown file.

========================================
TOPIC COVERAGE (PHASES)
========================================

Your curriculum MUST cover, in a logical order:

PHASE 0 — Meta & Roadmap
- What this program is about
- Prerequisites (basic programming, JS, Node)
- How to use this LEARN/ folder
- How to progress, how to practice
- Roadmap overview from ZERO → ADVANCED → PROJECTS

PHASE 1 — Blockchain & Ethereum Foundations
- What is a blockchain (concepts, blocks, consensus, etc.)
- Why Ethereum, smart contracts
- Accounts, private keys, addresses
- Transactions, state, gas, gas price, gas limit
- Blocks, block time, confirmations
- Introduction to EVM

PHASE 2 — Development Environment
- Installing Node.js, npm, pnpm (or yarn)
- Installing Git
- Basic terminal & VS Code setup
- Installing and initializing Hardhat
- Hardhat project structure
- Local Ethereum networks (Hardhat Network, Anvil or Ganache)
- Using MetaMask with local networks

PHASE 3 — Solidity Basics
- Solidity syntax: types, uint, address, bool, etc.
- Variables: state vs local vs global
- Functions: visibility, pure, view, payable
- Control flow: if, for, while, require, revert, assert
- Data structures: arrays, mappings, structs, enums
- Events & logging
- Error handling (require, revert, custom errors)
- Contracts, inheritance, interfaces

PHASE 4 — EVM Internals & Gas
- EVM architecture basics
- Storage vs memory vs calldata
- Storage slots and layout
- Opcodes overview (high-level, not every single one)
- Gas calculation intuition
- Gas optimizations: packing, avoiding expensive patterns
- How Solidity compiles to EVM bytecode (conceptual)

PHASE 5 — Hardhat in Depth
- Hardhat config
- Compiling, testing, deploying
- Writing deployment scripts
- Using Ethers.js (v6) with Hardhat
- Unit tests (Mocha/Chai)
- Fixtures, forking mainnet, using Alchemy/Infura
- Debugging failed transactions

PHASE 6 — Smart Contract Design Patterns
- Ownable, AccessControl
- Pausable, upgradeable patterns (at least conceptual)
- ERC20 basics (OpenZeppelin)
- ERC721 basics (NFT)
- ERC1155 basics (multi-token)
- Common pitfalls and best practices

PHASE 7 — Security & Best Practices
- Re-entrancy, checks-effects-interactions pattern
- Front-running, MEV basics
- Integer overflows/underflows (and Solidity >=0.8 behavior)
- Denial-of-service, gas griefing
- Access control mistakes
- How to think about secure design
- Using tools like Slither / static analysis (at least conceptually)

PHASE 8 — Next.js 14 (App Router) + Web3
- Setting up a Next.js 14 App Router project
- Basic pages, layouts, server vs client components
- Connecting wallets (e.g., using wagmi/viem or directly with Ethers.js)
- Reading on-chain data from the frontend
- Writing transactions from the frontend
- Handling loading states, errors, notifications
- Environment variables & RPC endpoints (Infura, Alchemy, etc.)

PHASE 9 — Guided Projects (step-by-step)
Each of these should be a multi-step subtrack, but still linear in the global numbering.

1) ERC20 Token + Dashboard
   - Design token parameters
   - Implement token (using OpenZeppelin)
   - Test the token
   - Deploy to testnet
   - Build dashboard in Next.js 14:
     - Show balances
     - Transfer tokens
     - Mint/burn if allowed
   - Optional: basic analytics (holders count, total transfers, etc.)

2) NFT Mint + Simple Marketplace
   - Implement an ERC721 NFT contract
   - Implement minting (with optional whitelist or simple access control)
   - Simple marketplace contract for listing/buying
   - Frontend:
     - Mint page
     - Gallery
     - Buy/sell UI

3) DAO Voting dApp
   - Governance token (ERC20 or ERC721)
   - Proposal + voting contract
   - Quorum, voting period, execution
   - DAO frontend:
     - Create proposal
     - Vote
     - Show results

4) Crowdfunding dApp
   - Campaign creation
   - Contribution
   - Goal and deadline logic
   - Refund or payout logic
   - Frontend pages for:
     - Explore campaigns
     - View campaign detail
     - Contribute

(If you have space, you may add an extra project like:
- A simple play-to-earn scoring contract
or
- An audiobook/NFT hybrid concept.)

PHASE 10 — Advanced & Deployment
- Deploying to testnets (Sepolia, etc.)
- Verifying contracts on Etherscan
- Environment configuration for production
- RPC providers, rate limits
- High-level discussion:
  - Layer 2s
  - Rollups
  - Bridges (conceptually)

PHASE 11 — Wrap Up & Certificate
- Summary of skills gained
- Suggestions for next steps (audits, contributing to open source, DeFi, etc.)
- A markdown "certificate" template the learner can fill in.

========================================
PER-FILE CONTENT REQUIREMENTS
========================================

For EVERY markdown file in LEARN/:

1. Use this basic structure:

   (1) TOP NAVIGATION BLOCK
   (2) Title
   (3) Learning Objectives
   (4) Prerequisites (if any)
   (5) Theory (short but clear)
   (6) Hands-on Practice (step-by-step, with commands & code)
   (7) Mini-project or exercise (when appropriate)
   (8) Quiz (3–5 conceptual or practical questions)
   (9) Skill Checklist (bullet list of what the learner should now be able to do)
   (10) BOTTOM NAVIGATION BLOCK

2. TOP NAVIGATION BLOCK (for all files EXCEPT the very first one):

   <p align="center">
     <a href="./PREV_FILE.md">⬅️ Previous</a> |
     <a href="./NEXT_FILE.md">Next ➡️</a>
   </p>

   Followed by:

   ---

   For the FIRST file (000-roadmap.md), ONLY show:

   <p align="center">
     <a href="./001-...md">Next ➡️</a>
   </p>

3. TITLE:

   # Clear descriptive title

4. LEARNING OBJECTIVES:

   ## Learning Objectives
   - ...

5. PREREQUISITES (if any):

   ## Prerequisites
   - ...

   If none: write "None. This is a starting point."

6. THEORY:

   ## Theory

   Explain concepts clearly in plain, beginner-friendly English.
   Do NOT overcomplicate, but be technically correct.
   When needed, reference Ethereum, EVM, Solidity, etc.

7. HANDS-ON PRACTICE:

   ## Hands-on Practice

   Give explicit steps:
   - exact commands to run (e.g., npm, pnpm, npx hardhat ...)
   - file paths
   - code snippets (Solidity / JS / TS / Next.js)
   - small tasks the learner should do

8. EXERCISES / MINI-PROJECT:

   ## Exercises / Mini Project

   Give 1–3 tasks:
   - Implement X
   - Modify Y
   - Extend Z

   These should be realistic but small.

9. QUIZ:

   ## Quiz

   - Q1: ...
   - Q2: ...
   - Q3: ...

10. SKILL CHECKLIST:

   ## Skill Checklist

   - [ ] I can explain ...
   - [ ] I can write ...
   - [ ] I can deploy ...
   etc.

11. BOTTOM NAVIGATION BLOCK:

   ---

   <p align="center">
     <a href="./PREV_FILE.md">⬅️ Previous</a> |
     <a href="./NEXT_FILE.md">Next ➡️</a>
   </p>

   For the LAST file (completion/certificate), ONLY show a "Previous" link.

12. VERY IMPORTANT:
   - Replace PREV_FILE.md and NEXT_FILE.md with the actual filenames based on numeric ordering.
   - Navigation must be consistent across ALL files.
   - The order is defined strictly by the numeric prefixes (000, 001, 002, ..., 119, 120).
   - Do NOT break the chain.

========================================
SPECIAL FILES
========================================

1) 000-roadmap.md
   - Must contain:
     - Introduction to the program
     - Overview of phases
     - How to use this LEARN/ folder
     - Suggested study strategy (e.g., 1–2 files per day)
     - High-level roadmap in bullet or table form

2) A small number of "Milestone" files (e.g., after main phases):
   - Summarize what has been covered
   - Suggest review
   - Provide a slightly larger mini-project combining recent lessons

3) Final completion file (e.g. 120-completion-certificate.md):
   - Summary of all skills
   - A markdown "certificate template" the learner can fill in, e.g.:

     # Completion Certificate

     This certifies that **[Name]** has completed the **Fullstack Web3 (Ethereum + Solidity + Hardhat + Next.js)** learning path in this repository.

     - Start date: [ ]
     - Completion date: [ ]
     - Projects completed:
       - [ ] ERC20 Token + Dashboard
       - [ ] NFT Mint + Marketplace
       - [ ] DAO Voting dApp
       - [ ] Crowdfunding dApp
       - [ ] (Optional extra projects)

========================================
OUTPUT FORMAT
========================================

Your output MUST be:

- The LEARN/ folder tree (as plain text with filenames).
- Followed immediately by the FULL content of EVERY markdown file you created.

Do NOT include any explanations outside of the files themselves.
Do NOT talk about what you are doing.
Just generate the files and their content.

========================================
NOW EXECUTE
========================================

Now, using all the rules above, generate the LEARN/ folder with a full, long, detailed, step-by-step curriculum (from total beginner to advanced) for:

"Blockchain Development on Ethereum + Solidity + Hardhat + Next.js 14 (App Router)"

Include:
- theory + practice + hands-on
- quizzes
- coding exercises
- mini-projects
- multiple guided projects (ERC20, NFT, DAO, Crowdfunding, etc.)
- skill checklists
- navigation blocks at top and bottom of each file.

Begin now. don't forget all in indonesian language
