# NFT

`NFT` provides the ability to digitize assets. Through this module, each off-chain asset will be modeled as a unique on-chain nft.

## Available Commands

| Name                                          | Description                                                                                         |
| --------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [issue](#coven-tx-nft-issue)                   | Specify the nft Denom (nft classification) and metadata JSON Schema to issue nft.                   |
| [transfer-denom](#coven-tx-nft-transfer-denom) | The owner of the NFT classification can transfer the ownership of the NFT classification to others. |
| [mint](#coven-tx-nft-mint)                     | Additional issuance (create) of specific nft of this type can be made.                              |
| [edit](#coven-tx-nft-edit)                     | The metadata of the specified nft can be updated.                                                   |
| [transfer](#coven-tx-nft-transfer)             | Transfer designated nft.                                                                            |
| [burn](#coven-tx-nft-burn)                     | Destroy the created nft.                                                                            |
| [supply](#coven-query-nft-supply)              | Query the total amount of nft according to Denom; accept the optional owner parameter.              |
| [owner](#coven-query-nft-owner)                | Query all nft owned by an account; you can specify the Denom parameter.                             |
| [collection](#coven-query-nft-collection)      | Query all nft according to Denom.                                                                   |
| [denom](#coven-query-nft-denom)                | Query nft denom information based on Denom.                                                         |
| [denoms](#coven-query-nft-denoms)              | Query the total amount of nft according to Denom; accept the optional owner parameter.              |
| [token](#coven-query-nft-token)                | Query specific nft based on Denom and ID.                                                           |

## coven tx nft issue

Specify the nft Denom (nft classification) and metadata JSON Schema to issue nft.

```bash
coven tx nft issue [denom-id] [flags]
```

**Flags:**

| Name, shorthand     | Required | Default                                                                                                                                                                                                                     | Description |
| ------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| --name              |          | The name of the denom                                                                                                                                                                                                       |             |
| --uri               |          | The uri of the denom                                                                                                                                                                                                        |             |
| --data              |          | Off-chain metadata for supplementation (JSON object)                                                                                                                                                                        |             |
| --schema            |          | Denom data structure definition                                                                                                                                                                                             |             |
| --symbol            |          | The symbol of the denom                                                                                                                                                                                                     |             |
| --mint-restricted   |          | This field indicates whether there are restrictions on the issuance of NFTs under this classification, true means that only Denom owners can issue NFTs under this classification, false means anyone can                   |             |
| --update-restricted |          | This field indicates whether there are restrictions on updating NFTs under this classification, true means that no one under this classification can update the NFT, false means that only the owner of this NFT can update |             |

## coven tx nft transfer-denom

The owner of the NFT classification can transfer the ownership of the NFT classification to others.

```bash
coven tx nft transfer-denom [recipient] [denom-id]
```

## coven tx nft mint

Additional issuance (create) of specific nft of this type can be made.  

```bash
coven tx nft mint [denomID] [tokenID] [flags]
```

**Flags:**

| Name, shorthand | Required | Default                     | Description |
| --------------- | -------- | --------------------------- | ----------- |
| --uri           |          | URI of off-chain token data |             |
| --recipient     |          | Receiver of the nft         |             |
| --name          |          | The name of nft             |             |

## coven tx nft edit

The metadata of the specified nft can be updated.

```bash
coven tx nft edit [denomID] [tokenID] [flags]
```

**Flags:**

| Name, shorthand | Required | Default                     | Description |
| --------------- | -------- | --------------------------- | ----------- |
| --uri           |          | URI of off-chain token data |             |
| --name          |          | The name of nft             |             |

## coven tx nft transfer

Transfer designated nft.

```bash
coven tx nft transfer [recipient] [denomID] [tokenID] [flags]
```

**Flags:**

| Name, shorthand | Required | Default                     | Description |
| --------------- | -------- | --------------------------- | ----------- |
| --uri           |          | URI of off-chain token data |             |
| --name          |          | The name of nft             |             |

## coven tx nft burn

Destroy the created nft.

```bash
coven tx nft burn [denomID] [tokenID] [flags]
```

## coven query nft

Query nft

### coven query nft supply

```bash
coven query nft supply [denomID]
coven query nft supply [denomID] --owner=<owner address>
```

### coven query nft owner

```bash
coven query nft owner [owner address]
coven query nft owner [owner address] --denom=<denomID>
```

### coven query nft collection

```bash
coven query nft collection [denomID]
```

### coven query nft denom

```bash
coven query nft denom [denomID]
```

### coven query nft denoms

```bash
coven query nft denoms
```

### coven query nft token

```bash
coven query nft token [denomID] [tokenID]
```
