# Pre-Offer Market Filter

> Source: Alex Hormozi, _$100M Offers_ (2021). Framework cited descriptively under nominative fair use.

## Why this exists

A great offer in a bad market still loses. Run this filter BEFORE auditing the offer's internals. If the market fails 2+ indicators, the offer ceiling is capped no matter how good the audit fixes are.

## The four indicators

### 1. Massive pain

The market feels the problem acutely, not academically. The buyer would describe the pain unprompted.

- ✅ Pass: SaaS founders losing $50K/mo to churn. Restaurants drowning in no-shows. Agencies burned out on retainer scope creep.
- ❌ Fail: "It would be nice to have." Pain is theoretical, not operational.

Audit signal: does the buyer's day-to-day get materially better when the pain goes away?

### 2. Purchasing power

The market can afford to buy. This is about willingness AND ability.

- ✅ Pass: B2B SaaS founders with $100K+ ARR. Established agencies. Enterprises with budget cycles.
- ❌ Fail: College students. Pre-revenue founders. Hobbyists. "It's expensive but maybe one day."

Audit signal: is there an existing line item in the buyer's budget that this could come out of?

### 3. Easy to target

You can find the buyers without burning the marketing budget on broad audiences.

- ✅ Pass: SaaS founders on LinkedIn (filter by title, company size, industry). Restaurant owners on Google Maps. Real-estate investors at REI meetups.
- ❌ Fail: "People who care about productivity." "Anyone running a business." "Mid-market." (No identifiable acquisition channel.)

Audit signal: name the EXACT channel + filter you would use to reach 100 of these buyers tomorrow.

### 4. Growing market

The market is expanding, not shrinking. Growing markets forgive offer mistakes; shrinking markets punish even great offers.

- ✅ Pass: AI infrastructure (growing). Home services (steady-to-growing). Niche SaaS verticals (growing).
- ❌ Fail: Print newspapers. Generic web design. Categories disrupted by AI in the last 18 months.

Audit signal: what does the market look like in 3 years? If it's smaller, the offer's runway is short.

## Scoring

Score each indicator: PASS / WEAK / FAIL.

| Indicators failing | Verdict |
| ------------------ | ------- |
| 0 of 4             | Strong market. Offer audit fixes will compound. |
| 1 of 4             | Manageable. Note the failed indicator and design around it. |
| 2 of 4             | Capped ceiling. Audit fixes help but the market won't reward great offers proportionally. |
| 3 of 4             | Wrong market. Recommend repositioning before more offer work. |
| 4 of 4             | Stop. The offer doesn't have a market. Switch projects. |

## When to run this filter

- ✅ Always: before scoring a brand-new offer
- ✅ Before pricing decisions: if the market fails on purchasing power, even a perfect Value Equation won't justify the price
- ✅ Before a launch: a market filter check catches "great offer, wrong audience" before ad spend ramps
- ❌ Skip: routine A/B test work where the market is already proven

## Audit output format

```
Market filter:
  Massive pain:        PASS — buyers describe the pain unprompted in 8/10 discovery calls.
  Purchasing power:    WEAK — buyers have budget but it sits in a different department.
  Easy to target:      PASS — LinkedIn Sales Navigator filters return 12,000 named accounts.
  Growing market:      PASS — category up 34% YoY per Gartner 2025.

Verdict: 1 weak, 0 fails. Manageable. Design around the budget-routing issue (sell to the budget owner, not the user).
```
