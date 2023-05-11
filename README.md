# BAS
BSC Application Sidechain (BAS) is EVM-compatible chain, that helps developers to build BSC-based apps.

## Building the source

Building `bas` requires both a Go (version 1.14 or later) and a C compiler. You can install
them using your favourite package manager. Once the dependencies are installed, run

```shell
$ git clone https://github.com/Ankr-network/bas-template-bsc.git
$ git checkout v1.0.3
$ make geth
```
The build output is ```build/bin/geth``` executable.

## Running `bas`

Going through all the possible command line flags is out of scope here,
but we've enumerated a few common parameter combos to get you up to speed quickly
on how you can run your own `bas` instance.

### Launching a network

You will need a genesis file to join a network, which may be found in https://raw.githubusercontent.com/Ankr-network/bas-mainnet-genesis/main/metaapes-mainnet/genesis.json

Launching `mainnet` node for network specified by the genesis file:

```shell
$ geth --datadir /data init genesis.json
$ geth --networkid 17243 --datadir /data --genesis genesis.json
```

## Dev

### Running testnet

The network is specified only by its genesis file, so running a testnet node is equivalent to
using a testnet genesis file instead of a mainnet genesis file:
```shell
$ wget https://raw.githubusercontent.com/Ankr-network/bas-mainnet-genesis/main/metaapes-testnet/genesis.json
$ geth --datadir /data init genesis.json
$ geth --datadir /data --genesis genesis.json
```

### Running archive

```shell
$ geth --gcmode=archive --syncmode=full --networkid=17243 --txpool.gasfreecontracts="0x5e749a7D95E938fF304Cf3559CFbD18bBf2E6950" --datadir /data --genesis genesis.json
```


## Parameters

Run `geth --help` to get all parameters

|    Command    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| :-----------: |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **`networkid`**   | mainnet - 17243                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|   `gcmode`    | Blockchain garbage collection mode ("full", "archive") (default: "full")                                                                                                                                                                                                                                                                                                                                                                                                                         |
|   `syncmode`    | Blockchain sync mode ("fast", "full", "snap" or "light") (default: fast)                                                                                                                                                                                                                                                                                                                                                                                                                         |
|   `txpool.gasfreecontracts`    | List with gas free recipients                                                                                                                                                                                                                                                                                                                                                                                                                         |




