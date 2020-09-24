###How to:

##Start local net:
npm i -g ganache-cli
ganache-cli

## Deploy Core Smart Contract (UniSwap Factory):
> Sol=0.5.16

truffle migrate --reset



## Deploy Periphery Smart Contract (UniSwap Router):
>Sol=0.6.6

cd ../periphery
truffle migrate --reset

https://github.com/maxawad/SwissSwap-Periphery

## Deploy Migrators Smart Contract (Liquidity Provider UNISWAP Tokens):
cd ../migrators
truffle migrate --reset
