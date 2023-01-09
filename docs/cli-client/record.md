# Record

Record module allows you to manage record on COVEN Hub

## Available Commands

| Name                                | Description        |
| ----------------------------------- | ------------------ |
| [create](#coven-tx-record-create)    | Create a record    |
| [record](#coven-query-record-record) | Query record by id |

## coven tx record create

Create a record

```bash
coven tx record create [digest] [digest-algo] [flags]
```

**Flags:**

| Name, shorthand | Type   | Required | Default | Description                                |
| --------------- | ------ | -------- | ------- | ------------------------------------------ |
| --uri           | string |          |         | Source uri of record, such as an ipfs link |
| --meta          | string |          |         | meta data of record                        |

## coven query record record

Query record by id

```bash
coven query record record [record-id]
```
