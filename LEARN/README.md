# Blockchain Learning Path

Welcome! This path is tailored for a web-dev moving into Solidity/Hardhat. Work through modules in order; each has a hands-on task using this repo.

## How to use
- Read a module, then do the "Try it" steps in your terminal/editor.
- Keep Hardhat artifacts clean: run `npx hardhat clean` between bigger changes if builds get messy.
- Track notes in `LEARN/notes.md` (create it) and keep questions per module.
- Expected total time: ~6–10 focused hours.

## Modules
1. Foundations & Setup (`01-foundations.md`)
2. Solidity Basics (`02-solidity-basics.md`)
3. Hardhat Workflow (`03-hardhat-workflow.md`)
4. Testing Smart Contracts (`04-testing.md`)
5. Deployment & Networks (`05-deployment.md`)
6. Frontend Integration (`06-frontend.md`)
7. Security & Gas Hygiene (`07-security.md`)
8. Next Steps & References (`08-next-steps.md`)

## Repo quick start
```bash
npm install
npx hardhat compile
npx hardhat test   # will fail until you add tests in module 4
```
