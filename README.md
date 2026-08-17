# SOMIN Cloud Suite — prototype (sowise.somin.ai)

Interactive prototype restyled to the **somin-brand-guideline** (2026, *Brands* voice).
Two self-contained pages, no build step, no dependencies beyond the Google Fonts link.

| File | Serves at | What it is |
|---|---|---|
| `index.html` | `https://sowise.somin.ai/` | Cloud Suite — dashboard, strategy, social, SEO/AEO/GEO, ads, plan & billing |
| `pro.html` | `https://sowise.somin.ai/pro.html` | SOMIN PRO — SOMIN Copilot + SOWISE agentic workspace (simple + advanced modes) |
| `CNAME` | — | `sowise.somin.ai` |
| `somin_social_preview.png` | — | 1200×630 OG card for `index.html` |
| `somin_pro_preview.png` | — | 1200×630 OG card for `pro.html` |

The two pages cross-link on the live domain: `index.html` opens SOMIN PRO at
`https://sowise.somin.ai/pro.html` (3 entry points — enterprise chip, strategy
header, plan & billing); `pro.html` links back to `https://sowise.somin.ai/`
("↗ SOMIN Cloud Suite", in both the advanced sidebar and the simple view).

## Sign-in

Two accounts, same password on both pages:

| Email | Shown as |
|---|---|
| `sasha@somin.ai` | Aleks Farseev · Founder · SOMIN |
| `kirill@somin.ai` | Kirill Lepikhin · SOMIN |

Password: `123qwe0-=`

No other account is accepted. Credentials are **not** stored in either file:
each entry is the SHA-256 digest of `"<email>|<password>"`, hashed in-browser via
Web Crypto at sign-in and compared against the digest — a digest cannot be
reversed back into the email or password. `pro.html` already worked this way;
`index.html` used a plaintext `USERS` map and a plaintext `const PASSWORD`
readable by anyone viewing source, so it now uses the same scheme. Both pages
return a single "Incorrect email or password" so a valid email can't be probed.

To change the roster, hash the new pairs and swap the digests:

```
python3 -c "import hashlib;print(hashlib.sha256(b'you@somin.ai|yourpassword').hexdigest())"
```

then edit `USERS` in `index.html` (digest → display name/role/avatar) and
`AUTH_H` in `pro.html` (flat list of digests).

## Language

**English is the default** on both pages. The EN / 中文 toggle is unchanged and
the full Chinese localisation is intact — `pro.html` remembers the choice in
`localStorage` under `somin_lang` and falls back to `en`.

---

## Brand system applied

### Palette

Accent family is **teal-only** — no red, orange or yellow anywhere in the chrome,
and every grey is teal-tinted.

| Role | Was | Now |
|---|---|---|
| Primary accent | `#FF642D` orange | **`#2DBF9C`** teal |
| Accent hover / lighter | `#FF8C43` | `#55D0B3` |
| Accent active / companion | `#C33909` | `#1F8A70` |
| Accent wash | `#FFF3D9` | `#D5F2EA` |
| Dark surface | `#191B23` | **`#16201F`** |
| Deep surface / nav wells | `#141519` | `#101817` |
| Dark card fill | `#2B2E38` | `#1F2A29` |
| Card background | `#F4F5F9` | `#F2FAF8` |
| Borders / dividers | `#E0E1E9` / `#C4C7CF` | `#DFEAE8` / `#C9D1D0` |
| Body text | `#484A54` | `#2A3635` |
| Secondary text | `#6C6E79` | `#6B7A78` |
| Soft / inactive | `#A9ABB6` | `#9BA8A6` |
| Premium / Pro (was violet) | `#8649E1` | `#14655A` |
| Info (was blue) | `#006DCA` | `#6B7A78` |
| Success (was green) | `#009F81` | `#1F8A70` |
| Danger (was red) | `#FF4953` | `#16201F` |
| Warning (was yellow) | `#FDC23C` | `#9BA8A6` |

Token names moved with the values: `--orange*` → `--teal*`, `--violet*` → `--deep*`,
`--blue*` → `--mid*`, `--green` → `--ok`, `--red` → `--neg`, `--yellow` → `--warn`.

### Category colour-coding

Each fixed category set is defined **once** and reused identically on every screen;
no two categories in a set share a value.

- Tracked brands (`--c-*` in `pro.html`): `#2DBF9C` · `#16201F` · `#14655A` · `#1F8A70` · `#7FDCC6` · `#9BA8A6`
- Pillars: P1 `#2DBF9C` · P2 `#14655A` · P3 `#6B7A78`
- Whitespace verdicts: `#2DBF9C` · `#55D0B3` · `#6B7A78` · `#16201F`
- Trend status: rising `#1F8A70` · volatile `#2DBF9C` · falling `#6B7A78` · flat `#9BA8A6`
- Funnel stages: TOFU `#6B7A78` · MOFU `#14655A` · BOFU `#2DBF9C`

### Type

Montserrat throughout (Noto Sans SC retained for the `zh` locale), replacing Inter.
Section labels are Regular caps at `0.2em` tracking in teal; stat labels at `0.15em`.
Headlines stay sentence case — the **Brands** voice.

### Wordmark

The legacy spark glyph is gone. Every mark is now the SOMIN wordmark: `SO` in
`#2DBF9C` joined flush to `MIN` in `#16201F` on light surfaces / `#FFFFFF` on dark,
tight tracking, top-left. Rendered as two spans with no space and no added
letter-spacing, in all four places it appears (Cloud Suite sidebar + login, PRO
sidebar + login, and the nested simple-mode prototype).

Favicons and apple-touch-icons were rebuilt as the SOMIN parallelogram
(locked 2.414 : 1, teal on `#16201F`) — legible at 16 px where a wordmark is not.

### Kept off-palette (deliberate)

Per the guideline's client-brand carve-out, real third-party platform colours stay
as themselves in channel charts and post cards: LinkedIn `#0A66C2`, Facebook
`#1877F2`, Instagram `#E4405F` / `#C13584`, Google `#4285F4` / `#34A853`, Telegram
`#229ED9`. The generated ExoStride campaign creatives are client artwork inside
SOMIN chrome and are untouched — the platform frame around them is fully SOMIN.

---

## Touchigh removal

Zero occurrences of `touchigh` (any case) remain. Renames applied:

| Was | Now |
|---|---|
| Touchigh | SOMIN |
| Touchigh Copilot | SOMIN Copilot |
| TWISE | SOWISE |
| Touch PRO | SOMIN PRO |
| HumanTouch Loop | HumanCheck Loop |
| Touchigh MCP / Touchigh-class / Touchigh-verified | SOMIN MCP / SOMIN-class / SOMIN-verified |
| `/touchigh-{brand,agency,influencer}-deck` | `/somin-{brand,agency,influencer}-deck` |
| `cloud.touchigh.ai` | `sowise.somin.ai` |
| `*@touchigh.ai`, `@touchigh` | `*@somin.ai`, `@somin_ai` |
| Nav groups `T`MONITOR / `T`INSPIRE / `T`WISE | `SO`MONITOR / `SO`INSPIRE / `SO`WISE |
| `TOUCHIGH_TEAM`, `touchighTeamCardHTML`, `Touchigh_setMode`, `Touchigh_ADS`, `touchpro`, `twiseSrc`, `th_auth`, `th_lang` | `SOMIN_TEAM`, `sominTeamCardHTML`, `SOMIN_setMode`, `SOMIN_ADS`, `sominpro`, `sowiseSrc`, `somin_auth`, `somin_lang` |

Meta, canonical, OG and Twitter tags on both pages point at `sowise.somin.ai`,
and the social preview images were regenerated on brand.

Both pages were rendered in headless Chromium across the login, onboarding and
every nav destination with **zero** JavaScript errors.
