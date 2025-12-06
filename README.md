📘 README – ARC Network Soulbound Token (SBT) Minting System
🎖️ Overview

This repository contains a fully implemented Soulbound Token (SBT) system deployed on the ARC Network Testnet.
The project includes:

✔ A secure non-transferable ERC-721 SBT

✔ Support for free minting

✔ Burn functionality, allowing remint after deletion

✔ Randomized token IDs for uniqueness

✔ On-chain SBT ownership tracking (userTokenId)

✔ Metadata hosted via GitHub RAW

✔ Frontend integration (Replit-friendly)

This SBT can be used for:

User badges

On-chain achievements

Proof-of-participation (PoP)

XP or progress badges

Reputation tokens

Gamified DApps

🚀 Features
🔐 1. Non-transferable (Real SBT)

Using OpenZeppelin ERC-721 v5.x, transfers and approvals are completely blocked through the _update() hook:

❌ No transfers

❌ No approvals

❌ No delegation

✔ Only mint and burn permitted

🆓 2. Free Mint (1 active SBT per user)

Each wallet can mint one SBT at a time, but can mint again after burning.

🔁 3. Burn + Remint Support

Users can burn their own SBT:

Burn deletes userTokenId

Burn resets minted[address]

User can mint again immediately

This enables a cycle:

Mint → Burn → Mint → Burn → ...

🔑 4. Random Token IDs

Each SBT receives a fully randomized ID based on:

wallet address

timestamp

block randomness

🧩 5. Metadata With Video Support

The SBT metadata uses:

"animation_url": "https://raw.githubusercontent.com/<user>/<repo>/main/video.mp4"


Enabling animated badges inside wallets and marketplaces.

📁 Project Structure
Mint-SBT-on-ARC-Network/
│
├── MintSBT.sol              # Main SBT Smart Contract (non-transferable)
├── metadata.json            # Token metadata (with animation_url)
└── ArcMintSBT.mp4           # Optional animated badge (video)

📜 Smart Contract Summary

Deployed contract example:

0x9d48f2DD9e14E63f88c2b100C7072c92A9ba8A20

Key Components

mint()
Mints 1 SBT per wallet (unless previously burned).

burn()
Allows the owner to destroy their SBT and mint again.

userTokenId(address)
Returns the token ID owned by a specific address.

setURI()
Owner-only metadata update.

Non-transferable logic
Enforced via _update() override (OZ 5.x standard).

🛠 Deployment Instructions (Remix + ARC Network)
1. Open Remix IDE

https://remix.ethereum.org/

2. Import the contract (MintSBT.sol)
3. Install OpenZeppelin Contracts 5.x inside Remix
npm install @openzeppelin/contracts

4. Compile using Solidity 0.8.20
5. Connect wallet via “Injected Provider”

Select ARC Network Testnet.

6. Deploy and provide your metadata URI:
https://raw.githubusercontent.com/<YOUR_USER>/<YOUR_REPO>/main/metadata.json

7. Use the following functions:
Function	Description
mint()	Mint your SBT
burn()	Burn your SBT (allows remint)
tokenURI()	Returns the metadata
setURI()	Owner updates metadata
userTokenId(wallet)	Retrieve user’s tokenId
🌐 Metadata Example (metadata.json)
{
  "name": "ARC Network Animated SBT",
  "description": "Soulbound Badge minted on ARC Network.",
  "animation_url": "https://raw.githubusercontent.com/<user>/<repo>/main/ArcMintSBT.mp4"
}

🖥 Frontend Integration (Replit)

To integrate with Replit, ensure the frontend:

Reads tokenId via:

const tokenId = await contract.userTokenId(walletAddress);


Uses burn() with no arguments

Uses mint via:

await contract.mint();


Displays error if tokenId == 0

Uses the correct ABI and contract address

🔒 Security Review

This contract is high-security by design:

No funds handled

No external calls

No approvals

No transfer logic

Burn restricted to token owner

Metadata change restricted to contract owner

SBT non-transferable at the protocol level

The contract is suitable for production use.

🧑‍💻 Contributing

Pull requests are welcome!
You may fork and implement:

Badges

Achievements

Game progression

Reputation systems

DAO identity markers

📄 License

MIT License — free to use, modify, and build upon.

⭐ Final Notes

Thank you for exploring ARC Network and experimenting with decentralized identity and SBT models. This project is designed for builders who want a safe and clean foundation for creating on-chain badges and non-transferable identity systems.

Happy building! ⚡
ARC ON.
