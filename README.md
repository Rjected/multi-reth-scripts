# multi-reth-scripts
Scripts for running reth on multiple testnets on the same machine.

This runs reth on the following networks:

| Network | Datadir           | RPC port |
| ------- | ----------------- | -------- |
| Mainnet | /mnt/reth/mainnet | 8545     |
| Sepolia | /mnt/reth/sepolia | 8546     |
| Goerli  | /mnt/reth/goerli  | 8547     |

`/mnt` should be large since this runs 3 archive nodes at once.

Logs are also stored, for reth and lighthouse, under `/mnt`.

This consists of the following scripts:
 - `start-reth`, which starts mainnet reth
 - `start-lighthouse`, which starts mainnet lighthouse
 - `start-reth-sepolia`, which starts sepolia reth
 - `start-lighthouse-sepolia`, which starts sepolia lighthouse
 - `start-reth-goerli`, which starts goerli reth
 - `start-lighthouse-goerli`, which starts goerli lighthouse

The lighthouse nodes are currently started without checkpoint sync. When running for the first time, reth scripts should be started before lighthouse scripts, because the reth script will initialize the datadir and JWT for lighthouse.
Reth logs are run with the `info,rpc=trace,rpc::engine=trace` filter, meaning engine events and RPC queries are logged + persisted.
