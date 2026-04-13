# SAPM Monte Carlo — Defense Procurement / Monopsony Lock-In

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Defense Procurement (Monopsony Lock-In).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **4.88** |
| β_W mean | 4.88 |
| β_W std | 0.4 |
| **90% CI** | **[4.2, 5.5]** |
| 99% CI | [4.0, 5.8] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$164.4B/yr** |
| Π (revenue) | $33.7B/yr |

**β_W = 4.88** means the defense procurement industry destroys **$4.88 in system
welfare for every $1.00 in revenue** — across 6 channels and 100,000 Monte Carlo draws.

**Classification**: Class 2 — Intractability

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-defense-procurement.git
cd sapm-mc-defense-procurement
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 4.88` and `ΔW median : $164.4B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_cost_overrun_xinefficiency | $60.0B | [$49.9B, $70.0B] | Normal |
| C2_monopoly_rent | $30.0B | [$24.0B, $36.0B] | Normal |
| C3_opportunity_cost | $38.7B | [$31.1B, $46.3B] | Normal |
| C4_readiness_degradation | $17.6B | [$14.0B, $21.2B] | Normal |
| C5_political_economy | $7.0B | [$5.0B, $9.8B] | Lognormal |
| C6_governance_institutional_failure | $11.1B | [$7.9B, $14.3B] | Normal |
| **Total ΔW** | **$164.4B** | **[$142.6B, $186.6B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 2.0 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0000%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Defense Procurement (Monopsony Lock-In)*.
> GitHub: epostnieks/sapm-mc-defense-procurement.
> https://github.com/epostnieks/sapm-mc-defense-procurement
