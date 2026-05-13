# claude-skill-hormozi-offer-audit

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Built for Claude](https://img.shields.io/badge/Built%20for-Claude-D97757)](https://claude.com)
[![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)](#)

> A Claude skill that audits an existing sales offer (landing page, pricing tier, or lead magnet) using Alex Hormozi's frameworks from $100M Offers and $100M Leads. Returns a scored audit with prioritized fixes.

You drop your landing page, your pricing tier, or your lead magnet into Claude. The skill scores the offer against the Value Equation, runs the Grand Slam checklist, and returns a Top 3 Fixes block you can ship the same day.

This skill audits offers. It does not generate them from scratch. If you want a generator, look elsewhere.

---

## Why this skill exists

Most online tools that mention Hormozi's frameworks are generators. They build offers from a blank page. That is useful when you have nothing. It is the wrong shape when you already have a live landing page, a published pricing tier, or a lead magnet pulling weak opt-in numbers and you want to know what to change.

This skill is audit-first. You bring an existing offer. The skill scores it on four levers, names the weakest one, and gives you three concrete fixes ranked by impact-to-effort. The output is reviewable in 5 minutes and shippable the same day.

It covers both books: $100M Offers (Value Equation, Grand Slam, Pre-Offer Market Filter) and $100M Leads (lead magnet definition and quality bar). It does not pretend to know step-by-step builds the books do not document the same way online interpretations do.

---

## Install

Skills do not sync across surfaces (per [Anthropic's Agent Skills docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview#cross-surface-availability)). Install on each surface where you want to run this skill.

### Claude Code (CLI)

Two paths. Use git clone today; the plugin marketplace listing is pending Anthropic approval.

**Option A: git clone (works today).** Clone the repo and load it with the `--plugin-dir` flag:

```bash
git clone https://github.com/johnericforte/claude-skill-hormozi-offer-audit.git ~/claude-plugins/hormozi-offer-audit
claude --plugin-dir ~/claude-plugins/hormozi-offer-audit
```

To verify the plugin loaded, run `/help` in Claude Code. You should see `hormozi-offer-audit:audit` listed.

**Option B: Plugin marketplace (pending Anthropic approval).** Once the listing lands:

```
/plugin install hormozi-offer-audit
```

### claude.ai (web) / Claude Desktop

ZIP the `skills/audit/` directory and upload it via **Settings → Features → Skills** on claude.ai. The skill syncs to Claude Desktop through your account. Requires a Pro, Max, Team, or Enterprise plan with code execution enabled. See [Anthropic's docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) for plan requirements and limits.

### Invocation (Claude Code)

Once loaded in Claude Code, invoke the skill with the plugin-namespaced name:

```
/hormozi-offer-audit:audit
```

### Optional dependency: `humanizer`

The skill works best with the [`humanizer`](https://github.com/blader/humanizer) skill installed for the final pass on the audit's "After" copy. The first time you invoke this skill, it will check for `humanizer` and OFFER to install it for you (with your explicit approval). You can accept, decline, or install it manually:

```bash
git clone https://github.com/blader/humanizer.git ~/.claude/skills/humanizer
```

`humanizer` is a standalone skill (not a plugin), so it installs to the standard `~/.claude/skills/` directory.

If you decline, the skill ships the audit without the humanizer pass and labels it accordingly.

---

## Quick start

Once installed, invoke the skill via Claude:

```
Use the hormozi-offer-audit:audit skill on this landing page hero:

"Cliently is the all-in-one client management tool. Powerful features. Easy to use. Try free for 14 days."

I am a SaaS founder. The buyer is a service agency. Skip pre-audit research; I know my market.
```

Claude will:

1. Confirm offer type (paid offer) and input format (copy-pasted text)
2. Skip the pre-audit research mode (you opted out)
3. Score the Value Equation, 0-25 per lever
4. Output a Top 3 Fixes block with before/after examples
5. Run the Grand Slam Enhancement Audit
6. Optionally invoke the `humanizer` skill on the "After" copy if you have it installed

---

## Demo

### Before (the input you give Claude)

> "Cliently is the all-in-one client management tool. Powerful features. Easy to use. Try free for 14 days."

### After (the audit Claude returns)

**Audit Score Block:**

- Overall: 28 / 100
- Dream Outcome: 4 / 25. "Client management tool" is a category, not an outcome.
- Perceived Likelihood: 6 / 25. "Powerful" and "easy to use" are claims without proof.
- Time Delay: 8 / 25. "Try free for 14 days" does not promise what the buyer sees by Day 14.
- Effort & Sacrifice: 10 / 25. The offer says nothing about setup time, data migration, or team training.

Weakest lever: **Dream Outcome.**

**Top 3 Fixes:**

1. **Replace category with outcome (Dream Outcome).**
   - Before: "Cliently is the all-in-one client management tool."
   - After: "Cut your client no-show rate by 40% inside 30 days."

2. **Add proof inline (Perceived Likelihood).**
   - Before: "Powerful features."
   - After: "Used by 1,200+ agencies. Average no-show drop: 38% in the first month. Case study: Acme Agency, May 2025."

3. **Compress the time-to-value claim (Time Delay).**
   - Before: "Try free for 14 days."
   - After: "Connect your calendar in 5 minutes. See your first reduction in no-shows within 7 days."

**Grand Slam Enhancement Audit:**

Scarcity: not present. Urgency: not present. Bonus stack: not present. Guarantee: weak (free trial only). Naming: M.A.G.I.C. score 1/5.

---

## Use cases

- SaaS founder rewriting a landing page hero before a launch
- Course creator pricing a new program against the Value Equation
- Freelancer building a service tier ladder with Grand Slam mechanics
- Agency owner auditing a lead magnet that is underperforming on opt-in rate
- E-commerce brand stacking bonuses into a product launch offer
- Coach or consultant scoring an existing sales page for the weakest lever before A/B testing

---

## How it works

The skill follows a 7-step audit workflow:

1. **Confirm offer type and input format.** Paid offer routes to the Grand Slam path. Lead magnet routes to the Quality Bar path.
2. **Offer pre-audit research mode.** Optional. The skill asks per dimension (Dream Outcome, target buyer, market filter signals) whether you want a research agent to fill in missing inputs. You can skip and go straight to the audit using only what you provided.
3. **Extract intent dimensions.** Buyer, current price, stack contents, distribution. Clarifying questions if any critical dimension is still missing after the optional research.
4. **Score the Value Equation.** 0-25 per lever. Show the math. Flag the weakest lever.
5. **Run the Grand Slam audit** (paid offer) OR the **Quality Bar check** (lead magnet).
6. **Output the Audit Score Block + Top 3 Fixes.** Each fix targets a specific lever and includes a before/after example.
7. **Final humanization pass.** If you have the [`humanizer`](https://github.com/blader/humanizer) skill installed, the skill invokes it on the "After" copy in the Top 3 Fixes block. If not installed, the audit ships as-is.

The full mechanic, including the framework definitions and scoring rubric, lives in [`SKILL.md`](./SKILL.md). Reference cards for each framework live in [`references/`](./references/).

---

## Companion skills

These pair well with `hormozi-offer-audit`:

- **[`humanizer`](https://github.com/blader/humanizer)**: strips AI vocabulary, em-dash overuse, rule-of-three padding, and other AI-writing tells from the "After" copy in your audit. Invoked automatically by this skill if installed.
- **[`cialdini-influence-audit`](https://github.com/johnericforte/claude-skill-cialdini-influence-audit)**: audits the same offer copy for missing influence principles (the 7 Cialdini principles plus Pre-Suasion).
- **[`claude-blog-assistant`](https://github.com/johnericforte/claude-skill-blog-assistant)**: if the offer lives inside a blog post, this orchestrator wraps the full publishing lifecycle AND audits existing posts. Pair with the Hormozi offer audit when shipping new blog content.

You do not need either to run this skill. Both raise the quality of the output if installed.

---

## FAQ

**Is this skill affiliated with Alex Hormozi?**

No. This is an independent open-source tool. It is not affiliated with, endorsed by, or sponsored by Alex Hormozi, Bumble IP LLC, or Acquisition.com. Frameworks are referenced descriptively under nominative fair use. See [`DISCLAIMER.md`](./DISCLAIMER.md).

**Is this a substitute for reading the books?**

No. The books are the source of truth. This skill is a derivative reference for audit-tool use. If your work depends on the frameworks, read the books.

**Can I use this for commercial work?**

Yes. The skill is MIT-licensed. You can use it on client work, paid audits, and any other commercial application.

**Why is there no step-by-step lead magnet build framework in the skill?**

Published "step-by-step" lead magnet builds attributed to Hormozi online are typically third-party interpretations, not direct Hormozi material. To stay accurate, this skill audits lead magnets against the Quality Bar (4 items) only. The canonical step-by-step build lives in the book. See [`references/lead-magnet.md`](./references/lead-magnet.md) for details.

**Does the skill work with tools other than Claude Code?**

The skill is written in the Claude Code skill format (`SKILL.md` + frontmatter). It also works in OpenCode, which uses the same skill format. For other tools, you may need to adapt the format manually.

**What if I want a tool that GENERATES offers from scratch instead of auditing existing ones?**

This skill is audit-first. For generation, look at other skills in the ecosystem (e.g., `wondelai/skills/hundred-million-offers`).

**How do I update the skill when Hormozi publishes new material?**

Open an issue or pull request on the repo. Framework updates and corrections are welcome.

---

## Sources & attribution

Frameworks referenced descriptively under nominative fair use. Not affiliated with or endorsed by Alex Hormozi, Bumble IP LLC, or Acquisition.com.

**Primary sources (the books are the source of truth):**

- Hormozi, Alex. _$100M Offers: How To Make Offers So Good People Feel Stupid Saying No_. 2021.
- Hormozi, Alex. _$100M Leads: How to Get Strangers To Want To Buy Your Stuff_. 2023.

**Verified online references:**

- [Acquisition.com books hub](https://www.acquisition.com/books)
- [Acquisition.com free Offers course](https://www.acquisition.com/training/offers) (includes "The Value Equation" module)
- [Acquisition.com free Leads course](https://www.acquisition.com/training/leads) (includes "Lead Magnet Mastery" module)

Full source list, third-party summaries used during research, and the verification status of every framework definition: [`references/sources.md`](./references/sources.md).

For the full disclaimer on trademarks, fair use, and the limits of this skill, see [`DISCLAIMER.md`](./DISCLAIMER.md).

---

## Contributing

Pull requests welcome. Especially:

- Framework verification corrections (cite the book chapter and edition)
- Additional worked examples in `references/examples/` (one example per industry vertical)
- Bug reports on audit logic that misfires on real offers

For framework misattribution or trademark concerns, open an issue or contact the maintainer through the channels in the Author section below. The author will respond and adjust in good faith.

---

## Author

Built by **Eric Forte**, AI Automation Engineer for GoHighLevel Marketing Agencies.

- Website: [ericforte.com](https://www.ericforte.com)
- Blog: [ericforte.com/blog](https://www.ericforte.com/blog)
- LinkedIn: [@johnericforte](https://www.linkedin.com/in/johnericforte/)

---

## License

[MIT](./LICENSE) © 2026 Eric Forte
