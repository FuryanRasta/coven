# Farm

Farm module allows you to easily create farm activities on coven.

## Available Commands

| Name                              | Description                                           |
| --------------------------------- | ----------------------------------------------------- |
| [create](#coven-tx-farm-create)    | Create a new farm pool                                |
| [adjust](#coven-tx-farm-adjust)    | Adjust farm pool parameters                           |
| [destroy](#coven-tx-farm-destroy)  | Destroy the farm pool and get back the invested bonus |
| [stake](#coven-tx-farm-stake)      | Deposit liquidity token                               |
| [harvest](#coven-tx-farm-harvest)  | Get back the bonus for participating in the farm pool |
| [farmer](#coven-query-farm-farmer) | Query farmer information                              |
| [pool](#coven-query-farm-pool)     | Query the current status of a farm pool               |
| [pools](#coven-query-farm-pools)   | Query farm pool information by page                   |
| [params](#coven-query-farm-params) | Query the management parameters of the farm module    |

## coven tx farm create

Create a new farm pool and pay the handling fee and bonus.

```bash
coven tx farm create <Farm Pool Name> [flags]
```

**Flags:**

| Name, shorthand    | Required | Default | Description                                              |
| ------------------ | -------- | ------- | -------------------------------------------------------- |
| --lp-token-denom   | true     |         | The liquidity token accepted by farm pool                |
| --reward-per-block | true     |         | The reward per block,ex: 1coven,1atom                     |
| --total-reward     | true     |         | The Total reward for the farm pool                       |
| --description      | false    | ""      | The simple description of a farm pool                    |
| --start-height     | true     |         | The start height the farm pool                           |
| --editable         | false    | false   | Is it possible to adjust the parameters of the farm pool |

### coven tx farm adjust

Adjust the parameters of the pool before the farm pool ends, such as `reward-per-block`, `total-reward`.

```bash
coven tx farm adjust <Farm Pool Name> [flags]
```

**Flags:**

| Name, shorthand     | Required                                  | Default | Description                          |
| ------------------- | ----------------------------------------- | ------- | ------------------------------------ |
| --additional-reward | And `--reward-per-block` must choose one  | ""      | Bonuses added to the farm pool       |
| --reward-per-block  | And `--additional-reward` must choose one | ""      | The reward per block,ex: 1coven,1atom |

## coven tx farm destroy

Destroy the farm pool and get back the invested bonus.The rewards earned by the user farm ends at this moment, requiring the user to manually retrieve the income and the liquidity of the deposit.

```bash
coven tx farm destroy <Farm Pool Name> [flags]
```

### coven tx farm stake

The farmer participates in farm activities by staking the liquidity tokens specified by the pool. The rewards obtained by participating in the activities are related to the number of staking tokens and farm pool parameters.

```bash
coven tx farm stake <Farm Pool Name> <lp token> [flags]
```

### coven tx farm harvest

The farmer withdraws his rewards back.

```bash
coven tx farm harvest <Farm Pool Name>
```

### coven query farm farmer

Query farmer's information, including unclaimed rewards, mortgage liquidity, etc.

```bash
coven query farm farmer <Farmer Address> --pool-name <Farm Pool Name>
```

**Flags:**

| Name, shorthand | Required | Default | Description        |
| --------------- | -------- | ------- | ------------------ |
| --pool-name     | false    | ""      | the farm pool name |

### coven query farm pool

Query related information of a farm pool by name

```bash
coven query farm pool <Farm Pool Name>
```

### coven query farm pools

Paging query farm pool

```bash
coven query farm pools
```

### coven query farm params

Paging query farm pool

```bash
coven query farm params
```
