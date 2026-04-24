# FITE7415 Project

Quantitative trading strategy research project for HKU FITE7415. This repository contains the full path from early BTCUSD exploration to the final XAUUSD production candidate.

## Final Strategy

The final selected strategy is `XAUUSD-ZEntry-Grid`, a daily mean-reversion strategy on XAUUSD.

- Main script: `Program/XAUUSD-ZEntry-Grid/code/xauusd_round26_zentry_m1_0_v1.py`
- Selected round: Round 26
- Core idea: enter when price is sufficiently below a 20-day mean, then manage risk with ATR-based stop loss, take profit, and a max holding period

### Final Result vs Baseline

| Metric | Final Strategy | Baseline (Round 23) |
|--------|----------------|---------------------|
| Sharpe | 1.1869 | 0.7956 |
| MaxDD | 0.01281 | 0.02653 |
| TotalPnL | +601.6870 | +696.9780 |
| TradeCnt | 100 | 280 |

## How To Reproduce

The recommended path is the ALGOGENE Web UI. This is the simplest way for teammates to reproduce the reported result.

### Script To Run

Use:

`Program/XAUUSD-ZEntry-Grid/code/xauusd_round26_zentry_m1_0_v1.py`

### Backtest Settings

Use these values exactly:

| Field | Value |
|-------|-------|
| Strategy Name | XAUUSD-ZEntry-Grid-R26 |
| Subscribe List | XAUUSD |
| Start Date | 2023-01 |
| End Date | 2025-12 |
| Initial Capital | 10000 |
| Base Currency | USD |
| Risk Free Rate | 0 |
| Leverage | 1 |
| Allow Short Sell | False |
| Dataset | 1440 (1-day) |
| Position Base Env | False |
| News Feed | False |
| Economics Feed | False |
| Weather Feed | False |

### Web UI Steps

1. Log in to `algogene.com`.
2. Open **Algo Research Lab**.
3. Upload `Program/XAUUSD-ZEntry-Grid/code/xauusd_round26_zentry_m1_0_v1.py`.
4. Enter the exact settings from the table above.
5. Submit the backtest.
6. Compare the output with the target metrics below.

### Reproduction Success Criteria

Treat the run as successfully reproduced if the full-sample result is close to:

| Metric | Target |
|--------|--------|
| TradeCnt | 100 |
| TotalPnL | +601.6870 |
| Sharpe | 1.1869 |
| MaxDD | 0.01281 |

Small differences can occur because of platform-side execution details, but the trade count, Sharpe level, and drawdown profile should remain close.

## Quick Setup for Teammates (One-Click Local Testing)

For team members who want to test the strategy locally with MCP environment:

### Prerequisites
- Python 3.10 or higher (if Python is not installed, download from python.org)
- Git (for cloning the repository)

### Setup Steps (Windows/Mac/Linux)

**Step 1: Clone Repository**
```bash
git clone https://github.com/CharlieInTheFranxx/FITE7415-Project.git
cd FITE7415-Project
```

**Step 2: Create Virtual Environment**

*On Windows (PowerShell):*
```powershell
python -m venv FITE7415
.\FITE7415\Scripts\Activate.ps1
```

*On Mac/Linux:*
```bash
python3 -m venv FITE7415
source FITE7415/bin/activate
```

**Step 3: Install Dependencies**
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

**Step 4: Verify Installation**
```bash
python -c "import algogene_mcp_server; print('✓ MCP dependencies installed successfully')"
```

**Step 5: View Strategy Code**
```bash
cat Program/XAUUSD-ZEntry-Grid/code/xauusd_round26_zentry_m1_0_v1.py
```

### Running Tests Locally

Once the MCP environment is set up, you can:
1. Copy your personal ALGOGENE credentials into a local `config.py` (not tracked by git)
2. Adapt the strategy script to use local MCP client
3. Test any modifications before submitting to ALGOGENE platform

### Troubleshooting

**Issue**: Virtual environment creation fails
- **Solution**: Check that Python 3.10+ is installed (`python --version`), and you have write permissions in the project directory

**Issue**: pip install fails with package resolution errors
- **Solution**: Update pip first with `pip install --upgrade pip`, then retry the installation

**Issue**: "algogene_mcp_server not found" error
- **Solution**: Ensure you are in the activated virtual environment (you should see `(FITE7415)` in your shell prompt)

## Repository Layout

- `Program/BTCUSD/`: early BTCUSD research and reports
- `Program/XAUUSD/`: XAUUSD shadow optimization and baseline selection
- `Program/XAUUSD-ZEntry-Grid/`: final mainline optimization rounds and selected production candidate
- `Program/Overview.md`: project status summary
- `Program/current-mainline.md`: active mainline pointer
- `Program/hard.md`: strategy design notes

## Key Research Files

- Main winner report: `Program/XAUUSD-ZEntry-Grid/reports/26th-round.md`
- Final closeout: `Program/XAUUSD-ZEntry-Grid/reports/B-mainline-optimization-closeout.md`
- Baseline reference: `Program/XAUUSD/code/xauusd_mainline_v1.py`

## Strategy Notes

- Platform: ALGOGENE
- Frequency: daily bars
- Instrument: XAUUSD
- Short selling: disabled
- Leverage: 1x

Use your own ALGOGENE account and configure credentials locally outside version control.

## Course Context

Course: FITE7415  
Institution: The University of Hong Kong

This repository is intended for coursework collaboration, research review, and result reproduction.

### Quantitative Trading Theory
- Concepts: Mean reversion, Z-scores, ATR, Sharpe ratio
- References: Course materials and standard quant finance textbooks

### Contact

For questions about this project:
1. **Group Lead**: Zhang Haotian (u3665820@connect.hku.hk)
2. **Team Members**: [To be added by collaborators]

---

**Last Updated**: 2026-04-24  
**Status**: ✅ Production Ready  
**Next Steps**: Final course report submission
