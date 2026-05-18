# Chinese Copywriting Rules

Source: https://github.com/sparanoid/chinese-copywriting-guidelines/blob/master/README.zh-Hans.md

For detailed punctuation rules when Chinese prose embeds English sentences, quotations, titles, UI labels, or book / journal names, load `mixed-punctuation.md`.

Use these rules for Simplified Chinese and mixed Chinese-English copy. Keep semantics intact.

## Spacing

- Add one halfwidth space between Chinese characters and English words, acronyms, product names, variables, or inline code.
- Add one halfwidth space between Chinese characters and Arabic numerals.
- Add one halfwidth space between numerals and units such as `MB`, `GB`, `ms`, `kg`, `px`, `TB`, and `GHz`.
- Do not add a space between a numeral and `%` or `°`.
- Do not add spaces around fullwidth Chinese punctuation such as `，`、`。`、`！`、`？`、`：`、`；`、`（`、`）`.
- Do not insert spaces inside official product names if the official spelling omits them.

Examples:

- `用 React 写 3 个组件。`
- `响应时间是 120 ms，成功率是 99%。`
- `支持豆瓣FM 的旧账号格式。`

## Punctuation

- Use fullwidth Chinese punctuation in Chinese sentences: `，`、`。`、`！`、`？`、`：`、`；`、`（`、`）`.
- Do not use repeated punctuation for emphasis. Prefer one punctuation mark, or the compact `？！` pattern when both question and surprise are needed.
- Use halfwidth punctuation inside complete English sentences, English titles, code-like names, and special terms.
- Do not add spaces between fullwidth punctuation and adjacent text.
- Use context-appropriate book title or emphasis formatting. For English publications in Markdown, italic text may be more suitable than Chinese book title marks when following the upstream guideline strictly.

Examples:

- `这个 API 返回了什么？`
- `他说：“Stay hungry, stay foolish.”`
- `推荐阅读 *Designing Data-Intensive Applications*。`

## Fullwidth and Halfwidth

- Use halfwidth Arabic numerals: `123`, not `１２３`.
- Use halfwidth English letters, acronyms, and symbols inside English terms.
- Use fullwidth punctuation for Chinese clauses and sentences.
- Use halfwidth punctuation for URLs, file paths, commands, package names, code identifiers, and English-only fragments.
- In design mockups or posters, fullwidth numerals can be acceptable for visual alignment if the user explicitly wants that style.

## Proper Nouns and Abbreviations

- Preserve official capitalization for brands, products, organizations, languages, and frameworks.
- Do not normalize brand spelling to all lowercase, all uppercase, or decorative variants unless the official spelling requires it.
- Avoid nonstandard abbreviations in formal copy. Prefer `TypeScript`, `HTML5`, `React`, `Next.js` over unclear shorthand such as `Ts`, `h5`, or ad hoc framework abbreviations.
- Do not change established technical terms inside code spans or identifiers.

## Links and Markdown

- Preserve Markdown links, images, headings, tables, frontmatter, MDX components, and code fences.
- Adjust spaces around inline Markdown links only when it improves readability and does not break syntax.
- Do not edit URL text, anchors, query strings, or paths.
- Keep punctuation outside links when the punctuation belongs to the surrounding Chinese sentence.

## Special Characters

- Use the fullwidth ellipsis `……` (two `…` characters, six dots total), not `...`, `…`, or `。。。`, inside Chinese sentences.
- Use the Chinese em dash `——` (two `—` characters back to back), not `--`, `—` alone, or `~`, when interrupting or appending a clause in Chinese.
- For numeric ranges in Chinese prose prefer the en dash `–` or tilde `~` consistently within one document; do not mix. The ASCII hyphen `-` is acceptable in code-like spans (`HTTP/1.1`, `UTF-8`).
- Quote marks inside Chinese sentences default to `“ ”` and `‘ ’`. Use straight quotes `" "` only inside code spans, English fragments, or shell commands.

## Brackets

- Use fullwidth Chinese parentheses `（）` for Chinese prose annotations, including English translations or explanatory English phrases.
- Use halfwidth parentheses `()` for code-like content, URLs, file paths, command syntax, version strings, RFC identifiers, function calls, and complete English fragments.
- When using halfwidth `()` inside Chinese text, keep one halfwidth space outside the brackets on both sides and no extra space inside the pair.
- For nuanced Chinese-English punctuation cases, load `mixed-punctuation.md`.

Examples:

- `这个函数返回一个布尔值（true 或 false）。` — content is Chinese, use fullwidth.
- `DIY（Do It Yourself）教育有助于孩子独立人格的形成。` — prose annotation, use fullwidth.
- `请阅读 RFC 7231 (HTTP/1.1 Semantics)。` — code-like standard title, use halfwidth with spaces.

## Punctuation Repetition and List Numbering

- **No mixed terminal punctuation**: Do not write `！。`, `？。`, `?！`, `。！`. Pick one terminator. The compact `？！` (question + surprise) is acceptable when both meanings are needed simultaneously.
- **No accidental double commas**: Watch for `，，` and `, ，` (halfwidth + fullwidth comma adjacent), which happen during Chinese-English copy edits.
- **No repeated emphasis punctuation**: `！！！`, `？？？`, `。。。` are not valid emphasis in formal writing. Use one mark or rephrase for emphasis.
- **List numbering must be consistent within one article**: Do not mix `1.` / `1、` / `1）` / `（1）` / `①` / `一、` styles. Pick one and stay with it. Markdown lists default to `1.`; switch only when there is a typographic reason.
- **Nested list style should differ from parent**: When nesting an ordered list inside another ordered list, use a different marker style at each level (e.g., `1.` outside, `a.` or `1)` inside) so structure is visible at a glance.

## Code Blocks and Inline Code

- Always declare a language tag on fenced code blocks: `​```ts`, `​```bash`, `​```sql`, not bare `​````.
- Use canonical language tags consistently in one document: prefer `ts` or `typescript` everywhere, not both; same for `js` vs `javascript`, `sh` vs `bash`, `yml` vs `yaml`.
- Inline code uses backticks: `​useEffect`, `​npm install`. Do not wrap code in Chinese quotes `“useEffect”` or fullwidth brackets.
- Inside code spans and code blocks, do not apply Chinese spacing or punctuation rules.

## Optional or Controversial Rules

- Spaces around inline links are stylistic. Apply them only when the surrounding style uses them or the user asks for strict upstream style.
- Corner quotes `「」` and `『』` in Simplified Chinese are stylistic. Do not force-convert quote style unless requested.
- If the document is Traditional Chinese, do not convert scripts unless the user explicitly asks.

## Review Checklist

1. Chinese-English spacing.
2. Chinese-number spacing.
3. Number-unit spacing and `%` / `°` exceptions.
4. Fullwidth Chinese punctuation in Chinese sentences.
5. No extra spaces around fullwidth punctuation.
6. Halfwidth numerals and English terms.
7. Official proper noun capitalization.
8. Markdown, code, URLs, and identifiers preserved.
9. Ellipsis `……` (not `...`), em dash `——` (not `--`), consistent numeric range separator.
10. Fullwidth `（）` for prose annotations, halfwidth `()` for code-like English / URLs / versions, with spacing.
11. Fenced code blocks have language tags; tag style is consistent across the document.
12. No mixed or repeated terminal punctuation (`！。`, `？？？`, `。。。`).
13. List numbering style is consistent within the article; nested lists use a different marker level.
