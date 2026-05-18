# Verifiability and Fact-Checking

Use this reference when an article makes technical, factual, version-sensitive, or empirical claims. Load it on top of `review.md` when the draft's domain or claims warrant it.

## When to Load This

Load this reference when the draft contains any of:

- API behavior, default values, configuration semantics.
- Protocol or standard claims (RFC, W3C, ECMA, ISO).
- Performance numbers, benchmarks, latency / throughput / cost figures.
- Version-specific feature availability or release timeline.
- Legal, compliance, license, or policy claims.
- Company or product behavior statements.
- Direct quotes, statistics, or `据说 / 听说 / 网上说` style attributions.
- Pricing or SLA claims.
- Benchmarks, performance numbers, charts, screenshots, or statistics from surveys or studies.

Skip when the article is pure opinion, experience report, or tutorial whose claims do not depend on external facts.

## Primary Source Mapping

For each claim type, prefer primary sources. Secondary sources are acceptable only as supplements, not as the sole basis for a firm claim.

| Claim type | Primary source | Secondary (supplemental only) |
|---|---|---|
| API behavior, defaults | Official docs, source code | Stack Overflow, blog posts |
| Protocol / standard | RFC, W3C, ECMA, ISO | MDN (high-quality secondary) |
| Performance numbers | Self-measured + hardware/version/workload disclosure | Academic papers, benchmark sites |
| Version availability | Release notes, CHANGELOG, GitHub releases | Package manager pages |
| Legal / compliance | Regulation text, official interpretations | Lawyer blogs, news |
| Company statements | Official blog, SEC filings, press releases | Press coverage, social media |
| Pricing / SLA | Official pricing pages, contracts | Sales decks, third-party comparisons |
| AI model behavior / cost | Provider's official model card and pricing page | Aggregators, blog comparisons |

When the article cites a secondary source for a primary-source-class claim, flag it as `待核实-需查` and name the primary source to verify against.

## Time Sensitivity Tiers

Different domains decay at very different rates. Mark fact-check items with the decay tier so the reviewer knows how soon a recheck is needed.

- **6 months or sooner — recheck before publishing**:
  - Front-end framework APIs (React, Vue, Svelte, Next.js).
  - AI model names, capabilities, and pricing.
  - Cloud provider pricing, quotas, and SKU lineup.
  - SaaS product features and UI flows.
  - Fast-moving libraries (Bun, Deno, Vite, tRPC).
- **1 to 2 years — recheck if older**:
  - Programming language new features (after spec stabilizes).
  - Database engine features and behavior.
  - Container and orchestration tooling.
  - ORM and query builder behavior.
- **Long-term stable**:
  - Data structures and algorithm complexity.
  - TCP / HTTP / DNS protocol fundamentals.
  - Classic CS theory and mathematical claims.
  - Operating system fundamentals (process model, virtual memory, syscalls).

When in doubt, treat a claim as more time-sensitive than the author seems to assume. Tech writers frequently underestimate decay rate.

## Four-State Annotation

Replace vague "needs verification" with one of four explicit states. Each fact-check item should pick exactly one. Findings without one of these labels should be considered incomplete.

- `已核实-来源 X`: Verified against a specific primary source. The source link, document section, or version number must be included. Bare references like "official docs" without a section anchor do not satisfy this.
- `待核实-需查 X`: Not yet verified. The verification target must be named explicitly — which doc, which release notes, which RFC section, which official pricing page.
- `推断-基于 X`: An inference rather than a fact, with the reasoning basis stated. Useful when the author reasons from first principles but did not measure. Should not be presented as fact in the article body.
- `不可核实-观点性表达`: Opinion, aesthetic judgment, or experience report that is out of scope for fact-checking. Mark explicitly so it is not relitigated.

## AI-Generated Content Hallucination Patterns

Many drafts now start as AI output. The reviewer should treat the following patterns as suspect and require verification, even when the prose reads fluently. Prefix related findings with `AI 痕迹:` so the author understands the failure mode.

- **Fabricated APIs**: Function or method names that sound plausible but do not exist. Signature looks idiomatic (correct casing, conventional argument order), but no such function appears in the official reference. Always verify by searching the project's official API index directly, not via search engines.
- **Fabricated libraries or packages**: Generic-sounding names like `react-some-thing`, `python-fast-helper`, `vue-easy-state`. Search npm / PyPI / crates.io / pkg.go.dev directly. Do not trust the LLM's package recommendations.
- **Expired or invented version numbers**: "Since version 18.5" when 18.5 does not exist; "Python 3.13.2 introduced X" without checking. Always cross-reference the project's release page.
- **Widely-attributed but unsourced quotes or statistics**: "Research shows 70% of teams ...", "Linus once said ...", "Stack Overflow's 2023 survey found ...". If the citation cannot be traced to a specific paper, talk, interview, or survey URL, treat as fabricated.
- **Perfectly symmetric structures**: `3 优点 / 3 缺点 / 3 使用场景`, `5 步上手`, paragraphs of identical length. Real engineering rarely partitions this cleanly; the structure is an LLM artifact and often hides shallow content.
- **Over-hedged universalist phrasing**: Every claim wrapped in `虽然 ... 但是 ...`, every recommendation hedged with `在某些情况下 ...`. Reads neutral, says nothing.
- **Doc paraphrase without original perspective**: Sections that re-word the official docs without examples, tradeoffs, failure cases, or lived experience. Flag as "no added value vs. official docs" and either cut or replace with author's own experience.
- **Confident-but-wrong causal claims**: "X works this way because Y" where Y is a plausible-sounding but incorrect mechanism. Common in articles about garbage collection, event loops, lock semantics, and TCP behavior.

## Second-Hand Information Handling

When the draft uses `据说`, `听说`, `网上说`, `有人说`, `据传`, `据报道`:

- Require the original source. Suggest tracing back to the English original when the article cites a translation, because Chinese tech communities sometimes propagate the same mistranslation across years of reposts.
- If no source can be found, downgrade the claim to "作者经验" with an explicit author disclaimer, or remove it.
- For numerical claims (percentages, dollar amounts, benchmarks), no-source means delete — not downgrade. Numbers without sources are worse than no numbers.

## Data and Charts

Numbers and visuals carry disproportionate trust weight in technical writing. Hold them to a higher bar than prose.

### Performance Numbers

Every benchmark or perf claim needs at least these four disclosures. Missing any of them downgrades the claim from "evidence" to "anecdote":

- **Hardware**: CPU model, core count, RAM, storage class. For cloud benchmarks: instance type (e.g., `c7g.4xlarge`), region, and tenancy if relevant.
- **Software versions**: language runtime version, library versions, kernel/OS version when relevant.
- **Workload**: dataset size, concurrency, query mix, warmup behavior, measurement window. `1000 QPS` without describing the request shape is meaningless.
- **Measurement methodology**: which tool (`wrk`, `hey`, `pgbench`, custom), how many runs, p50 vs p99, cold vs warm cache.

For comparison benchmarks ("X is 3 times faster than Y"), additionally require:

- Both systems configured fairly (default vs tuned, single-node vs cluster).
- Same workload run against both.
- Statistical disclosure (variance, run count).

Flag perf claims that quote third-party benchmarks without re-verifying that the original benchmark's workload matches the author's claimed use case.

### Charts and Diagrams

When the draft includes a chart, screenshot, or hand-drawn diagram, require:

- **Axis labels and units**: Both axes labeled. Units explicit (ms vs s, MB vs MiB, requests vs requests-per-second).
- **Data source and collection time**: A line under the chart naming the source and when the data was collected. Charts older than 12 months in fast-moving domains (cloud pricing, AI model performance) should be re-collected before publishing.
- **No misleading truncation**: Y-axis not starting at zero must be flagged as such in the caption. Log scale must be labeled. Broken axes must be visible.
- **Sample size or run count**: Bar charts of latency or throughput should disclose how many runs the bar represents and whether it shows mean, median, or some percentile.

### Screenshots

Screenshots of UIs, dashboards, or terminals decay especially fast.

- **Timestamp or version context**: Either the screenshot includes a visible timestamp/version, or the caption states when it was captured and against which version.
- **Sensitive data redaction**: API keys, internal hostnames, user emails, customer names must be redacted. Note that blurring is often reversible — prefer opaque blocks.
- **Locale awareness**: A screenshot in a non-Chinese UI (or vice versa) should be acknowledged so readers do not think the UI changed.

### Statistics from Surveys, Studies, Reports

- Cite the specific survey or paper with title, year, and link, not just "research shows".
- Quote the sample size and methodology when the number drives a recommendation.
- Beware of vendor-published statistics — they are marketing input, not neutral evidence. Mark as `推断-基于 X` rather than `已核实` when the source is the vendor that profits from the conclusion.

## Link Rot

- Prefer permalinks: GitHub commit SHAs over branch tips, dated release notes over "latest", versioned doc URLs over canonical ones.
- For links likely to rot (vendor blog posts, news, marketing pages), suggest adding an `archive.org` snapshot link alongside the live URL.
- For already-404'd content, replace with an archive snapshot or remove the dependent claim entirely. Do not silently leave a dead link.

## Output Integration

When reporting findings under `事实核查` in the review output (see `review.md` Output Format):

- Tag each item with one of the four annotation states above.
- For `待核实-需查 X` items, name the source class to check (RFC number, release notes for version Y, official pricing page URL).
- For claims in the 6-month-or-sooner tier, additionally prefix the finding with `时效敏感:`.
- For AI-hallucination-pattern findings, additionally prefix with `AI 痕迹:`.
- Group `已核实` and `不可核实` items at the bottom so action items (`待核实` and `推断`) stay visible.
