# The Automated Deployer (multichain-contract-forge)

Managing 100 repositories manually is impossible. This CLI tool is designed to be the "Industrial Press" for the **Alex000115** ecosystem. It reads a configuration manifest, compiles the target Solidity files, and deploys them to multiple chains simultaneously. It ensures that your contracts have the same address on every network, simplifying frontend integration for the Master Dashboard.

## Core Features
* **Deterministic Deployment:** Uses a Singleton Factory and `CREATE2` to ensure your DEX or Escrow has the same contract address on all EVM chains.
* **Batch Verification:** Automatically submits source code to block explorers immediately after deployment.
* **Gas Strategy:** Real-time gas price monitoring to pause deployments during high-congestion periods.
* **Flat Architecture:** All logic (Compiler, Deployer, Verifier) is housed in the root directory for rapid execution.



## Logic Flow
1. **Target:** You specify a list of repos (e.g., `Repo_81`, `Repo_92`) in the `forge-config.json`.
2. **Compile:** The tool triggers the Hardhat/Foundry compiler and extracts the Bytecode and ABI.
3. **Broadcast:** The CLI sends deployment transactions to the selected RPC endpoints (Base, Optimism, etc.).
4. **Log:** Deployment addresses and transaction hashes are saved to a local `deployments.log` for the Dashboard to consume.

## Setup
1. `npm install`
2. Add your `PRIVATE_KEY` and `RPC_URLS` to `.env`.
3. `node forge-deploy.js --all`
