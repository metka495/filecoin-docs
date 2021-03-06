---
title: Joining a network
sidebarDepth: 0
description: Learn how to join one of the various Filecoin testnets.
---

# Joining a network

Once a Lotus node has been initialised on the appropriate [Filecoin network option](https://docs.filecoin.io/how-to/networks/), this section provides setup instructions for syncing the chain, creating a wallet, checking balances and sending FIL to other addresses.

### Note: Using the Lotus Node from China

If you are trying to use `lotus` from China, set this **environment variable** on your machine:

```sh
IPFS_GATEWAY="https://proof-parameters.s3.cn-south-1.jdcloud-oss.com/ipfs/"
```

## Get started

Start the **daemon** using the default configuration in `./build`:

```sh
lotus daemon
```

In another terminal window, check your connection with peers:

```sh
lotus net peers | wc -l
```

 > **NOTICE:** Make sure there is a reasonable "open files limit" set on the machine, such as 10000. If you're seeing a lower value, such as 256 (default on macOS), read our [troubleshooting instructions](https://docs.filecoin.io/mine/mining-troubleshooting/) on how to update it prior to starting the Lotus daemon.

## Chain sync

While the daemon is running, the next requirement is to sync the chain. Run the command below to view the chain sync progress. To see current chain height, visit the appropriate network statistics page.

```sh
lotus sync wait
```

- This step will take anywhere between a few hours to a couple of days.
- You will be able to perform Lotus operations after it is finished.

## Create your first address

Initialize a new wallet:

```sh
lotus wallet new
```

Sometimes your operating system may limit file name length to under 150 characters. You need to use a file system that supports long filenames.

Here is an example of the response:

```sh
t1aswwvjsae63tcrniz6x5ykvsuotlgkvlulnqpsi
```

- Use an appropriate faucet to acquire FIL
- Paste the address you created
- Press the send button

## Check wallet address balance

Wallet balances in Lotus are in **FIL**, the smallest denomination of FIL is an **attoFil**, where 1 attoFil = 10^-18 FIL.

```sh
lotus wallet balance <YOUR_NEW_ADDRESS>
```

You will not see any attoFIL in your wallet if your **chain** is not fully synced.

## Send FIL to another wallet

To send FIL to another wallet from your default account, use this command:

```
lotus send <target> <amount>
```

## Configure your node's connectivity

To effectively accept incoming storage & retrieval deals, your Lotus node needs to be accessible to other nodes on the network. To improve your connectivity, be sure to: 

- [Set the multiaddresses for you miner to listen on](https://docs.filecoin.io/mine/connectivity/#setting-multiaddresses)
- [Maintain a healthy peer count](https://docs.filecoin.io/mine/connectivity/#checking-peer-count)
- [Enable port forwarding](https://docs.filecoin.io/mine/connectivity/#port-forwarding)
- [Configure your public IP address and port](https://docs.filecoin.io/mine/connectivity/#setting-a-public-ip-address)

## Monitor the dashboard

To see the latest network activity, including **chain block height**, **block height**, **blocktime**, **total network power**, largest **block producer miner**, check out the network's monitoring dashboard.
