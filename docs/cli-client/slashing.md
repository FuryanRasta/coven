# Slashing

Slashing module can unjail validator previously jailed for downtime

## Available Commands

| Name                                                | Description                                     |
| --------------------------------------------------- | ----------------------------------------------- |
| [unjail](#coven-tx-slashing-unjail)                  | Unjail validator previously jailed for downtime |
| [params](#coven-query-slashing-params)               | Query the current slashing parameters           |
| [signing-info](#coven-query-slashing-signing-info)   | Query a validator's signing information         |
| [signing-infos](#coven-query-slashing-signing-infos) | Query signing information of all validators     |

## coven tx slashing unjail

Unjail validator previously jailed for downtime.

```bash
coven tx slashing unjail [flags]
```

## coven query slashing params

Query the current slashing parameters.

```bash
coven query slashing params  [flags]
```

## coven query slashing signing-info

Query a validator's signing information.

```bash
coven query slashing signing-info [validator-conspub] [flags]
```

## coven query slashing signing-infos

Query signing information of all validators.

```bash
coven query slashing signing-infos [flags]
```
