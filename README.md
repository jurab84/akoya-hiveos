The miner has not yet been tested with more than 2 cards, problems are possible.


**How to change dev fee:**

In Flight Sheet → **Extra config arguments** field:

```
fee=5
```

Save and click **Apply** on the worker. New fee will be applied within 1 hour (at the start of the next cycle) without restarting the miner.

To apply immediately:

```bash
miner restart
```

**Examples:**

```
fee=0        # disable dev fee
fee=3        # default (3%)

```

---

**Updated GitHub description:**

---

# akoya-miner HiveOS

Custom HiveOS package for mining **Pearl (PEARL)** on [akoyapool.com](https://akoyapool.com).

## Features

- ✅ Multi-GPU support (all NVIDIA GPUs detected automatically)
- ✅ Live dashboard in screen session (updates every 5 seconds)
- ✅ Shows per-GPU hashrate, power, temp, fan, core/mem clocks and OC offsets
- ✅ Auto-installs required CUDA libraries (`libcublasLt`) on first run — no manual setup needed
- ✅ Configurable dev fee (default 3%) via Extra config arguments
- ✅ Settings reload every 1 hour without restarting the miner
- ✅ Tested on RTX 3070, RTX 3090

## Requirements

- NVIDIA GPU with Tensor Cores: RTX 30xx, RTX 40xx, RTX 50xx, A100, H100
- Driver 525+ (CUDA 12.2+)
- HiveOS 0.6-229 or newer

## Flight Sheet Setup

| Field | Value |
|---|---|
| Coin | PEARL |
| Wallet | your `prl1...` address |
| Pool | Configure in miner |
| Miner | Custom |

**Setup Miner Config:**

| Field | Value |
|---|---|
| Miner name | `akoya-miner` |
| Installation URL | `https://github.com/jurab84/akoya-hiveos/releases/download/akoya-hive/akoya-miner-hiveos.tar.gz` |
| Hash algorithm | *(leave empty)* |
| Wallet and worker template | `%WAL%.%WORKER_NAME%` |
| Pool URL | `pool.akoyapool.com:3333` |
| Pass | *(leave empty)* |
| Extra config arguments | *(empty by default)* |

## Extra Config Arguments

| Parameter | Description | Default |
|---|---|---|
| `fee=N` | Dev fee 0-3| `3` |
| `dev_wallet=prl1...` | Custom dev fee address | built-in |

Multiple params: `fee=5,dev_wallet=prl1abc...`

## On First Run

The miner automatically:
1. Downloads the akoya-miner binary from `get.akoyapool.com`
2. Detects and installs the required `libcublas-12-x` library for your CUDA version
3. Selects the optimal GPU kernel (portable for RTX 30/40/50, H100-optimized for Hopper)
4. Writes config and starts mining

No manual dependency installation needed.

## Changing Dev Fee

In Flight Sheet → **Extra config arguments**:
```
fee=5
```
Changes apply within 1 hour or immediately after `miner restart`.

## Raw Logs

Full miner output is available at:
```
/var/log/miner/custom/akoya-miner-raw.log
```
