# SwissSwap Core

SwissSwap Core is the on-chain heart of a decentralized exchange. It is a fork of the Uniswap V2 core contracts, written in Solidity, that lets anyone swap one token for another through shared liquidity pools instead of an order book. This repository holds the factory and pair contracts plus a Truffle setup to deploy them to a local test blockchain.

## What it does

- `UniswapV2Factory` creates and keeps track of trading pairs (one pool per token pair).
- `UniswapV2Pair` holds the liquidity of a pair, mints and burns liquidity tokens, and executes swaps with a constant product price rule.
- `UniswapV2ERC20` is the liquidity provider token.
- `Token1` (TK1) and `Token2` (TK2) are simple ERC20 tokens used as a test pair on local networks.
- The deployment script deploys the factory, deploys the two test tokens, and creates a pair for them.

## Tech stack

- Solidity 0.5.16
- Truffle for compiling and deploying
- Ganache for a local blockchain
- OpenZeppelin Contracts 2.5.1 (committed under `node_modules/`)

## Run it locally

You need Node.js and npm. Installing Truffle and Ganache needs access to the npm registry.

1. Install the tools: `npm install -g truffle ganache-cli`
2. Start a local blockchain in one terminal: `ganache-cli`
3. In another terminal, in this folder, deploy: `truffle migrate --reset`

This compiles the contracts with solc 0.5.16 and deploys the factory, the two test tokens, and one pair. The first Ganache account becomes the fee setter of the factory.

Precompiled contract artifacts are already in `build/contracts/`.

## Full SwissSwap stack

This repository is only the core. The related pieces live in separate repositories:

- Router (Solidity 0.6.6): https://github.com/maxawad/SwissSwap-Periphery. Deploy it with `cd ../periphery && truffle migrate --reset`.
- Migrators (move liquidity tokens from Uniswap): https://github.com/maxawad/SwissSwap-Migrators. Deploy it with `cd ../migrators && truffle migrate --reset`.

## Status

Prototype. It deploys to a local development chain. It has no automated tests, no front end, and no deployment to a public network. The mainnet branch of the migration script has empty token addresses and must be filled in before use. The test tokens have no mint function, so they hold no supply as written.

## Credits

Based on the Uniswap V2 core contracts by Uniswap (https://github.com/Uniswap/uniswap-v2-core), which are released under GPL-3.0. The token contracts use OpenZeppelin Contracts.
