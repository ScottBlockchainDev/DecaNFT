# SpheraWorld

## Deploy Setup

Add a `.env` file (to the root project directory) with your `MNEMONIC="your mnemonic"` and fund your wallet in order to deploy!

1. Deploy two contracts:

```shell
npx hardhat --network ethereum-sepolia deploy --tags SpheraKitBag
npx hardhat --network ethereum-sepolia deploy --tags SpheraHead
npx hardhat --network blast-testnet deploy --tags SpheraHead
```

2. Set the "trusted remotes", so each contract can send & receive messages from one another, and **only** one another.

```shell
npx hardhat --network ethereum-sepolia setTrustedRemote --target-network blast-testnet --contract SpheraHead
npx hardhat --network blast-testnet setTrustedRemote --target-network ethereum-sepolia --contract SpheraHead
```

3. Set the min gas required on the destination

```shell
npx hardhat --network ethereum-sepolia setMinDstGas --target-network blast-testnet --contract SpheraHead --packet-type 1 --min-gas 100000
npx hardhat --network blast-testnet setMinDstGas --target-network ethereum-sepolia --contract SpheraHead --packet-type 1 --min-gas 100000
```

4. Send ONFT across chains

```shell
npx hardhat --network ethereum-sepolia SpheraHeadSend --target-network blast-testnet --token-id 2654 --contract SpheraHead
npx hardhat --network blast-testnet SpheraHeadSend --target-network ethereum-sepolia --token-id 200 --contract SpheraHead
```

## Deployed Addresses

SpheraKitBag: Ethereum Sepolia, 0xfDb49a1F69dbbd67D3d5902C376F3b812f299594

SpheraHead: Blast Testnet, 0x1a832804f4A12F7E83Fc1fd115b0165fdB5c4916

SpheraHead: Ethereum Sepolia, 0xCFb70DF7346e8f991A4881380adb6D2c22d19F11
