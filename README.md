# Corner Kick Analysis — English Premier League

Statistical analysis of 256 hand-coded corner kicks from the 2025/26 Premier League season, investigating which tactical factors predict dangerous attacking outcomes.

---

## Overview

Corner kicks represent one of soccer's few structured, repeatable scoring opportunities — yet only about 2.3% directly produce goals. This project asks: **what actually makes a corner dangerous?**

Rather than only measuring goals, we built a weighted **danger scoring system** that quantifies the threat level of every outcome (goal, shot on target, shot off target, clearance, etc.) on a continuous scale. This allowed us to evaluate corner quality far more precisely than a binary goal/no-goal approach.

Key questions we investigated:

- Do short corners generate more danger than traditional crosses?
- Does winning first contact actually predict possession retention?
- Which target locations on the field produce the highest attacking threat?
- How does counter-attack risk vary by delivery type?

---

## Data

- **Source:** Hand-coded from live match footage — 256 corner kicks across matchweeks 7–11 of the 2025/26 Premier League season (October–November 2025)
- **Collection:** 5 observers each coded up to 5 matches using a standardized coding sheet
- **Observations:** Each row is one corner kick
- **Exclusions:** Time-wasting corners taken by winning teams after 90 minutes were excluded

### Variables

| Variable | Description |
|---|---|
| `Attack` / `Defense` | Teams involved |
| `Score` | Goal differential (attacking − defending) at time of corner |
| `Time` | Match minute |
| `A.Height` / `D.Height` | Average height (cm) of attacking / defending outfield players |
| `Goal.Height` | Height of goalscorer, if applicable |
| `Left.Side` | 1 = left corner flag, 0 = right |
| `Inswinger` | 1 = ball curls toward goal, 0 = away |
| `A.in.6` / `A.in.Box` | Attacking players in 6-yard box / penalty area |
| `D.in.6` / `D.in.Box` | Defending players in 6-yard box / penalty area |
| `First.Contact` | 1 = attacking team made first touch |
| `Outcome` | Result: Goal, Shot on Target, Shot off Target, Cleared, etc. (11 categories) |
| `Possession` | 1 = attacking team recovered possession |
| `Location` | Target zone: Goalmouth, Front Post, Back Post, Penalty Spot, Short, Top of Box |
| `Short` | 1 = corner played short |

---

## Key Findings

**Short corners are far more dangerous than traditional crosses**
Short corners produced a danger score nearly 3× higher than other deliveries (0.90 vs 0.34) and a goal/shot rate of 35.5% vs 14.7%. A chi-square test (p = 0.009) and two-sample t-test (p = 0.022) both confirmed the difference is statistically significant.

**Winning first contact does not predict possession**
The defending team won first contact 60.2% of the time, yet the attacking team recovered possession 60.9% of the time — a near-zero relationship confirmed by a chi-square test (p = 0.994). Partial clearances and uncontrolled headers frequently fall to attackers, suggesting **second-ball positioning matters more than first touch**.

**Delivery location drives danger, not first contact**
When first contact went to attackers, danger scores were significantly higher (p < 0.0001) — but this reflects that attacking touches tend to occur in high-value zones like the goalmouth, not that winning first contact itself creates danger. The cross delivery and target location do the heavy lifting.

**Short corners offer the best risk-reward balance**
Despite generating the most attacking danger, short corners did not increase counter-attack exposure, making them the optimal tactical choice for corners.

---

## Files

| File | Description |
|---|---|
| `CornerKickProject.pdf` | Full report: background, data summary, visualizations, statistical tests, findings |
| `corners.csv` | Raw dataset — 256 hand-coded corner kicks |

---

## Tools

R · ggplot2 · Base R statistical tests (chi-square, two-sample t-test)

---

## Authors

Championship Group 4 — Hayden Andrews, Lauren Havenstein, Tyler Katowitz, Daniel Larson, Gavin Rowland
