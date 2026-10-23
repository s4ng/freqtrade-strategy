# freqtrade-strategy

[English](README.md) | 한국어

[Freqtrade](https://www.freqtrade.io/) 기반의 암호화폐 자동매매 전략 모음 및 Docker Compose 실행 환경입니다.

---

## 전략 목록 (Strategies)

- [ElliotV5_SMA](https://strat.ninja/overview.php?strategy=ElliotV5_SMA)
- [E0V1E_45](https://github.com/ssssi/freqtrade_strs/blob/c919fd17ed1a50310aa41ba36c849641455bfe3a/binance/E0V1E.py)
- [E0V1E_49](https://github.com/xamie01/project-samuel/blob/476bd293b4950ab985bdf70bbecd40d6bde67901/MY%20BOT%20DOCS/strategies/E0V1E.py)
- [E0V1E_53](https://strat.ninja/overview.php?strategy=E0V1E_53)
- [E0V1E_55](https://strat.ninja/overview.php?strategy=Utopia) *(메인 / 기본값)*

---

## 요구사항 (Requirements)

- [Docker](https://docs.docker.com/get-docker/) 및 [Docker Compose](https://docs.docker.com/compose/)
- Bash 실행 환경 *(`./run` 스크립트 실행용 - Linux, macOS, 또는 Windows WSL / Git Bash)*
- 거래소 API 자격 증명 *(예: Binance)*

---

## 시작하기 (Getting Started)

### 1. 설정 파일 준비
샘플 설정 파일을 복사하여 거래소 API 키 등을 설정합니다:
```bash
cp user_data/config.json.sample user_data/config.json
```
`user_data/config.json` 파일을 열어 다음 설정을 확인 및 변경합니다:
- `exchange.key` & `exchange.secret`: 거래소 API 키 및 시크릿 입력
- `dry_run`: 모의 투자(시뮬레이션) 시 `true`, 실제 거래 시 `false`

### 2. 스크립트 실행 권한 부여 (Linux / macOS / WSL)
```bash
chmod +x run
```

---

## 사용법 (Usage)

제공되는 `./run` 헬퍼 스크립트 또는 `docker compose` 명령어를 직접 사용할 수 있습니다.

### `./run` 헬퍼 스크립트 명령어

| 명령어 | 설명 | 해당 Docker Compose 명령 |
| :--- | :--- | :--- |
| `./run trade` | 트레이딩 봇 백그라운드 실행 | `docker compose up -d trade` |
| `./run stop` | 실행 중인 트레이딩 봇 정지 | `docker compose down` |
| `./run -d`, `--download-data` | 과거 거래 데이터 다운로드 | `docker compose run --rm download-data` |
| `./run -b`, `--backtesting` | 다운로드한 데이터로 백테스팅 실행 | `docker compose run --rm backtesting` |
| `./run -p`, `--test-pairlist` | 페어리스트 설정 검증 | `docker compose run --rm test-pairlist` |

### 웹 UI (FreqUI)
트레이딩 봇이 실행 중일 때 브라우저에서 웹 대시보드에 접속할 수 있습니다:
- **URL**: [http://localhost:8080](http://localhost:8080)

> **로그 확인**: `user_data/logs/freqtrade.log` 파일 또는 `docker compose logs -f trade` 명령어로 확인할 수 있습니다.

---

## 면책 조항 (Disclaimer)
본 프로젝트는 교육 및 연구 목적으로 제공됩니다. 암호화폐 거래는 높은 금융 위험을 수반하며 원금 손실이 발생할 수 있습니다. 모든 투자 판단 및 손익에 대한 책임은 사용자 본인에게 있습니다.
