# 🚀 RaydiumVolumeBot-v2-using-jupiter

![Solana](https://img.shields.io/badge/Solana-362D59?style=for-the-badge&logo=solana&logoColor=white)
![Jupiter](https://img.shields.io/badge/Jupiter-FF6B35?style=for-the-badge&logo=jupiter&logoColor=white)
![Jito](https://img.shields.io/badge/Jito-00A86B?style=for-the-badge&logo=jito&logoColor=white)

This bot is designed to automate the distribution of SOL to multiple wallets and execute simultaneous buy and sell swap transactions on the Raydium DEX. By integrating Jito Bundle, the bot optimizes all transactions, ensuring maximum performance and efficiency.

## 📚 Table of Contents

- [Features](#-features)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Usage](#-usage)
- [Code Explanation](#-code-explanation)
- [Best Practices](#-best-practices)
- [Contributing](#-contributing)
- [License](#-license)
- [💖 Support the Developer](#-support-the-developer)

## 🌟 Features

- **Automated Distribution**: Efficiently distributes SOL across multiple wallets.
- **Endless Swaps: Performs** simultaneous buy and sell transactions seamlessly.
- **Optimized Performance**: Leverages Jito Bundle for transaction bundling and enhanced speed.
- **Market Impact**: Helps increase the token's market holders through active volume generation.
- **Powered by Solana**: Utilizes Solana’s high-speed, low-cost blockchain for optimal performance.
- Jito bundles for MEV protection
- Comprehensive error handling and logging

## 🛠 Prerequisites

- Node.js (v18 or later)
- npm (v6 or later)
- A Solana wallet with SOL for transaction fees
- 0.01 SOL in wallet for swap

## 📦 Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/black-rustx/RaydiumVolumeBot-v2.git
   cd RaydiumVolumeBot-v2
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Create a .env file in the project root and add your Solana RPC URL and wallet private key:
   ```
   RPC_ENDPOINT=https://your-rpc-url-here
   PRIVATE_KEY=[your,private,keypair,array,here]
   ```
   We have included an example .env file in the repository for your convenience.

## 🚀 Usage

Run the script with:

```bash
npm start
```

This will execute a sample swap of 0.01 SOL to USDC. Modify the `main` function in `index.js` to customize the swap parameters. Ensure you have the correct token addresses and amounts for your swap in the wallet for the swap to execute.

## 💻 Code Explanation

The `index.js` file contains the following key components:

1. **Setup and Imports**:

   - The script imports essential libraries and modules for interacting with Solana, including @solana/web3.js, @solana/spl-token, and custom utility functions from utils and executor modules.
   - Constants like RPC endpoints, intervals, and token mint details are imported from a constants file.

2. **Solana Connection and Main Wallet Initialization**:

   - **`solanaConnection`**: Establishes a connection to the Solana blockchain using an RPC endpoint with WebSocket support for real-time updates.
   - **`mainKp`**: Initializes the main wallet using a private key decoded from `base58`.

3. **Key Functions**:

   - **`distributeSol`**: Distributes SOL from the main wallet to multiple newly generated wallets, ensuring each has enough balance for subsequent operations.
   - **`buy`**: Executes buy transactions for tokens using Jupiter's aggregator for efficient swaps.Dynamically adjusts the buy amount based on wallet SOL balance and configured percentages (BUY_UPPER_PERCENT and BUY_LOWER_PERCENT). Utilizes Jito Bundle integration for optimized transaction execution when enabled.
   - **`sell`**: Sells tokens held in associated token accounts by leveraging Jupiter's swap functionality. Handles token balance checks and ensures the transaction is completed successfully.

4. **Wallet Transfer**:

   - Transfers remaining SOL to a newly generated wallet after each buy-and-sell cycle to reset the operation loop.

5. **Main Logic**:

   The main function orchestrates the entire bot process:

   - Prints bot settings, wallet balance, and other configurations..
   - Distributes SOL to sub-wallets for parallel operations
   - Executes an endless cycle of buying, selling, and redistributing SOL

6. **Optimization Features**:

   - **`Jito Bundle Integration`**: Enhances transaction bundling for improved efficiency and ensures optimal MEV protection.
   - **`Compute Budget Instructions`**: Adds compute unit limits and custom unit prices to transactions, improving performance on the Solana network.

7. **Error Handling and Logging**:

   - Comprehensive error handling ensures the bot continues or retries failed transactions without interrupting the workflow.
   - Logs detailed messages to track operations, including transaction links for monitoring on Solscan.

8. **Example Usage**:
   - Simply run the script to start the bot. It continuously performs buy-and-sell operations on the Raydium DEX and redistributes SOL across wallets, leveraging Solana's efficiency and Jupiter's aggregation.

## Transaction Simulation

To ensure accurate compute unit allocation, we simulate the transaction before sending it. This process:

1. Constructs a transaction with all necessary instructions.
2. Simulates the transaction using `connection.simulateTransaction()`.
3. Retrieves the actual compute units consumed.
4. Adds a 20% buffer to the consumed units for safety.

This approach helps prevent transaction failures due to insufficient compute budget.

## 🏆 Best Practices

This volume bot implements several best practices:

- **Versioned Transactions**: Utilizes the latest transaction format for improved efficiency.
- **Compute Budget Optimization**: Uses transaction simulation to set appropriate compute units.
- **Dynamic Priority Fees**: Implements adaptive priority fees based on recent network activity.
- **Address Lookup Tables**: Leverages ALTs to reduce transaction size and cost.
- **MEV Protection**: Integrates with Jito for protection against MEV (Miner Extractable Value).
- **Error Handling**: Implements comprehensive error catching and logging for easier debugging.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 💖 Support the Developer

If you found this bot helpful and would like to support the development of more resources like this, consider tipping! Your contributions help keep the project alive and thriving.

**Solana Wallet Address:** `jaDpUj6FzoQFtA5hCcgDwqnCFqHFcZKDSz71ke9zHZA`
**ETH Wallet Address:** `0x96aca495621E93c884A8cb054bB823Bc273C29Bb`

Thank you for your support!

Happy swapping! If you have any questions or run into issues, please open an issue in the GitHub repository.

## 📞 Author

Telegram: [@g0drlc](https://t.me/da1asin)
