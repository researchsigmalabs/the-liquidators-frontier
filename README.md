# The Liquidator's Frontier

**Leverage, Seniority and the Endogenous Attachment Point in Isolated Lending Markets**

σ-Labs · working paper (draft — open for review and contributions)

📄 [the-liquidators-frontier.pdf](the-liquidators-frontier.pdf) · source: [the-liquidators-frontier.tex](the-liquidators-frontier.tex)

---

## What this is

A risk model for on-chain overcollateralised lending derived from the **protocol's own mechanics** — the oracle, the liquidation incentive and the interest-rate model — rather than an external stochastic model bolted on top.

A collateralised borrow in an isolated market is a **two-tranche structure**: the borrower holds the residual claim (long a put on the collateral), the lender holds the senior one. The attachment point that actually binds is not the contractual LLTV line — it is an **effective** one, produced block by block, and it is never written down.

## Core results

- **The effective attachment ≠ the LLTV line.** The contractual threshold has a closed form; the effective one is produced each block by the oracle × liquidation incentive × IRM, and it is the one that binds.
- **One primitive governs clearing:** from the liquidator's incentive inequality, a maximum tolerable slippage **σ\* = c(1−λ)** and a minimum viable size proportional to gas. The LLTV headroom `1−λ` splits — in fixed proportion `c : 1−c` — between the **enforcer's budget** (σ\*) and the **room retained** (the buffer β).
- **σ\* is distribution-free and block-computable** (venue state is readable), so the frontier is a floor you can evaluate every block with no distributional assumption — at the cost of being a best case.
- **One inequality, three failures:** a reverting oracle, illiquid collateral, and dust positions nobody closes are the *same* inequality losing on different terms.
- **Raising the LLTV cap shrinks σ\*** — so the cap is a claim about the collateral's liquidity stated in the grammar of a risk parameter.

## Why it matters

"Near-zero LGD" on blue-chip collateral is **real but conditional**: it holds only while liquidators can offload seized collateral within σ\* of the oracle price. When the haircut needed to warehouse an asset exceeds σ\*, **no rational liquidator clears it** — the position can't be liquidated and the lender is left short a put that is never exercised. For tokenised / illiquid collateral near the cap, that put is **permanently uncleared**.

## Building

`the-liquidators-frontier.tex` is self-contained (no external figures). Build with any TeX distribution:

```
pdflatex the-liquidators-frontier.tex
```

## Contributing

This is a **draft open for outside review and contributions**. We especially welcome:

- counter-examples and failures of the σ\* frontier,
- extensions to the first-passage / cascade sections,
- empirical liquidation data that tests the effective-vs-contractual gap,
- composition with structural credit pricing (Merton / Black–Cox).

**All changes land via pull request** — see [CONTRIBUTING.md](CONTRIBUTING.md). Open an issue to discuss first if you'd like.

Contact: σ-Labs.

## License

Text and figures: [CC BY 4.0](LICENSE). Please cite as *σ-Labs, "The Liquidator's Frontier," 2026.*
