---
name: ai-citation-check
description: 'Use when a user wants a quick, manual SEO and AI SEO check of whether their website shows up and gets cited in AI answers and search, for example "does ChatGPT cite us", "why does Perplexity link our competitor", "are AI crawlers blocked on my site", or "how do I get found in AI search". No scripts and no API keys: the agent helps build a short set of real buyer questions, the user asks them by hand in ChatGPT (with search) and Perplexity a few times each and records who gets cited, then the agent walks through an on-site checklist: robots.txt for search vs training crawlers, CDN bot blocking, noindex, nosnippet and noarchive, text that only appears after JavaScript, JSON-LD, and answer-first passages. No invented scores or traffic promises.'
---

# AI citation check (manual)

A hands-on way to find out whether ChatGPT and Perplexity cite a website when buyers ask questions, and what on the site might be standing in the way. The user does the asking; the agent helps plan it, reads the results and goes through the site checklist. Not affiliated with or endorsed by OpenAI, Perplexity, Google or Microsoft.

## Rules (apply to every step)
1. **Evidence or nothing.** Every finding points to something the user can open: an answer they recorded, a page, a robots.txt line, a header. If you can't show where it came from, leave it out.
2. **No invented numbers.** No 0-100 "AI visibility score", no traffic projections, no "this will get you cited". Report what was seen ("cited in 4 of 18 answers") and checks passed ("7 of 10 pass").
3. **Facts vs judgment.** What the user recorded and what the pages show are facts. Advice on what to rewrite is a recommendation; label it that way.
4. **Answers are a sample.** The same question gets different answers from one try to the next. Always give counts with the number of tries, and never claim a change from a single try.
5. **Read-only.** Don't change anything on the user's site. Suggest; the user decides.

## 1. Scope
Ask, then confirm in one message:
- The site and **3-8 key pages**: home, the main product or service pages, and the 2-3 content pages they most want cited.
- Their domain(s), including subdomains like `blog.`, the brand name, and the **short names people actually use** for it. Answers often use the short form, and only the names on the list count as a mention.
- **2-5 competitors.**
- Who they sell to, and the questions those customers ask.

## 2. Build the question set
Aim for **10-20 questions** written the way people type them, not like the site's own headings. A rough mix:

| Type | Share | Example (fictional bike shop) |
|---|---|---|
| Category / "best" | ~30% | best commuter bike for hilly cities |
| Problem / how-to | ~30% | how often should I replace a bike chain |
| Comparison | ~15% | hydraulic vs mechanical disc brakes |
| Specific fact | ~15% | how much does an e-bike battery weigh |
| Brand | ~10% | is [brand] a good bike shop |

- Keep the brand name out of every question except the brand ones, and count brand questions separately. They measure reputation, not whether people find you.
- Give each key page at least two questions it should answer.
- Good sources for real wording: the user's sales and support questions, question-style queries in Google Search Console, and "People also ask" boxes and forum threads in their niche.
- If the business is local, put the place in some questions.
- Save the list and reuse it unchanged next time, or the two checks can't be compared.

## 3. Ask the questions by hand
The user does this in their own browser:
- [ ] Ask each question in **ChatGPT with search turned on** and in **Perplexity**. Start a new chat for every question so earlier answers don't steer the next one.
- [ ] Ask each one **3 times** per engine. Fewer than that and you can't tell a pattern from noise.
- [ ] For each answer, write down: was one of your pages **cited** (linked as a source), was your brand **named** in the text, and which other domains were cited.

A simple table works:

| Question | Engine | Try | Cited (Y/N, which page) | Named (Y/N) | Others cited |
|---|---|---|---|---|---|

Google AI Overviews and AI Mode can't be tested in a repeatable way. For Google, the useful check is whether the page is ready to be used at all (step 5). Say so plainly.

## 4. Read the results
- **Citation rate** per engine for the non-brand questions, as a count ("cited in 5 of 36 answers"), then brand questions on their own line, then per question.
- **Which of their pages** get cited, and which key pages never do.
- **Named vs cited.** Named without a link, or linked without the name: both are worth reporting.
- **Who gets cited instead.** For the 3-5 domains that win most often on the questions they lost, open one cited page each and note, as facts, what it has that the user's page lacks: a direct one-paragraph answer, a comparison table, specific numbers, a date, an FAQ, an author.

Treat any number from this as rough. A dozen questions asked three times is a small sample, and answers in the apps change often.

## 5. On-site checklist
Go through each key page with the user. Order the fixes: access problems first, then how quotable the pages are, then structured data, then everything else.

**Can the crawlers get in?**
- [ ] **robots.txt.** Check for rules that block the crawlers behind AI search: `OAI-SearchBot` (ChatGPT search), `PerplexityBot`, `Claude-SearchBot`, `Googlebot` (also covers AI Overviews and AI Mode), `Bingbot` (Copilot is built on Bing). If a search crawler is blocked, that engine can't cite the page from its index.
- [ ] Blocking **training** crawlers (`GPTBot`, `ClaudeBot`, `Google-Extended`, `CCBot` and similar) is a business choice, not a visibility bug. Lay out the trade-off and let the user decide; never tell them to unblock one to "rank in AI".
- [ ] **How robots.txt itself answers.** If it returns a server error or times out, crawlers treat the whole site as off limits. A 404 means no rules, so everything is allowed.
- [ ] **CDN or firewall bot blocking.** A "block AI bots" setting at the CDN overrides an open robots.txt. The user checks their CDN's bot settings and logs. Real crawlers are identified by IP, so a quick test with a fake user agent is only a hint.
- [ ] **Google and Bing's own view.** URL Inspection in Google Search Console and Bing Webmaster Tools shows what the real crawler gets.

**Can the page be used?**
- [ ] No `noindex`, `nosnippet` or a tiny `max-snippet` (under 50 characters) on pages they want quoted, in the HTML or the `X-Robots-Tag` header. Use `data-nosnippet` on the bits that really must stay out.
- [ ] For Bing, `noarchive` keeps a page out of Copilot answers (normal Bing results aren't affected). If the user wants Copilot to show only the URL, title and snippet, `nocache` is the alternative.
- [ ] The main text is in the HTML the server sends, not only added by JavaScript. Many AI crawlers don't run JavaScript. A quick test: view the page source (not the inspector) and look for the key paragraphs.

**Is it easy to quote?**
- [ ] For the questions the user lost, does the page answer them near the top, in a paragraph that makes sense on its own? Good quotable passages name the subject instead of opening with "This" or "It", include specifics (numbers, names, steps), put the answer first, run roughly 40-300 words, and sit under a heading that matches the question.
- [ ] Pages that compete for comparison questions benefit from a real comparison table; fact questions from a plain stated fact with a date.

**Structured data**
- [ ] JSON-LD that fits the page: `Organization` on the home page, `Product` or `SoftwareApplication` on product pages, `Article` on content pages, `BreadcrumbList`, `LocalBusiness` for local businesses, and `FAQPage` only where there's a real FAQ. Validate it in Google's Rich Results Test. No engine promises citations because of structured data.

**Information only**
- [ ] `llms.txt`: note whether it exists. It's a proposal, and no major AI search engine has confirmed using it. A missing one isn't a problem.

## 6. Write it up
A short report: the question set, the counts per engine (with number of tries), which pages get cited and which don't, who wins instead and what their pages have, then the fixes in order, each tied to its evidence, who does it and how to check it worked. End with the caveats: the sample is small, app answers vary, Google AI Overviews couldn't be tested directly. Suggest repeating the same questions in a month, after fixes have had time to be crawled.
