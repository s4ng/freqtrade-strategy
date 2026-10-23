# freqtrade-strategy

English | [한국어](README.ko.md)

Trading strategies and Docker Compose setup for [Freqtrade](https://www.freqtrade.io/).

---

## Strategies

- [ElliotV5_SMA](https://strat.ninja/overview.php?strategy=ElliotV5_SMA)
- [E0V1E_45](https://github.com/ssssi/freqtrade_strs/blob/c919fd17ed1a50310aa41ba36c849641455bfe3a/binance/E0V1E.py)
- [E0V1E_49](https://github.com/xamie01/project-samuel/blob/476bd293b4950ab985bdf70bbecd40d6bde67901/MY%20BOT%20DOCS/strategies/E0V1E.py)
- [E0V1E_53](https://strat.ninja/overview.php?strategy=E0V1E_53)
- [E0V1E_55](https://strat.ninja/overview.php?strategy=Utopia) *(Main / Default)*

---

## Requirements

- [Docker](https://docs.docker.com/get-docker/) & [Docker Compose](https://docs.docker.com/compose/)
- Bash environment *(Linux, macOS, or WSL / Git Bash on Windows for `./run` helper script)*
- Exchange API credentials *(e.g., Binance)*

---

## Getting Started

### 1. Configuration
Copy the sample configuration file and add your exchange credentials:
```bash
cp user_data/config.json.sample user_data/config.json
```
Edit `user_data/config.json`:
- `exchange.key` & `exchange.secret`: Your exchange API credentials.
- `dry_run`: Set to `true` for paper trading (simulation), or `false` for live trading.

### 2. Permissions (Linux / macOS / WSL)
Grant execution permissions to the helper script:
```bash
chmod +x run
```

---

## Usage

You can use the `./run` helper script or execute `docker compose` commands directly.

### Helper Script Commands

| Command | Description | Equivalent Docker Command |
| :--- | :--- | :--- |
| `./run trade` | Start trading bot in background | `docker compose up -d trade` |
| `./run stop` | Stop trading bot | `docker compose down` |
| `./run -d`, `--download-data` | Download historical market data | `docker compose run --rm download-data` |
| `./run -b`, `--backtesting` | Run backtest using downloaded data | `docker compose run --rm backtesting` |
| `./run -p`, `--test-pairlist` | Test pairlist configuration | `docker compose run --rm test-pairlist` |

### Web UI (FreqUI)
When the trade service is running, the web UI is available at:
- **URL**: [http://localhost:8080](http://localhost:8080)

> **Logs**: View logs in `user_data/logs/freqtrade.log` or run `docker compose logs -f trade`.

---

## Disclaimer
This project is for educational and research purposes only. Cryptocurrency trading carries significant risk. Use at your own risk.
