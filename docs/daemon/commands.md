---
order: 2
---

# Commands

## Introduction

COVEN Daemon Commands allow you to init, start, reset a node, or generate a genesis file, etc.

You can get familiar with these commands by creating a [Local Testnet](local-testnet.md).

## Usage

```bash
coven <command>
```

## Available Commands

| Name                                                             | Description                                                                                                     |
| ---------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| [init](local-testnet.md#coven-init)                               | Initialize private validator, p2p, genesis, and application configuration files                                 |
| [add-genesis-account](local-testnet.md#coven-add-genesis-account) | Add genesis account to genesis.json                                                                             |
| [gentx](local-testnet.md#coven-gentx)                             | Generate a genesis tx carrying a self delegation                                                                |
| [collect-gentxs](local-testnet.md#coven-collect-gentxs)           | Collect genesis txs and output a genesis.json file                                                              |
| [start](local-testnet.md#coven-start)                             | Run the full node                                                                                               |
| [unsafe-reset-all](local-testnet.md#coven-unsafe-reset-all)       | Resets the blockchain database, removes address book files, and resets priv_validator.json to the genesis state |
| [tendermint](local-testnet.md#coven-tendermint)                   | Tendermint subcommands                                                                                          |
| [testnet](local-testnet.md#build-and-init)                       | Initialize files for a Covenhub testnet                                                                          |
| [reset](local-testnet.md#coven-reset)                             | Reset app state to the specified height                                                                         |
| [export](export.md)                                              | Export state to JSON                                                                                            |
| version                                                          | Show executable binary version                                                                                  |

## Global Flags

| Name,shorthand | Default      | Description                                        | Required | Type   |
| -------------- | ------------ | -------------------------------------------------- | -------- | ------ |
| -h, --help     |              | Help for coven                                      |          |        |
| --home         | /$HOME/.coven | Directory for config and data                      |          | String |
| --log_level    | \*:info      | Log level (default "main:info,state:info,*:error") |          | String |
| --trace        |              | Print out full stack trace on errors               |          |        |
