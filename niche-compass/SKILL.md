---
name: niche-compass
description: Niche Compass (寻道罗盘) — a cross-platform niche compliance, competitor teardown, and monetization funnel analyzer covering both Chinese and global platforms. Given a "platform + niche" (e.g. YouTube + personal finance, TikTok + cross-border e-commerce, Instagram + fitness, Douyin + e-commerce), it adapts to the AI's own tool capability (browser-capable agents pause once to confirm logins and niche; tool-less AIs degrade gracefully and answer directly), then runs end to end and outputs a platform rules map (red lines, official programs, peer risk profiles with compliant alternatives), acquisition and monetization paths, funnel conversion ranges, break-even modeling, a competitor matrix, a feasibility scorecard, and a small-scale validation plan. Strategy teardown and data estimation only — no copywriting, no advice on evading platform review. Use this skill whenever the user mentions niche research, competitor account analysis, platform rules / red lines / creator programs, monetization paths, funnel conversion, view-to-follower ratio, pre-launch research, or data tools such as vidIQ, Social Blade, TubeBuddy, Kalodata, FastMoss, Chanmama, Feigua, Xinbang, even if they never say "analyzer".
---

# Niche Compass (寻道罗盘)

Cross-platform niche compliance, competitor teardown, and monetization funnel analyzer.

## Scope and boundaries

This skill does not depend on any specific AI or tool. Where it mentions browsing or web search, an AI that lacks that capability falls back to the degraded tiers below.

**What it does**: platform rules mapping, competitor sample teardown, monetization path analysis, funnel estimation, feasibility judgment.

**What it does not do**:
- Write copy, scripts, hooks, or slogans.
- Teach ways to evade platform review (masking, coded vocabulary, persona cover, credential workarounds). Requests like this are answered with a **peer risk profile + compliant alternatives** instead.
- Touch, request, or store the user's passwords, cookies, or tokens.
- Fabricate data. If there is no reliable basis, write "no reliable data".

## Overall flow

0. **Capability self-check and tiering** (the AI decides on its own; do not ask the user)
1. Parse input, auto-generate the platform list
2. Tier 1 only: **one single pause** — in one message, confirm login status and niche refinement. Tiers 2 and 3 do not pause; they use defaults.
3. Run to the end (handle obstacles with the fallback rules; do not interrupt the user again)
4. Collect data and filter samples
5. Sub-niche handling → Modules 1, 2, 3 → additional analyses
6. AI self-audit and correction
7. Deliver the report

---

## Capability self-check and tiering (do this first)

Before starting, judge your run tier from the tools you actually have. **Do not ask the user.** State the tier at the top of the report.

| Tier | Capability | How to run |
|---|---|---|
| 1 | Browser operation + web access | Full flow, including the Step 0 checkpoint (the single pause) |
| 2 | Web search only | Public-information edition. **No pause.** Output directly. |
| 3 | No tools | Framework edition from existing knowledge. **No pause.** Output directly. |

### Degradation rules

| Content | Tier 1 | Tier 2 | Tier 3 |
|---|---|---|---|
| Platform rules and official programs | Read official pages; include link and retrieval date | Search official pages; include link and date if found, otherwise "to be verified" | All marked "to be verified", with a note that they may be outdated |
| Red-line categories, monetization forms, compliant alternatives, risk profiles | Full | Full | Full (from general knowledge; note time-sensitivity) |
| Sample filtering, competitor matrix, comment-demand mining | Full | Only what public sources can support; rest marked "could not be completed in this run" | Marked "could not be completed in this run". **Never list specific account names or numbers.** |
| Funnel conversion | Ranges + sources; confidence can reach medium/high | Wide ranges; confidence at most "low" | Wide ranges; confidence "low"; label as experience-based reference |
| Break-even modeling | Based on funnel ranges | Based on wide ranges; order-of-magnitude only | Method and formulas only; numbers labeled "illustrative" |
| Vague niche | Offer options at the checkpoint | Use the default (overview table + deep-dive on 3) | Same as Tier 2 |

### Iron rules when tools are missing
- Anything not doable is written as "could not be completed in this run". Never invent accounts, data, or links.
- Label every data point's origin: web search / existing knowledge / none.
- Never pad numbers just to make the report look complete.

---

## Step 0: Input parsing and pre-flight checkpoint (Tier 1 only; Tiers 2–3 skip the pause and use defaults)

### 0.1 Auto-generate the platform list

Infer the platforms needed from "platform + niche" and label each role:

| Role | Description | Examples |
|---|---|---|
| Target platform | Where the user wants to operate | YouTube, TikTok, Instagram, Douyin |
| Cross-validation platform | Demand, discovery, search interest | Reddit, Pinterest, Xiaohongshu, Bilibili |
| Data tool | Third-party data platforms and official indexes | vidIQ, Social Blade, Kalodata, Google Trends |

Rules:
- Mark at most **3** platforms as "required". Everything else is "optional" and defaults to public data. This keeps the login burden light and avoids risk-control triggers from multi-account automation.
- For each: purpose | required/optional | fallback if unavailable.

### 0.2 Check login status

- If you have browser or automation tools: open each page and **only determine whether it is logged in**. Never enter credentials or read cookies.
- If you have no such tools: ask the user to check and reply. Do not assume logged in.
- Mark logged-in platforms "✅ ready". Only prompt for the ones not logged in, and the user logs in themselves.

### 0.3 Niche clarification (in the same message as the login check)

If the niche is broad, **do not guess and do not expand everything**. Offer choices in the same message:

- At most 4 options; allow "all of them" or "you decide".
- Skip this if the user was already specific.

Examples:
- "E-commerce" → ① Domestic shelf/content commerce (live and short-video selling) ② Cross-border (TikTok Shop, Amazon, DTC/independent store) ③ A specific category (please specify) ④ All of them
- "Gaming" → ① A specific game (name it) ② A game genre/type ③ General gaming content (news, commentary, streaming) ④ All of them

### 0.4 Execution environment

Prefer to judge from the tools you have. Only ask the user when you cannot tell (e.g. several tools are available). The environment decides the collection method:

| Environment | Can do | Notes |
|---|---|---|
| Browser-extension type (operates the user's open browser) | Reuse existing login, read pages, paginate, read comments, trigger downloads | Runs in the foreground; the user should not use that window at the same time |
| Automation-browser type (separate browser) | Foreground or headless | No login state; log in once inside it; headless mode usually cannot pass captchas and is easier to flag |
| Local-script type (e.g. yt-dlp) | Batch fetching from the command line; can run in the background | For logged-in content the user configures it locally; **cookies must never be sent to the AI**; keep the machine awake for long jobs |
| No tools / plain chat | Public web search | Deeper data only if the user volunteers exports |
| Cloud sandbox | Public data only | Cannot use the user's local login |

### 0.5 Checkpoint message template

One message containing: (1) platform list with login status, (2) niche options, (3) environment question if needed.

> This run needs: YouTube (target, ✅ ready), Reddit (cross-validation, ❌ not logged in), vidIQ (data, optional).
> Please: ① log in to Reddit; ② choose a direction: A… B… C… D) all of them; ③ which kind of tool are you using?
> Reply "ready" to start. If you don't reply, defaults apply: skip platforms not logged in, treat the niche as "all of them".

### 0.6 Pause and defaults

- Start immediately after the reply. **Do not interrupt again for logins or choices.**
- If the user skips or does not reply: unlogged platforms fall back to public data, the niche is treated as "all of them", and this is noted in the report's data section.

---

## Step 1: Data collection

### Modes
- **Light mode**: web search only — platform enforcement notices, public cases, public rankings.
- **Deep mode**: exports from data tools the user has logged into, or logged-in pages read via browser tools.
- Mode by tier: Tier 1 may use deep mode; Tier 2 is light mode only; Tier 3 has no collection and follows the degradation rules.

### Collection principles
- Do not rush to download videos. Titles, metrics, comments, captions, and data-tool exports usually suffice for niche research. Download video files only when analyzing visual structure.
- Rate-limit batch operations, keep them for personal research, respect platform terms, and never bypass paywalls or verification.
- Do not retain personal data from comments or accounts; do not name private individuals in the report.

### Source grades

Label each data point with its grade:

| Grade | Source type | Examples |
|---|---|---|
| A | Official | Creator dashboards, official policy pages, official announcements and creator-program pages, official trend tools (Google Trends, TikTok Creative Center, Meta Ad Library) |
| B | Third-party data platforms | Global: Social Blade, vidIQ, TubeBuddy, Playboard, Noxinfluencer, Kalodata, FastMoss, SimilarWeb, Semrush, Ahrefs. China: Chanmama, Feigua, Xinbang, Newrank, Qiangua, Huitun, etc. (subject to what the user actually has and current features) |
| C | Public cases and industry material | Industry reports, media coverage, creators' public retrospectives, platform enforcement cases |

Integration rules:
1. Third-party figures are mostly estimates, not true backend data. Say so in the report.
2. Cross-check each metric with at least 2 sources. If they differ by more than 30%, list the gap and likely causes (definitions, sampling, update timing).
3. Prefer user-provided exports; record platform name, export date, and filters.
4. Metric definitions differ across platforms. Compare across platforms using **rank and relative ratios**, not raw absolute numbers.

### Fallback rules (run to the end without interrupting the user)

| Situation | Handling |
|---|---|
| Login expired | Record it, fall back to public data, continue |
| Captcha / slider / human verification | Do not attempt to bypass; skip the page, continue |
| Risk control or rate limiting triggered | Stop collecting from that platform immediately; slow down or switch to public data |
| Paywall / feature not enabled | Do not bypass; use free entry points or other sources |
| Missing or conflicting data | Mark "no reliable data" or list the conflict; do not invent |

All skipped or degraded items are summarized at the end under "Incomplete items and data limits".

---

## Step 2: High-quality benchmark sample filtering

Filter before analyzing. Default thresholds (adjust per niche, and **state the reason for any adjustment**):

| Dimension | Default standard |
|---|---|
| Account size | Prefer mid-tier / active accounts, with the follower band set by niche (e.g. 10k–500k); top accounts are reference only |
| Activity | ≥ 8 posts in the last 30 days (daily-update niches) or ≥ 4 (weekly niches) |
| View-to-follower ratio | Average views of the last 20 posts / followers ≥ niche median |
| Engagement authenticity | Comment/like and save/like ratios within the niche's normal range; no mass duplicate comments or empty accounts engaging |
| Conversion intent | Share of high-intent comment phrases (where to buy / how to join / price / link please) |
| Exclusions | Obvious reposts, matrix-account clones, suspected inflated views, recently penalized or restricted accounts |
| Sample size | At least 10 accounts per niche; if fewer, note "sample insufficient, conclusions for reference only" |

Attach the sample list (account, platform, followers, data date) at the end of the report for the user to review afterward. Do not pause mid-run for confirmation.

## Step 3: Sub-niche handling

- **User chose a specific direction**: analyze only that. Write regional (domestic/overseas) and account-type (individual/business) rule differences separately.
- **User chose "all" or "you decide"**:
  1. Output a **sub-niche overview table**: sub-niche | one-line assessment | compliance difficulty | competition | monetization ceiling.
  2. Pick **3** for deep dives based on traction, compliance difficulty, and fit with the user's credentials; state the selection basis.
  3. The rest stay in the overview only; the user can later ask to expand any of them.

---

## Global and regional supplement (mandatory when the target platform is overseas or the niche involves going global)

### G1. Platforms and official programs (names and entry points only; thresholds must be verified on official pages)
- YouTube: Partner Program (YPP), Shorts monetization, memberships, shopping features
- TikTok: Creator Rewards Program, TikTok Shop and its affiliate program, Creator Marketplace
- Instagram / Facebook (Meta): content monetization and brand-partnership tools
- X, Pinterest, Reddit, LinkedIn, Twitch, and independent monetization platforms such as Substack, Patreon, Gumroad

### G2. Regional eligibility differences
- Programs are open to different countries and the lists change. Third-party articles often disagree with each other. **Always rely on the official page**; mark "to be verified" if it cannot be found.
- Write the **creator's location** and the **target audience's location** separately in the report. When they differ, evaluate eligibility, earnings, and compliance separately.
- CPM/RPM varies widely by country. Give earnings ranges per target-audience country, with a single currency and the exchange-rate date.

### G3. Compliance dimensions (list by category; verify specific provisions via search before citing)
- Advertising and sponsorship disclosure (e.g. FTC in the US, ASA/CMA in the UK, EU rules)
- Heavily regulated content: financial and investment (including crypto), health and medical, weight loss, gambling — regulators in many regions set specific rules on influencer promotion
- Copyright and music licensing (e.g. DMCA, Content ID)
- Privacy and data (e.g. GDPR, CCPA), especially when collecting emails or running communities
- AI-generated content disclosure and platform policies
- Protection of minors

### G4. Overseas owned audience and payments
- Forms: email list / newsletter (the core owned channel overseas), Discord, Telegram, WhatsApp, paid communities and subscription platforms
- Payments and delivery: Stripe, PayPal, Gumroad, etc.; typical price ranges and fees
- Tax and payouts: platform tax-information requirements, cross-border payouts, VAT — all marked "to be verified", with a reminder to consult a professional
- Affiliate: Amazon Associates, affiliate networks (e.g. Impact, CJ), TikTok Shop affiliate

### G5. Funnel metrics overseas
Typical chain: views → profile click → link-in-bio click → email signup / community join → paid. Still output as "range + source + confidence", and split by country.

---

## Module 1: Platform rules map

### 1.1 Absolute red lines (not allowed)
- Credential red lines: what content requires licenses or qualifications (e.g. financial advice, medical, education, food and drugs, cross-border permits)
- Prohibited content and wording **by category** (do not list substitute words that evade filters)
- Banned visual or information elements
- Acquisition actions that lead to bans or restrictions

### 1.2 Official green lights and support
- Content directions the platform explicitly encourages
- Official monetization and support programs (creator programs, brand-deal marketplaces, niche-specific incentives, e-commerce onboarding and affiliate rules, YPP and tax requirements, etc.)

**For every policy, include**: policy name | eligibility conditions | official source link or dashboard entry | retrieval date. If no official link can be found, mark "to be verified". Never write specific thresholds from memory.

### 1.3 Peer risk profile (identify, grade, replace — never teach)

| Peer practice (category-level summary) | Risk level | Enforcement cases / rule basis | Outdated and high-risk? | Compliant alternative |
|---|---|---|---|---|

- Do not provide reusable steps, substitute-word lists, or interface-masking techniques.
- Mark previously common tactics that platforms have since tightened as "outdated, high-risk".
- A compliant alternative must serve a similar business purpose.

### 1.4 Compliance self-check
Against 1.1, check the user's identity and business form item by item: ✅ pass / ⚠️ needs more / ❌ not allowed, stating which credential or material is missing.

## Module 2: Acquisition and monetization path

### 2.1 Compliant public-domain acquisition
Break down **publicly visible** peer methods and judge their compliance: profile bio and officially allowed contact fields, official platform tools (business/creator account components, official DM tools, fan groups, shops/storefronts, official brand-deal platforms), series and playlists.

Comment-section interception: record only what peers do and the enforcement risk; output no scripts. Recommended alternative: "build search-led capture under your own content + convert through official tools".

### 2.2 Front-end (public) monetization
Ad revenue share, brand-deal / sponsorship pricing logic, compliant affiliate and commerce options.

### 2.3 Back-end (owned audience) monetization

| Product form | Price range | Delivery cost | Compliance risk | Source and confidence |
|---|---|---|---|---|

Examples: paid community, consulting/coaching, tool distribution, courses, custom services, supply-chain related e-commerce. Heavily regulated niches must have a separate "regulatory red lines" line.

## Module 3: Funnel conversion estimation

**Iron rules**:
- Give every ratio as a **range**, never a single number.
- Label each with source (grade A/B/C), sample description, and **confidence (high/medium/low)**.
- If there is no reliable basis, write "no reliable data" and tell the user how to measure it themselves.

| Stage | Estimated range | Source and sample | Confidence |
|---|---|---|---|
| Views → followers (new targeted followers per 10k views) | | | |
| Public → owned audience | | | |
| Owned audience → paid (low-ticket) | | | |
| Owned audience → paid (high-ticket) | | | |

### Break-even modeling
1. Target monthly revenue → paying customers needed → owned-audience size needed → followers / views needed
2. Add costs: content production, labor, paid traffic, tool subscriptions, platform fees, taxes
3. Output **conservative / neutral / optimistic** scenarios, with payback period and the most sensitive variable

---

## Additional modules

### A. Cross-platform role integration
Do not list platforms side by side. Write "the role each platform plays in this niche" (e.g. TikTok for conversion, Pinterest or Xiaohongshu for discovery and search demand) and how users move between platforms.

### B. Viral structure teardown
Summarize topic angles, hook types, length bands, posting-time patterns, thumbnail/title types. Pattern summary only — no copy.

### C. Comment demand mining
Count frequent questions, pain-point words, and purchase-intent word share. Output "top N real user needs".

### D. Competitor account matrix

| Account | Platform | Followers | Posts in last 30 days | Avg views | Engagement rate | Monetization form | Price point | Data source |
|---|---|---|---|---|---|---|---|---|

### E. Differentiation angles
From the competitor matrix and comment demand, find "high demand, low supply" gaps and suggest positioning directions (no copy).

### F. Niche feasibility scorecard
For each deep-dive niche, score 1–5 with reasons: compliance difficulty (harder = lower), competition, monetization ceiling, fit with the user's credentials, startup cost. End with a verdict — **Go / Caution / No-go** — and list the preconditions for "Go".

### G. Small-scale validation plan (2–4 weeks)
Funnel numbers are only estimates, so attach a test plan:
- Number and cadence of posts
- Metrics to record: views, completion rate, engagement, profile clicks, owned-audience signups, sales
- Pass criterion: the lower bound of the estimated range
- Stop-loss line: when to stop or pivot
- Remind the user to replace the report's estimates with their own real data

### H. Risk prioritization
Tag every recommendation with: **expected payoff / probability of penalty / consequence of penalty**, sorted from "high payoff, low risk" first.

---

## AI self-audit and correction (mandatory before output)

Audit by tracing sources, not by rereading:
1. Trace each key conclusion to its source; if none, downgrade to "to be verified" or delete.
2. Check numerical consistency: do funnel stages multiply to the break-even result? Do ranges contradict?
3. Compliance check: any evasion details, substitute-word lists, copy, or slogans? If so, delete and convert to a risk profile.
4. Completeness check: all modules, sub-niches, official policy links and retrieval dates present; sample size met or disclosed.
5. Privacy check: any private individuals named or personal data included?
6. Attribution check: attribution appears once, at the very end; omitted if the user asked to remove it.
7. Global check: for overseas targets, creator location and audience location written separately, and policies verified on official pages.
8. Tier consistency check: does the stated tier match actual capability? In Tiers 2–3, remove any specific accounts, numbers, or links that cannot be supported and replace them with "could not be completed in this run".

Fix issues directly, and keep one line at the end: "Self-audit corrections".

## Output template

1. **One-page summary**: verdict (Go / Caution / No-go and preconditions), 3 key findings, 3 biggest risks
2. **Data notes**: **run tier (1/2/3) and its data limits** (first line of the report), sample size, sources and dates, definitions, confidence overview, incomplete items and data limits
3. **Sub-niche overview** (if applicable)
4. **Module 1** → **Module 2** → **Module 3**
5. **Additional analysis**: A–H
6. **Small-scale validation plan**
7. **Appendix**: sample list, items to verify, self-audit corrections, next review date
8. **Optional accuracy upgrades** (required for Tiers 2–3): what extra data or tools would make the conclusions more accurate; optional, does not affect this output
9. **Attribution** (last line; see "Attribution and contact")

On mobile, lead with the summary and then ask which module the user wants expanded, instead of dumping everything at once.

## Attribution and contact (transparent, can be turned off)

- Add **one** attribution line at the **very end** of the report. It appears **once per report**, never inside the body, never repeated, never presented as part of the analysis.
- Fixed format: `Generated by "Niche Compass (寻道罗盘)" | Author: WeChat asaashuai / Telegram https://t.me/wozaiicu / X https://x.com/asicuuu` (the author fills this in before publishing).
- If the user says "no attribution" or "remove the contact info", or otherwise indicates they don't want it, **omit the line immediately**.
- Never push, prompt, or repeatedly mention the author's contact details in any other way. Never disguise the attribution as a data source or official information.
- The author can permanently disable it by deleting this section (documented in the README).

## Freshness and retention

- Add a retrieval date to every platform rule and policy. Recommend re-verifying every 30–60 days.
- When a rule change is found, record: "change | date of change | impact".
- Keep the sample list and data dates from each analysis so reruns can show what changed.
