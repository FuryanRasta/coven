# Distribution

The distribution module allows you to manage your [Staking Rewards](../concepts/general-concepts.md#staking-rewards).

## Available Subcommands

| Name                                                                                    | Description                                                                                                                                           |
| --------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| [commission](#coven-query-distribution-commission)                                       | Query distribution validator commission                                                                                                               |
| [community-pool](#coven-query-distribution-community-pool)                               | Query the amount of coins in the community pool                                                                                                       |
| [params](#coven-query-distribution-params)                                               | Query distribution params                                                                                                                             |
| [rewards](#coven-query-distribution-rewards)                                             | Query all distribution delegator rewards or rewards from a particular validator                                                                       |
| [slashes](#coven-query-distribution-slashes)                                             | Query distribution validator slashes.                                                                                                                 |
| [validator-outstanding-rewards](#coven-query-distribution-validator-outstanding-rewards) | Query distribution outstanding (un-withdrawn) rewards for a validator and all their delegations                                                       |
| [fund-community-pool](#coven-tx-distribution-fund-community-pool)                        | Funds the community pool with the specified amount                                                                                                    |
| [set-withdraw-addr](#coven-tx-distribution-set-withdraw-addr)                            | Set the withdraw address for rewards associated with a delegator address                                                                              |
| [withdraw-all-rewards](#coven-tx-distribution-withdraw-all-rewards)                      | Withdraw all rewards for a single delegator                                                                                                           |
| [withdraw-rewards](#coven-tx-distribution-withdraw-rewards)                              | Withdraw rewards from a given delegation address,and optionally withdraw validator commission if the delegation address given is a validator operator |

## coven query distribution commission

Query validator commission rewards from delegators to that validator.

```bash
coven query distribution commission [validator] [flags]
```

## coven query distribution community-pool

Query all coins in the community pool which is under Governance control.

```bash
coven query distribution community-pool [flags]
```

## coven query distribution params

Query distribution params.

```bash
 coven query distribution params [flags]
```

## coven query distribution rewards

Query all rewards earned by a delegator, optionally restrict to rewards from a single validator.

```bash
coven query distribution rewards [delegator-addr] [validator-addr] [flags]
```

## coven query distribution slashes

Query all slashes of a validator for a given block range.

```bash
coven query distribution slashes [validator] [start-height] [end-height] [flags]
```

## coven query distribution validator-outstanding-rewards

Query distribution outstanding (un-withdrawn) rewards for a validator and all their delegations.

```bash
coven query distribution validator-outstanding-rewards [validator] [flags]
```

## coven tx distribution fund-community-pool

Funds the community pool with the specified amount.

```bash
coven tx distribution fund-community-pool [amount] [flags]
```

## coven tx distribution set-withdraw-addr

Set the withdraw address for rewards associated with a delegator address.

```bash
coven tx distribution set-withdraw-addr [withdraw-addr] [flags]
```

## coven tx distribution withdraw-all-rewards

Withdraw all rewards for a single delegator.

```bash
coven tx distribution withdraw-all-rewards [flags]
```

## coven tx distribution withdraw-rewards

Withdraw rewards from a given delegation address, and optionally withdraw validator commission if the delegation address given is a validator operator.

```bash
coven tx distribution withdraw-rewards [validator-addr] [flags]
```
