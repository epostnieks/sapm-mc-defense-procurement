# Data Sources — Defense Procurement Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Defense Procurement: Monopsony Lock-In) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_cost_overrun_xinefficiency`

Cost-plus contracting X-inefficiency: $80B raw cost growth (GAO/ICEAA 1.68× factor on $350B base) × 0.75 attribution. RAND: 60-65% contractor-attributable. Sources: GAO-25-106402, ICEAA 2020, Arena et al. 2006.

*Full citations: paper §4 (available SSRN).*

### `C2_monopoly_rent`

Sole-source premium: 46% of $350B non-competitive × 22% markup × 0.85 attribution. 13→3 tactical missile suppliers, 8→3 aircraft. Stinger $25K→$400K. Sources: FPDS, POGO, Quincy Institute.

*Full citations: paper §4 (available SSRN).*

### `C3_opportunity_cost`

Deadweight loss from C1+C2 ($43B) × 0.90 attribution × 1.2 opportunity-cost multiplier. CBO/Hamilton: infrastructure ROI 2-4× marginal defense. Sources: Hamilton Project, CBO.

*Full citations: paper §4 (available SSRN).*

### `C4_readiness_degradation`

Sustainment monopoly O&S overruns ($22B on $200B O&S base, 10-15%) × 0.80 attribution. F-35 50% availability, $1.3T lifetime sustainment. Sources: DoD IG, GAO-24, NTU Foundation.

*Full citations: paper §4 (available SSRN).*

### `C5_political_economy`

$34B unrequested earmarks, $170M lobbying/yr (500-1200 lobbyists), 84% think-tank funding, 645 revolving-door instances/yr × 0.70 attribution. Sources: OpenSecrets, POGO, Quincy Institute, Public Citizen.

*Full citations: paper §4 (available SSRN).*

### `C6_governance_institutional_failure`

CR disruption ($5-8B/yr, 9/10 FYs), FAR compliance burden ($4-7B), reform-delay compounding ($3-7B) × 0.65 attribution. Section 809: 98 recs, ~24 implemented. Sources: DoD IG 2025, Section 809 Panel, GAO.

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $33.7B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Defense Procurement (Monopsony Lock-In)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
