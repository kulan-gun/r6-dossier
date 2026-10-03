# r6-dossier

Single-page repository for an unlisted GitHub Pages brief. The live path is unguessable and is not listed here.

## Operator ranking (top five)

Do not sort a player's attack or defence table by round count alone. Score every operator on four parts: rounds (40%), win rate, K/D and survival (20% each). Compare scores **inside a sample-size band**, so a hot fifteen-round sample cannot outrank an eighty-round main.

Rounds carry the most weight because a line is harder to hold the longer it runs. A 1.40 K/D over two hundred rounds says more than a 1.52 over a hundred, and the score should show that.

The second table on each card is **Substitutes** on Kulan_G100's and Big_Bunda_20's cards, and **Substitutes (on trial)** on the other three. That is not a testing queue: it is the next seat when a top-five pick is banned, taken, or a poor fit for the site. "On trial" means the sample is not large enough to call the sub settled.

### Bands

| Band | Rounds | What it means |
|---|---|---|
| A | 30+ | Can support a conclusion. Rank these first, by score. |
| B | 11–29 | A hint. Rank these next, by score. |
| C | 10 or fewer, or no sample (`—`) | Noise, or a recommendation with no data. Rank these last. Recs with no figures stay at the foot. |

### Score

Each part is scaled to 0–1, weighted, then shown as 0–100.

```
win  = clamp((win_rate_pct - 30) / 40)     # 30% → 0,  70% → 1
kd   = clamp((kd - 0.40) / 1.60)           # 0.40 → 0,  2.00 → 1
srv  = clamp((survival_pct - 15) / 45)     # 15% → 0,  60% → 1
rds  = clamp(ln(rounds / 8) / ln(300 / 8)) # 8 → 0,  ~55 → 0.53,  100 → 0.70,  200 → 0.89,  300 → 1

score = 100 * (0.2*win + 0.2*kd + 0.2*srv + 0.4*rds)
```

`clamp(x)` is `min(1, max(0, x))`.

Rounds are on a log scale: the early rounds earn the most, and credit keeps growing up to 300 instead of stopping at 100. The previous version weighted all four parts equally and capped rounds at 100, which gave a 105-round line the same volume credit as a 210-round one. K/D saturates at 2.00, so one 2.28 night cannot spend the whole score on a single stat. Win rate below 30% and survival below 15% score zero on that part.

Worked attack example: Thermite at 210 rounds / 51% WR / 1.40 K/D / 41% SRV scores **71**. Lion at 105 / 50% / 1.52 / 47% scores **67**. The sharper short line does not outrank the same quality held over twice the rounds.

Worked defence example: an operator at 96 rounds / 48% WR / 1.16 K/D / 35% SRV scores **55**. One at 89 / 58% / 1.34 / 44% scores **65**. Volume is still not enough when the other three lines are clearly worse.

When two Band A scores are within about two points, role identity may break the tie (default hard breach ahead of a similarly scored intel pick). Log that as a judgement call, not as a silent reorder.

## Privacy

- This repo is public.
- The page includes `<meta name="robots" content="noindex, nofollow">`.
- Do not block the path in `robots.txt` — crawlers need to fetch the page to see noindex.
- Do not link the published URL in public places.
- Players are referred to by handle only.
