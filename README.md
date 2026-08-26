# r6-dossier

Single-page repository for an unlisted GitHub Pages brief. The live path is unguessable and is not listed here.

## Operator ranking (top five)

Do not sort a player's attack or defence table by round count alone. Score every operator with four equally weighted parts (25% each). Compare scores **inside a sample-size band**, so a hot fifteen-round sample cannot outrank an eighty-round main.

### Bands

| Band | Rounds | What it means |
|---|---|---|
| A | 30+ | Can support a conclusion. Rank these first, by score. |
| B | 11–29 | A hint. Rank these next, by score. |
| C | 10 or fewer, or no sample (`—`) | Noise, or a recommendation with no data. Rank these last. Recs with no figures stay at the foot. |

### Score

Each part is scaled to 0–1, then averaged, then shown as 0–100.

```
win  = clamp((win_rate_pct - 30) / 40)     # 30% → 0,  70% → 1
kd   = clamp((kd - 0.40) / 1.60)           # 0.40 → 0,  2.00 → 1
srv  = clamp((survival_pct - 15) / 45)     # 15% → 0,  60% → 1
rds  = clamp((rounds - 8) / 92)            # 8 → 0,     100 → 1 (caps)

score = 100 * (win + kd + srv + rds) / 4
```

`clamp(x)` is `min(1, max(0, x))`.

Rounds saturate at 100, so 132 vs 111 is a small gap. K/D saturates at 2.00, so one 2.28 night cannot spend the whole score on a single stat. Win rate below 30% and survival below 15% score zero on that part.

Worked defence example: an operator at 96 rounds / 48% WR / 1.16 K/D / 35% SRV scores **58**. One at 89 / 58% / 1.34 / 44% scores **70**. Volume is not enough when the other three lines are worse.

When two Band A scores are within about two points, role identity may break the tie (default hard breach ahead of a similarly scored intel pick). Log that as a judgement call, not as a silent reorder.

## Privacy

- This repo is public.
- The page includes `<meta name="robots" content="noindex, nofollow">`.
- Do not block the path in `robots.txt` — crawlers need to fetch the page to see noindex.
- Do not link the published URL in public places.
- Players are referred to by handle only.
