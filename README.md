miner for HiveOS
Here are all the settings for GitHub:

**Installation URL:**
`https://github.com/jurab84/akoya-hiveos/releases/download/akoya-hive/akoya-miner-hiveos.tar.gz`
**Flight Sheet — main fields:**

| Field | Value |
|---|---|
| Coin | PEARL |
| Wallet | wal|
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
| Extra config arguments | *(empty by default, or e.g. `fee=5`)* |

---

**Extra config arguments:**

| Parameter | Description | Example |
|---|---|---|
| `fee=N` | Dev fee from 0 to 100% (default: 3) | `fee=5` |
| `dev_wallet=prl1...` | Address for dev fee (default built-in) | `dev_wallet=prl1abc...` |

Multiple params can be combined with a comma: `fee=5,dev_wallet=prl1abc...`

---

**Requirements:**
- NVIDIA GPU with Tensor Cores: RTX 30xx, RTX 40xx, RTX 50xx, A100, H100
- CUDA 12.2+ (driver 525+)
- HiveOS 0.6-229 or newer

---

**Notes:**
- On first run the miner binary is downloaded automatically from `get.akoyapool.com`
- OC settings (core/mem offsets) are read live from HiveOS every 5 seconds
- Pool settings (fee, wallet, pool URL) are reloaded every 10 minutes without restarting
- Raw miner logs are available at `/var/log/miner/custom/akoya-miner-raw.log`
