# Monte Carlo Assumptions — Defense Procurement / Monopsony Lock-In

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $33.7B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 4.88 | Confirmed by N=100,000 draws |
| ΔW median (result) | $164.4B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_cost_overrun_xinefficiency` | normal | $50.0B | $60.0B | $70.0B | Cost-plus contracting X-inefficiency: $80B raw cost growth (GAO/ICEAA 1.68× fact |
| `C2_monopoly_rent` | normal | $24.0B | $30.0B | $36.0B | Sole-source premium: 46% of $350B non-competitive × 22% markup × 0.85 attributio |
| `C3_opportunity_cost` | normal | $31.5B | $38.7B | $46.8B | Deadweight loss from C1+C2 ($43B) × 0.90 attribution × 1.2 opportunity-cost mult |
| `C4_readiness_degradation` | normal | $14.4B | $17.6B | $21.6B | Sustainment monopoly O&S overruns ($22B on $200B O&S base, 10-15%) × 0.80 attrib |
| `C5_political_economy` | lognormal | $4.9B | $7.0B | $9.8B | $34B unrequested earmarks, $170M lobbying/yr (500-1200 lobbyists), 84% think-tan |
| `C6_governance_institutional_failure` | normal | $7.8B | $11.1B | $14.3B | CR disruption ($5-8B/yr, 9/10 FYs), FAR compliance burden ($4-7B), reform-delay  |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 2.0 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 2.0) = 0.0000%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 4.88 | 20% DC adj = 3.9 | 40% DC adj = 2.93

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $164B = 0.2% of world GDP ($106T) ✓
- **β_W range**: 4.88 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
