# USDC Transfer on EVM Testnets using Circle & Viem

A beginner-friendly TypeScript application for sending **USDC** between EVM-compatible wallets using **Circle's USDC contracts** and the **Viem** library.

This project demonstrates how to securely transfer USDC across supported EVM testnets while teaching the fundamentals of blockchain transactions, wallet management, and ERC-20 token interactions.

---

# Overview

This project allows you to:

* Load wallet credentials securely using environment variables.
* Connect to multiple supported EVM testnets.
* Check your USDC balance before sending.
* Transfer USDC to another wallet.
* Wait for transaction confirmation.
* View the transaction on the appropriate blockchain explorer.

Whether you're a beginner exploring blockchain development or an experienced developer looking for a simple USDC transfer example, this repository provides a solid foundation.

---

# Project Structure

```text
transfer-usdc-evm/
│
├── node_modules/
├── .env
├── .gitignore
├── index.ts
├── package.json
├── package-lock.json
└── tsconfig.json
```

---

# Prerequisites

Before running this project, ensure you have the following installed:

* Node.js (v20 or later recommended)
* npm
* Visual Studio Code (recommended)
* Git (optional)
* A wallet containing testnet USDC
* Testnet gas tokens for the selected network

Verify your installation:

```bash
node -v
npm -v
```

---

# Installation

## Step 1 — Create the Project

### Windows (PowerShell)

```powershell
mkdir transfer-usdc-evm
cd transfer-usdc-evm
```

### macOS / Linux

```bash
mkdir transfer-usdc-evm
cd transfer-usdc-evm
```

---

## Step 2 — Initialize the Project

```bash
npm init -y
```

---

## Step 3 — Install Dependencies

Install runtime dependencies:

```bash
npm install viem dotenv
```

Install development dependencies:

```bash
npm install -D typescript tsx @types/node
```

---

## Step 4 — Generate TypeScript Configuration

```bash
npx tsc --init
```

---

## Step 5 — Create Required Files

Create the following files:

```text
.env
index.ts
.gitignore
```

### Windows PowerShell

```powershell
New-Item .env -ItemType File
New-Item index.ts -ItemType File
New-Item .gitignore -ItemType File
```

---

## Step 6 — Configure package.json

Replace your `package.json` with:

```json
{
  "name": "transfer-usdc-evm",
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "start": "tsx index.ts"
  },
  "dependencies": {
    "dotenv": "^17.0.0",
    "viem": "^2.53.1"
  },
  "devDependencies": {
    "@types/node": "^26.0.1",
    "tsx": "^4.22.4",
    "typescript": "^6.0.3"
  }
}
```

Install packages:

```bash
npm install
```

---

# Environment Variables

Create a `.env` file in the project root.

```env
PRIVATE_KEY=0xYOUR_PRIVATE_KEY
RECIPIENT_ADDRESS=0xYOUR_RECIPIENT_ADDRESS
```

## Important

Your private key must:

* Begin with `0x`
* Contain exactly **64 hexadecimal characters** after `0x`
* Never be shared publicly
* Never be committed to GitHub

---

# .gitignore

Create a `.gitignore` file:

```gitignore
node_modules
.env
```

This prevents sensitive files from being uploaded to GitHub.

---

# Running the Application

Start the application:

```bash
npm start
```

You will see a list of supported testnets:

```text
Select a chain for your USDC transfer:

1. Arc Testnet
2. Arbitrum Sepolia
3. Avalanche Fuji
...
```

Enter the corresponding number for your desired network.

Example:

```text
Enter a number: 1
```

The application will then:

1. Connect to the selected blockchain.
2. Load your wallet.
3. Display your USDC balance.
4. Transfer USDC to the recipient.
5. Wait for transaction confirmation.
6. Display the transaction hash.
7. Provide a blockchain explorer URL.

Example output:

```text
Sender: 0x...
Recipient: 0x...

Balance: 160.67131 USDC

Transaction submitted.

Tx Hash:
0x...

Transfer confirmed!
```

---

# How It Works

The application follows these steps:

1. Loads environment variables from `.env`.
2. Validates the private key and recipient address.
3. Converts the private key into a wallet account.
4. Connects to the selected blockchain.
5. Reads the sender's USDC balance.
6. Executes an ERC-20 `transfer()` transaction.
7. Waits until the transaction is confirmed.
8. Displays the transaction details.

---

# Key Concepts

## `createPublicClient`

Used to **read** blockchain data.

Examples:

* Wallet balances
* Block numbers
* Smart contract state

---

## `createWalletClient`

Used to **sign and send** blockchain transactions.

Examples:

* Sending USDC
* Approving ERC-20 tokens
* Calling smart contract functions

---

## `privateKeyToAccount`

Converts your private key into an account that can sign blockchain transactions.

---

## `balanceOf()`

Reads the sender's USDC balance from the USDC smart contract.

---

## `transfer()`

Transfers USDC from the sender wallet to the recipient wallet.

---

# Troubleshooting

## Missing script: "start"

Ensure `package.json` contains:

```json
"scripts": {
  "start": "tsx index.ts"
}
```

---

## `touch` is not recognized

Windows PowerShell does not support `touch`.

Use:

```powershell
New-Item index.ts -ItemType File
```

---

## PRIVATE_KEY must be a 0x-prefixed 32-byte hex string

Ensure your private key:

* Starts with `0x`
* Has exactly 66 characters (including `0x`)
* Is your private key, **not** your wallet address or recovery phrase

---

## PRIVATE_KEY is undefined

Solution:

* Install `dotenv`
* Ensure `import "dotenv/config";` is the first line in `index.ts`
* Verify `.env` is located in the project root

---

## Cannot find module 'dotenv'

Install dotenv:

```bash
npm install dotenv
```

---

# Security Best Practices

* Never expose your private key.
* Never upload `.env` to GitHub.
* Always test on testnets before using mainnet.
* Use separate wallets for development and production.
* Rotate your private key immediately if it is accidentally exposed.

---

# Future Improvements

You can extend this project by adding:

* Custom transfer amounts entered at runtime.
* A React or Next.js frontend.
* WalletConnect integration.
* Support for multiple recipients.
* Transaction history.
* Balance caching.
* Mainnet support.
* Circle API integration.
* QR code scanning for recipient addresses.

---

# Learning Resources

* Circle Developer Documentation
* Viem Documentation
* TypeScript Documentation
* Ethereum ERC-20 Token Standard

---

# Contributing

Contributions are welcome.

If you'd like to improve this project:

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Open a Pull Request.

---

# License

This project is provided for educational purposes.

Feel free to modify, reuse, and extend it for your own applications.

---

# Acknowledgements

This project is inspired by the official Circle Developer Quickstart for transferring USDC on EVM-compatible networks and demonstrates how to interact with ERC-20 USDC contracts using the Viem library in a clean, beginner-friendly TypeScript application.
