# Token

Token module allows you to manage assets on COVEN Hub

## Available Commands

| Name                                       | Description                                |
| ------------------------------------------ | ------------------------------------------ |
| [issue](#coven-tx-token-issue)              | Issue a new token                          |
| [edit](#coven-tx-token-edit)                | Edit an existing token                     |
| [transfer](#coven-tx-token-transfer)        | Transfer the ownership of a token          |
| [mint](#coven-tx-token-mint)                | Mint tokens to a specified address         |
| [burn](#coven-tx-token-burn)                | Burn some tokens                           |
| [token](#coven-query-token-token)           | Query a token by symbol                    |
| [tokens](#coven-query-token-tokens)         | Query tokens by owner                      |
| [fee](#coven-query-token-fee)               | Query the token related fees               |
| [params](#coven-query-token-params)         | Query the token related params             |
| [total-burn](#coven-query-token-total-burn) | Query the total amount of all burn tokens. |

## coven tx token issue

Issue a new token

```bash
coven tx token issue [flags]
```

**Flags:**

| Name, shorthand  | Type    | Required | Default       | Description                                                                                                                    |
| ---------------- | ------- | -------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| --name           | string  | Yes      |               | Name of the newly issued token, limited to 32 unicode characters, e.g. "COVEN Network"                                          |
| --symbol         | string  | Yes      |               | The symbol of the token, length between 3 and 8, alphanumeric characters beginning with alpha, case insensitive                |
| --initial-supply | uint64  | Yes      |               | The initial supply of this token. The amount before boosting should not exceed 100 billion.                                    |
| --max-supply     | uint64  |          | 1000000000000 | The hard cap of this token, total supply can not exceed max supply. The amount before boosting should not exceed 1000 billion. |
| --min-unit       | string  |          |               | The alias of minimum uint                                                                                                      |
| --scale          | uint8   | Yes      |               | A token can have a maximum of 18 digits of decimal                                                                             |
| --mintable       | boolean |          | false         | Whether this token could be minted(increased) after the initial issuing                                                        |

### Issue a token

```bash
coven tx token issue \
    --name="Kitty Token" \
    --symbol="kitty" \
    --min-unit="kitty" \
    --scale=0 \
    --initial-supply=100000000000 \
    --max-supply=1000000000000 \
    --mintable=true \
    --from=<key-name> \
    --chain-id=<chain-id> \
    --fees=<fee>
```

### Send tokens

You can send any tokens you have just like [sending coven](./bank.md#coven-tx-bank-send)

#### Send tokens

```bash
coven tx bank send [from_key_or_address] [to_address] [amount] [flags]
```

## coven tx token edit

Edit an existing token

```bash
coven tx token edit [symbol] [flags]
```

**Flags:**

| Name         | Type   | Required | Default | Description                                       |
| ------------ | ------ | -------- | ------- | ------------------------------------------------- |
| --name       | string |          |         | The token name, e.g. COVEN Network                 |
| --max-supply | uint64 |          | 0       | The max supply of the token                       |
| --mintable   | bool   |          | false   | Whether the token can be minted, default to false |

`max-supply` should not be less than the current total supply

### Edit Token

```bash
coven tx token edit <symbol> --name="Cat Token" --max-supply=100000000000 --mintable=true --from=<key-name> --chain-id=<chain-id> --fees=<fee>
```

## coven tx token transfer

Transfer the ownership of a token

```bash
coven tx token transfer [symbol] [flags]
```

**Flags:**

| Name | Type   | Required | Default | Description           |
| ---- | ------ | -------- | ------- | --------------------- |
| --to | string | Yes      |         | The new owner address |

### Transfer Token Owner

```bash
coven tx token transfer <symbol> --to=<to> --from=<key-name> --chain-id=<chain-id> --fees=<fee>
```

## coven tx token mint

Mint tokens to a specified address

```bash
coven tx token mint [symbol] [flags]
```

**Flags:**

| Name     | Type   | Required | Default | Description                                                             |
| -------- | ------ | -------- | ------- | ----------------------------------------------------------------------- |
| --to     | string |          |         | Address to which the token will be minted, default to the owner address |
| --amount | uint64 | Yes      | 0       | Amount of the tokens to be minted                                       |

### Mint Token

```bash
coven tx token mint <symbol> --amount=<amount> --to=<to> --from=<key-name> --chain-id=<chain-id> --fees=<fee>
```

## coven tx token burn

Burn some tokens

```bash
coven tx token burn [symbol] [flags]
```

**Flags:**

| Name     | Type   | Required | Default | Description                   |
| -------- | ------ | -------- | ------- | ----------------------------- |
| --amount | uint64 | Yes      | 0       | Amount of the tokens to burnt |

### Burn Token

```bash
coven tx token burn <symbol> --amount=<amount> --from=<key-name> --chain-id=<chain-id> --fees=<fee>
```

## coven query token token

Query a token by symbol

```bash
coven query token token [denom] [flags]
```

### Query a token

```bash
coven query token token <denom>
```

## coven query token tokens

Query tokens by the owner which is optional

```bash
coven query token tokens [owner] [flags]
```

### Query all tokens

```bash
coven query token tokens
```

### Query tokens with the specified owner

```bash
coven query token tokens <owner>
```

## coven query token fee

Query the token related fees, including token issuance and minting

```bash
coven query token fee [symbol] [flags]
```

### Query fees of issuing and minting a token

```bash
coven query token fee kitty
```

## coven query token params

Query token module params

```bash
coven query token params [flags]
```

### Query token module params

```bash
coven query token params
```

## coven query token total-burn

Query the total amount of all burn tokens

```bash
coven query token total-burn [flags]
```

### Query the total amount of all burn tokens

```bash
coven query token total-burn
```
