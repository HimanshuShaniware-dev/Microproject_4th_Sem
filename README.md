# Microproject_4th_Sem

# Secure Social Recovery Wallet

## What Have We Built So Far?

The core of the project — the smart contract — is already written and tested. It is written in Solidity, the programming language used specifically for writing smart contracts on Ethereum. When the wallet is created, an owner is set along with a list of trusted guardians and a threshold — for example, 2 out of 3 guardians must agree to restore access. If the owner loses their wallet, guardians vote for a new owner address. The moment enough guardians have voted, ownership transfers automatically. No guardian can vote twice, no one outside the guardian list can interfere, and the whole process is transparent and tamper-proof.

We ran 6 automated tests against this contract and all of them passed. We also have a MetaMask wallet set up on the Sepolia test network (a fake Ethereum blockchain used for development) with test ETH ready for deployment.

---

## The Full System We Are Building

The smart contract alone is just the backend logic. To make this useful for real people, we need a complete web application on top of it.

**Frontend** is built with React. Users will connect their MetaMask wallet, see their dashboard, add or remove guardians, and trigger recovery requests through a clean web interface. The frontend talks to the blockchain directly through the user's MetaMask wallet.

**Backend** is built with Python using FastAPI. It handles user sessions, authentication, and guardian notifications. Login works without passwords — users sign a message with their wallet to prove they own it, using a method called Sign-In With Ethereum (SIWE).

**Database** uses PostgreSQL to store user preferences, guardian contact details, and recovery history off-chain. The blockchain stores the rules; the database stores the context.

**Smart Contract** is what we have already built. It lives on Ethereum, enforces all wallet rules, and cannot be tampered with by anyone — including us.
