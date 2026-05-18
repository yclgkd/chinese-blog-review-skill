---
name: chinese-blog-review
description: Use when reviewing or proofreading Chinese blog posts, Markdown drafts, technical notes, or long-form articles. Reports findings on title fit, topic focus, structure, technical accuracy, evidence, and Chinese copy formatting. NOT for English-only content, academic papers, marketing or brand copy, or auto-rewriting an article.
---

# Chinese Blog Review

## Overview

Use this skill as a Chinese blog editorial review guide. Treat article review like code review: report concrete issues with evidence and impact, preserve author voice, and only edit text when the user explicitly asks for changes.

## Workflow

1. Identify the article type: blog post, Markdown draft, technical note, essay, tutorial, or long-form documentation.
2. Read `references/review.md` and give editorial feedback first.
3. If the draft makes technical, factual, version-sensitive, or empirical claims (API behavior, protocol or standard, performance numbers, version availability, legal or compliance, pricing, second-hand `据说 / 听说` content), also load `references/verifiability.md` and apply its primary-source mapping, time-sensitivity tiers, four-state annotation, and AI-hallucination checklist.
4. Read `references/rules.md` only for copy formatting and Chinese mixed-script typography.
5. If the draft has English sentences, quotations, titles, labels, book / journal names, or punctuation-heavy Chinese-English mixing, also load `references/mixed-punctuation.md`.
6. Preserve Markdown structure, inline code, code blocks, URLs, frontmatter keys, package names, file paths, identifiers, command flags, and official brand spelling.
7. Treat formatting-only issues as lower priority than content correctness, topic fit, structure, and factual accuracy.
8. When fact-checking is needed, fetch primary sources and distinguish verified facts, inferences, and items still pending verification using the four-state annotation in `verifiability.md`.
9. If a project-specific style guide conflicts with this skill, follow the project-specific rule.

## Output

Follow the structure and finding format defined in `references/review.md` (Output Format section). The rules below cover policy only, not formatting:

- For review requests, return findings first. Do not rewrite the article unless asked.
- For polishing requests, return the corrected text first and keep changes scoped.
- For file edits, modify only the relevant text and avoid unrelated formatting churn.
- For exact upstream wording or version-sensitive questions, fetch the current upstream README before answering.
- Calibrate review length to article length: short articles (under ~1000 Chinese characters) get at most 5 findings; long articles get at most 12. When over budget, drop low-severity findings first.

## Source

Copy-formatting guidance is a compact local adaptation of `sparanoid/chinese-copywriting-guidelines`, `CY/T 154-2017 中文出版物夹用英文的编辑规范`, and the Chinese technical writing guide referenced in `references/mixed-punctuation.md`. It is not a verbatim mirror.
