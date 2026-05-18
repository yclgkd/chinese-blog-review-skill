# Mixed Chinese-English Punctuation

Use this reference when a Chinese article contains English words, phrases, complete English sentences, quotations, titles, labels, or book / journal names and the punctuation around them needs review.

Sources: `CY/T 154-2017 中文出版物夹用英文的编辑规范` and https://zh-style-guide.readthedocs.io/zh-cn/latest/标点符号/中英文混用时标点符号用法.html

This is a compact rule set, not a full style guide. It follows the practical direction of those sources: Chinese text is the container, English punctuation is preserved inside English content.

## Decision Rule

1. Decide whether the surrounding sentence is Chinese or English.
2. Decide what the embedded English is: word / phrase, complete sentence, title, quotation, UI label, code-like token, or source title.
3. Use Chinese punctuation for the surrounding Chinese sentence boundary.
4. Preserve English punctuation inside complete English sentences, English titles, and English quotations.
5. Preserve code, URLs, command flags, file paths, package names, identifiers, and Markdown syntax exactly unless the user asks for copy editing.

## English Words and Phrases

- Do not wrap ordinary English words or phrases in Chinese quotes by default.
- If the Chinese sentence ends after the English word or phrase, use Chinese terminal punctuation.
- Use Chinese punctuation outside the English phrase.

Examples:

- `change 和 transform 意义不同。`
- `distributed SQL 在这里是什么意思？`
- `如果想表达更礼貌的语气，用 might；反之，用 may。`
- `官网按钮写着：Try it now。`

## Complete English Sentences

- When a Chinese sentence embeds a complete English sentence as quoted text or an example, use Chinese quotes around the English sentence.
- Preserve the English sentence's internal punctuation.
- The surrounding Chinese sentence still takes Chinese punctuation according to its own mood.
- If this creates visually heavy endings such as `.”。` or `?”？`, do not mark it wrong by itself. Suggest rephrasing only when readability suffers or the project style forbids it.

Examples:

- `信里那句“It depends.”显得模棱两可。`
- `英文演讲的主旨是“Love is beautiful.”。`
- `她当时的原话是“Are you serious?”。`
- `作者为什么突然问“Does money really talk?”？`

## Commas, Semicolons, and Colons

- English commas, semicolons, and colons stay inside English sentences, English titles, and English names.
- Chinese commas, semicolons, and colons are used for the surrounding Chinese sentence.
- If an English phrase is an example or explanation of the preceding Chinese text, use a Chinese colon before it.
- Do not convert punctuation that is part of an official English title or product name.

Examples:

- `协议中的“The debt, if any, is to be written off.”暗藏玄机。`
- `天气炎热，她嚷着要 ice cream；天冷了，她要的还是 ice cream。`
- `我们寻找的问讯处就在身后，绿底白字写着：Information。`
- `TiDB: The Future of Databases 是一篇主题分享。`

## Question Marks and Exclamation Marks

- If the surrounding Chinese sentence is a question, end it with a Chinese question mark.
- If the embedded English sentence is a question, preserve its English question mark.
- If the embedded English title or quotation ends with `?` or `!`, preserve it.
- When the outer Chinese sentence and inner English sentence both carry question or exclamation force, doubled marks can be standard but visually noisy; prefer a rewrite when the text is for a blog rather than a formal publication.

Examples:

- `due to 和 because 意思一样吗？`
- `“Why shall I follow you?”是他提出的第一个问题。`
- `今天晚报的头条是不是“Pension Stops Growing?”？`
- `谈判时最好别说“No way!”！`

## Lists of English Items

- For parallel English letters, words, or phrases inside a Chinese sentence, use Chinese enumeration punctuation.
- Use `、` between listed English items; use `和` before the last item when it reads naturally.
- If each listed item is a full quoted English sentence, the quote boundaries may make `、` unnecessary.

Examples:

- `指示牌上 e、i 和 u 这三个字母印得模糊不清。`
- `may、might、can 和 could 都可以表达可能性。`
- `turn in、turn out、turn down、turn up 是否已经构成固定词组？`
- `老师把“He went to bed.”“He turned in early.”“He fell asleep.”写在黑板上。`

## Quotes

- Chinese quotes wrap complete English sentences embedded in Chinese prose.
- English words or phrases do not need quotes unless they are terms under discussion, UI strings, labels, or deliberately quoted wording.
- If an English sentence inside Chinese quotes needs its own quote marks, use English single quotes inside the English sentence.
- Do not use Chinese quotes for inline code, APIs, commands, package names, or identifiers; use code spans instead.

Examples:

- `bus 和 coach 有没有区别？`
- `见面就问“How old are you?”是不恰当的。`
- `报道中是否删去了“The witness said, ‘Nobody came to help.’”？`
- `“used to + 动词原形”一般表示过去常做的事。`

## Parentheses

- In running Chinese prose, use fullwidth Chinese parentheses for explanatory English translations or notes.
- Use halfwidth parentheses for code-like content, URLs, file paths, command syntax, version strings, RFC identifiers, function calls, and complete English fragments.
- When halfwidth parentheses appear inside Chinese prose, keep one halfwidth space outside the pair and no extra space inside the pair.
- If the project already has a consistent bracket style, follow the project style unless it harms readability.

Examples:

- `DIY（Do It Yourself）教育有助于孩子独立人格的形成。`
- `这次会议被定性为“高峰论坛”（summit forum）。`
- `请阅读 RFC 7231 (HTTP/1.1 Semantics)。`
- `调用 fetch(url, options) 时要处理超时。`

## English Book, Journal, and Article Titles

- English book and journal names inside Chinese prose should not use Chinese book title marks.
- In Markdown, prefer italics for English books and journals when that matches the surrounding style.
- English article titles use Chinese quotes.
- Preserve punctuation that belongs to the English title, including subtitles, question marks, and exclamation marks.

Examples:

- `推荐阅读 *Designing Data-Intensive Applications*。`
- `她在 *Learned Publishing* 发表过文章。`
- `World of Tomorrow 中的“Will Human Be Joyfully Enslaved by Cellphone?”很有争议。`
- `Self Regained: A Journey to Shangri-La 是原版书名。`

## Review Output Guidance

- Treat these as formatting or readability findings unless punctuation changes the meaning.
- When outputting a finding, cite this reference section by name, for example `Mixed Chinese-English Punctuation > Complete English Sentences`.
- Prefer a concrete local fix over restating the whole rule.
- Do not force strict publication style when the article is a casual personal blog and the current project style is consistent.
