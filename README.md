# Chinese Blog Review Skill

一个面向中文博客和技术文章的 Agent Skill。它把文章审稿当作 Code Review 来做：先指出问题、证据、影响和建议，不默认替作者重写。

## 适用场景

- 中文博客、Markdown 草稿、技术笔记、教程、长文审稿
- 检查标题是否兑现、内容是否偏题、结构是否清楚
- 检查技术概念、事实、代码示例和版本相关表述
- 检查证据、引用、读者价值、边界条件
- 在内容审稿完成后检查中文排版和中英文混排

## 不适用场景

- 自动改写整篇文章
- 批量格式化 Markdown
- 全自动事实核查（skill 会标记 `待核实-需查 X` 并识别 AI 幻觉模式，但作者仍需自行查证一手来源）
- 公司品牌文案、公众号运营稿、学术论文的专用审稿流程

这些场景可以基于本 skill 扩展，但当前版本优先服务个人中文博客和技术文章。

## 安装

从 GitHub 安装：

```bash
npx skills add yclgkd/chinese-blog-review-skill --skill chinese-blog-review
```

本地安装：

```bash
npx skills add /path/to/chinese-blog-review-skill --skill chinese-blog-review -g -y
```

## 使用

显式调用：

```text
$chinese-blog-review
请审一下这篇文章：...
```

也可以给出文件路径：

```text
使用 $chinese-blog-review 审稿 posts/my-draft.md
```

输出结构见下方"输出预览"。

## 审稿原则

按双层优先级。**作者核心关切**优先处理：

1. 标题与内容是否匹配
2. 是否偏题
3. 风格与流畅度（保留作者声音）
4. 专业准确性与事实风险

**其他编辑维度**按需启用：

5. 结构与论证链路
6. 证据与例子
7. 受众契合度
8. 原创性与读者价值
9. 边界与适用范围
10. 引用与风险
11. 可验证性（条件加载 `references/verifiability.md`）
12. 中文写作病灶——字词 / 句式 / 语气（`references/review.md` 内 Chinese Writing Pitfalls 段）

中文排版和中英文混排在内容审稿完成后处理。基础排版规则见 `references/rules.md`；复杂中英文混用标点按需加载 `references/mixed-punctuation.md`。它们的优先级低于以上任何一项。

核心边界：

- 只提出具体问题，不强行找问题。
- 不默认重写作者文章。
- 保留作者风格，除非风格影响理解。
- 涉及当前事实、API 行为、标准、法律、性能数据时，标记 `待核实-需查 X`，由作者完成核查。

## 输出预览

安装后审稿，输出大致是这种形状（节选自 `references/review.md` 内置的 Mini Template）：

```text
结论: 小修后发布。标题与内容匹配，存在一处事实表述需修正。

## 必须修改

### 严重: useEffect 执行时机表述错误

- 问题: 文章说 "useEffect 每次都会在渲染之前同步执行"。
- 证据: 原文第二段。
- 影响: 核心概念错误，会误导读者将同步布局逻辑写进 useEffect。
- 建议: 区分 useEffect 与 useLayoutEffect 的执行时机后修正。

## 事实核查

- 待核实-需查 React 官方文档 useEffect 章节: useEffect 是异步在 commit 之后执行。
```

完整规则、严重度定义、四态事实标注、AI 幻觉模式、中英文混用标点细则等均在 `references/` 下。

## 目录结构

```text
skills/chinese-blog-review/
  SKILL.md
  agents/
    openai.yaml            # OpenAI Codex 专属元数据（其他平台不需要）
  references/
    review.md              # 流程 + 维度 + 中文写作病灶 + Mini Template + 输出格式
    rules.md               # 中文排版规则
    mixed-punctuation.md   # 中英文混用时的标点规则（条件加载）
    verifiability.md       # 事实核查：来源映射、时效分级、AI 幻觉模式
```

## Attribution

`skills/chinese-blog-review/references/rules.md` 中的中文排版规则参考了 [sparanoid/chinese-copywriting-guidelines](https://github.com/sparanoid/chinese-copywriting-guidelines)。该项目使用 MIT License。

`skills/chinese-blog-review/references/mixed-punctuation.md` 中的中英文混用标点规则参考了 [中文技术文档写作风格指南](https://zh-style-guide.readthedocs.io/zh-cn/latest/) 和 `CY/T 154-2017 中文出版物夹用英文的编辑规范`，并针对个人技术博客审稿做了精简。

本仓库不是上游项目的镜像，只是为 Agent Skill 场景做的精简适配。

## License

MIT
