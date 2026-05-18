# Blog Editorial Review

Use this when reviewing Chinese blog posts, technical notes, Markdown drafts, and long-form articles. The goal is to give actionable editorial feedback, not to take over authorship.

Treat this like code review for articles:

- Report concrete issues, not vague preferences.
- Provide evidence from the draft.
- Explain impact on readers, correctness, or credibility.
- Suggest a path forward, but do not rewrite the author's work unless asked.
- Do not force findings. If a dimension has no meaningful issue, omit it.

## Review Priorities

First check the author's core editorial concerns:

1. **Title fit**: The article must deliver what the title promises. If a title promises depth but the body is only introductory, suggest either narrowing the title or expanding the article.
2. **Topic focus**: The article must stay on topic. Flag digressions that do not support the main question.
3. **Style and fluency**: Preserve the author's voice, but flag abrupt jumps, unclear transitions, and inconsistent tone.
4. **Professional accuracy**: Find factual, conceptual, technical, or code-level mistakes. Accuracy issues outrank style issues.

Then check these additional editorial dimensions:

1. **Structure and argument chain**: Does the article move from problem to reasoning to conclusion, or does it only list disconnected points?
2. **Evidence and examples**: Are claims supported by examples, code, comparisons, counterexamples, data, references, or experience?
3. **Audience fit**: Is the depth appropriate for the intended reader level? Are prerequisites introduced before use?
4. **Originality and reader value**: What does the article add beyond documentation or search-result summaries?
5. **Boundaries and applicability**: Are strong claims limited by context, versions, tradeoffs, and exceptions?
6. **Attribution and risk**: Are quotes, screenshots, code, charts, data, and external claims properly attributed?
7. **Verifiability**: Can technical claims, product behavior, version details, benchmarks, and standards be checked against reliable sources?
8. **Chinese writing pitfalls**: Word-level errors (grammatical-particle confusion like `的得地`, homophone substitutions like `登录/登陆`, near-character confusion, context-incompatible word substitutions even when each word is individually valid, quantifier mismatches, undefined acronyms), sentence-level issues (translation-ese, over-nominalization, `进行`/`性`/`化` overuse, long attributive chains, missing subjects, ambiguous pronouns, malformed sentences), and voice issues (empty intensifiers, clickbait wording, hollow closings, repeated paragraph-opening connectives).

Apply copy formatting from `rules.md` only after higher-priority content issues are covered.

## Dimensions

### Title and Promise

- Does the title match depth and scope?
- Are words like `深入理解`、`完全指南`、`最佳实践`、`原理`、`源码分析` supported by enough depth?
- If the article is introductory, suggest a modest title instead of forcing depth.
- If the title is strong and worth keeping, suggest missing sections needed to justify it.

### Topic Focus

- Identify the central question in one sentence.
- Mark paragraphs that do not support that question.
- Separate useful digressions from removable tangents.
- Suggest moving side topics to footnotes, appendices, or separate posts when appropriate.

### Structure and Flow

- Check whether the opening explains the problem, audience, and payoff.
- Check whether headings form a coherent outline.
- Look for missing transitions between concepts.
- Flag repeated points, abrupt jumps, and conclusions that introduce new claims too late.

Discourse-level pitfalls common in Chinese tech blogs:

- **首段未点题**: A technical post should make the reader understand "what problem this solves and whether to keep reading" within the first 150–200 characters. Drafts that open with industry context, history, or self-introduction before stating the problem tend to lose readers. Suggest cutting or moving the lead-in.
- **小标题与正文割裂**: After multiple revisions, H2 / H3 headings often drift from the paragraph content beneath them. Read each heading against its first paragraph. If they no longer match, either fix the heading or restructure the paragraph.
- **末段反问空转**: Endings like `你觉得呢？`、`你怎么看？`、`欢迎讨论` with no concrete pointer waste the ending slot. The last paragraph is high-attention real estate; use it for conclusions, limitations, next steps, or specific questions inviting concrete answers.
- **正文与目录承诺不一致**: When the article has an explicit outline (`本文将讨论 1/2/3`), check whether all promised sections actually appear and are roughly proportional to the promise.
- **章节比重失衡**: A section labeled as core (e.g., "核心实现") that takes one paragraph while the setup section takes ten paragraphs indicates a topic-focus problem, not a depth problem.

### Professional Accuracy

- Verify technical terminology, API behavior, version-specific claims, and causal explanations.
- For current facts, product behavior, benchmarks, standards, laws, or rapidly changing technology, verify with current primary sources before making firm claims.
- If unsure, say what needs verification instead of asserting.
- For code examples, check whether they are syntactically plausible, runnable in context, and aligned with the article's explanation.

### Evidence and Specificity

- Prefer concrete examples over abstract claims.
- Flag broad claims without support, especially `一定`、`所有`、`最佳`、`永远`、`本质上`.
- Check whether examples actually prove the point.
- Suggest adding diagrams, minimal examples, counterexamples, or tradeoffs when they would clarify the article.

### Audience Fit

- Infer the intended reader level: beginner, intermediate, advanced, or mixed.
- Flag unexplained prerequisites for beginners.
- Flag excessive basics in an article aimed at advanced readers.
- Check whether terminology is introduced before being used heavily.

### Originality and Value

- Ask what the article adds beyond common documentation or search-result summaries.
- Flag sections that feel like generic filler.
- Suggest adding personal experience, decision context, failure cases, comparison, or lessons learned when the article lacks a point of view.

### Style and Readability

- Preserve the author's natural style unless it harms clarity.
- Flag inconsistent tone, overly abrupt jokes, excessive abstraction, and paragraphs that are too dense.
- Suggest splitting long paragraphs, tightening repetitive sentences, or adding signposts.
- Avoid converting every draft into the same neutral corporate voice.

### Chinese Writing Pitfalls

Specific to Chinese technical writing. Flag patterns, do not auto-rewrite unless asked.

#### Word Choice

The four bullets below describe *categories* of character-level errors. The pairs and examples listed are anchors, not exhaustive lists. A typo that does not match any listed pair but creates a wrong word in context should still be flagged.

- **虚词与助词误用（非穷尽清单）**: 中文里最常踩的几组语法功能字配对，判定规则清晰：
  - `的 / 得 / 地`：定语用"的"（红色的车）、补语用"得"（跑得快）、状语用"地"（认真地写）。
  - `在 / 再`：表位置/状态用"在"（在工作）、表重复用"再"（再试一次）。
  - `做 / 作`：具体动作用"做"（做饭、做项目）、抽象/书面用"作"（作为、作出决定）。
  - `像 / 象`：相似用"像"（像 Python）、抽象事物用"象"（现象、对象）。
  - `帐 / 账`：金钱往来一律用"账"（账户、账单），不用"帐"。
  - `即 / 既`：表示"就是"用"即"（即代码 review）、表示"已经"用"既"（既然）。
  - `式 / 试`：方式用"式"（函数式）、尝试用"试"（试运行）。
- **同音异形词误用（IME 误植高发区）**: 拼音相同、写法不同、含义有别，是中文输入法最常生产的笔误来源。技术写作里高频对：
  - `登录 / 登陆`：账号场景一律用 `登录`；`登陆` 指物理登岸或大规模进入市场。
  - `部署 / 部属`：系统上线用 `部署`（deploy）；`部属` 是下属。
  - `配置 / 佩置`：`佩置` 不是标准词，技术写作一律 `配置`。
  - `截止 / 截至`：含义相反。`截止 6 月 30 日` 指到此为止；`截至 6 月 30 日` 指到这天为止仍在继续。
  - `必须 / 必需`：`必须` 修饰动作（必须执行）；`必需` 修饰名词（必需品、必需的依赖）。
  - `权利 / 权力`：`权利` 是可享受的（用户权利）；`权力` 是支配他人的能力。
  - `做为 / 作为`：标准写法是 `作为`。
  - `报错 / 抱错`：程序输出错误用 `报错`。
- **形近字误用**: 字形相近、含义不同。常见易混：`己 / 已 / 巳`、`末 / 未`、`戊 / 戌 / 戍`、`贷 / 货`、`暮 / 幕 / 墓`。技术文里影响最大的通常出现在变量命名、路径解释、版本号说明场景。
- **语境冲突的词误植（最难抓但最关键）**: 某个词单独看是合法中文，但在所在段落上下文里语义不通。常由 IME 自动选词或思维滑动产生。判定规则：扫描全文，对每个名词和动词在心里问一句"这个词在这一段的主题下读得通吗"，读不通就 flag——**即使该词独立看完全合法**。例如：
  - "用户登陆失败" —— 账号场景应为 `登录`，`登陆` 在这里逻辑不通。
  - "把版本回归到上一个 tag" —— 版本管理场景应为 `回滚`，`回归` 在 ML/统计领域才合适。
  - "把服务部属到生产环境" —— 应为 `部署`。
  - "这个函数返回值类型不一只" —— 应为 `不一致`。
  - 关键：清单外的错别字也要 flag，列出的只是常见锚点。

- **量词错配**: 中文量词与对象绑定，技术写作里高频错配：
  - 表 / 集合 → `一张表`、`一份数据集`，不是 `一个表`。
  - 数据 / 记录 → `一条数据`、`一条记录`，不是 `一个数据`。
  - 图片 / 截图 → `一张图片`、`一张截图`。
  - 文章 / 笔记 → `一篇文章`、`一篇笔记`。
  - 报错 / 异常 → `一处报错`、`一次异常`。
- **缩写未展开**: 缩写（`API`、`LLM`、`RAG`、`SLO`、`MTTR`、`CDN`、`RPC`、`CRDT` 等）在文章中首次出现时应给出展开形式或定义，至少对非高频术语如此。面向高级读者的文章可豁免，但要在开头声明读者层级。
- **空洞强调词**: `非常`、`极其`、`真的`、`其实`、`显然`、`众所周知`、`一定`、`必然`。删掉后语义通常不变，反而更紧。带"显然 / 众所周知"的句子尤其值得审视——常常隐含未经证明的前提。
- **标题党词汇**: `深入`、`一文`、`手把手`、`万字长文`、`保姆级`、`必看`、`完全指南`、`最佳实践`、`从入门到精通`、`源码剖析`。这些词本身不是错，但要兑现承诺。如果正文撑不住，建议换词。

#### Sentence Structure

- **翻译腔 / 英式中文**: 直译英文句式而生硬的表达。常见标记：`使得...能够...`、`基于...的`、`一个...的事实`、`关于...而言`、`在...的情况下`、被动语态滥用（`被认为是`、`被广泛使用`）。建议改写成主动、短句、动词驱动的中文。
- **过度名词化**: 动词变名词导致句子虚空。例如 `进行优化` → `优化`，`做出选择` → `选择`，`实现了对 X 的处理` → `处理了 X`。
- **"进行 + 双字动词" 滥用**: `进行优化`、`进行讨论`、`进行测试`、`进行分析`、`进行部署`。"进行"几乎都可删，直接用后面的动词。
- **"性 / 化" 字尾堆叠**: `重要性`、`必要性`、`可能性`、`复杂性`、`稳定性`；`简化`、`深化`、`细化`、`本地化`、`抽象化`。单用没问题，但同一段三个以上同尾抽象名词就该警觉，多半是空话。
- **"对 ... 进行 ... 的" 翻译腔三连**: `对系统进行性能调优的工作` → `调优系统性能`；`对用户输入进行校验的逻辑` → `校验用户输入`。这是中文技术写作里最显著的"AI / 翻译" 味。
- **长定语堆叠**: 名词前挂多层 `的`。例如 `一个用于处理用户输入验证的可复用的工具函数` → `一个可复用的用户输入校验函数`。一般 `的` 之前超过 12 字就该断。
- **主语缺失或漂移**: 中文允许省略主语，但技术文章里容易让读者搞不清"谁在做什么"。尤其在讲框架行为、用户操作、系统进程切换时要补主语。
- **"的的不休" / "了了不止"**: 同一句多个 `的` 或多个 `了` 累积，节奏拖沓。
- **指代不明的"这 / 那 / 它 / 其"**: 当上文出现多个名词时，代词的先行词不清。例如"我们把日志写到 S3，然后用 Athena 查询，**它**很慢"——"它"指 S3、Athena、还是查询本身？要么补名词，要么重写。
- **病句**: 三类常见：
  - 搭配不当：`提高质量和速度` —— 质量"提高"、速度通常"加快"，建议拆。
  - 成分残缺：缺主语或谓语，常见于长复合句。
  - 结构混乱：一句话切两半、前后逻辑不衔接；建议拆成两到三句。

#### Voice and Closing

- **滥用 "我们"**: 教程里习惯性 `我们来看一下`、`我们可以发现`，过密时显得空洞。技术性陈述优先用客观句。
- **句首连接词高频重复**: `所以`、`但是`、`而且`、`其实`、`然后`、`不过`。同一连接词连续 3 段及以上的段首出现就要警觉——这通常意味着段落之间缺少真正的逻辑切换，作者用连接词制造了"过渡感"假象。建议要么重写段间关系、要么删除冗余连接词。
- **空话结尾**: `希望这篇文章对你有帮助`、`让我们一起进步`、`如果你喜欢请点赞`。技术博客的结尾应该是结论、限制、下一步或参考，不是问候。

### Risk and Attribution

- Flag uncited quotes, copied passages, screenshots, code, charts, and data.
- Check whether external claims need links or attribution.
- Flag potentially misleading, overconfident, or harmful advice.

### Boundaries and Applicability

- Flag claims that are too absolute for the evidence.
- Check whether recommendations specify versions, assumptions, environment, scale, and tradeoffs.
- Suggest adding exceptions or constraints when advice depends on context.

### Verifiability

For drafts with technical, factual, version-sensitive, or empirical claims, load `verifiability.md` and apply:

- Primary source mapping (which kind of source counts as primary for each claim type).
- Time-sensitivity tiers (how soon a claim decays).
- Four-state annotation (`已核实-来源 X` / `待核实-需查 X` / `推断-基于 X` / `不可核实-观点性表达`).
- AI-hallucination patterns (fabricated APIs, packages, version numbers, quotes, perfectly symmetric structures).
- Second-hand information handling (`据说 / 听说 / 网上说`).
- Link rot mitigations.

For purely opinion-driven or experience-report articles, this dimension can be skipped.

## Output Format

Start with a short verdict:

- `可发布`
- `小修后发布`
- `需要大修`
- `暂不建议发布`

Then use this structure:

1. **结论**: One short paragraph with the overall publishability assessment.
2. **必须修改**: Blocking issues that should be fixed before publication.
3. **建议修改**: Non-blocking changes that would materially improve the article.
4. **可选优化**: Style, flow, formatting, or polish suggestions.
5. **需要作者确认**: Questions only the author can answer, such as intended audience, scope, title promise, or missing experience.
6. **事实核查**: Claims that are verified, need verification, or should cite sources.

Each finding should include:

- `问题`: concrete issue.
- `证据`: quote or location from the draft.
- `影响`: why it matters.
- `建议`: what the author can do.

Use these severities inside findings:

- `严重`: wrong topic, major factual error, misleading technical claim, broken core argument.
- `中等`: weak structure, insufficient evidence, unclear audience, major omissions.
- `轻微`: wording, transitions, copy formatting, minor consistency issues.

### Mini Template

Use this as the output shape. Omit sections that have no applicable issue; do not pad.

```
结论: 小修后发布。标题与内容匹配，存在一处事实表述需修正和若干轻微表达问题。

## 必须修改

### 严重: useEffect 执行时机表述错误

- 问题: 文章说 "useEffect 每次都会在渲染之前同步执行"。
- 证据: 原文第二段。
- 影响: 这是核心概念错误，会误导读者将同步布局逻辑写进 useEffect。
- 建议: 区分 useEffect 与 useLayoutEffect 的执行时机后修正解释。

## 可选优化

- `非常强大` 是空洞强调词，删除后语义不变（Word Choice > 空洞强调词）。

## 事实核查

- 待核实-需查 React 官方文档 useEffect 章节: useEffect 是异步在 commit 之后执行，非渲染前同步执行。
```

Notes on the template:

- Verdict is one line at the very top.
- Each finding cites a finding category from `Chinese Writing Pitfalls` or another section when applicable, so the author can look up the rule.
- Fact-check items use the four-state annotation from `verifiability.md`.
- A real review usually spans more sections; this template is a shape reference, not a length target.

End with optional next steps:

- Title options when title/content mismatch exists.
- Missing sections when content needs expansion.
- Fact-check items when sources are needed.
- Copy formatting notes when the content-level review is done.

## Handling Disagreement

Authors will push back. That is healthy, not a signal to retract a real finding. Use these rules:

- **Severity is not negotiable on facts.** If a finding is `严重` because of a factual or technical error, do not downgrade it just because the author disagrees. Ask for evidence instead and stand by the source.
- **Style and voice findings are negotiable.** `轻微` items about wording, tone, or pacing should yield to the author's preference once acknowledged. Restate the tradeoff, then drop it.
- **Title and scope findings are author-led.** The reviewer flags the mismatch; the author chooses whether to fix the title or expand the content. Do not pick for them.
- **Audience and intent are author-only.** If the author clarifies the intended reader or purpose, update the review against that new context. Do not insist on the original assumption.
- **Repeat findings get one restatement.** If the same issue is pushed back twice, restate the evidence one more time, then mark it as `作者已知` and move on. Do not escalate.
- **Never invent a compromise to please the author.** If there is no middle ground (for example, a wrong API claim), say so plainly.
