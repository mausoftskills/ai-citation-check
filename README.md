# AI Citation Check

A free agent skill (SKILL.md format) for a quick, hands-on SEO and AI SEO check: do ChatGPT and Perplexity cite your website when buyers ask the questions you'd want to show up for, and is anything on your site getting in the way of being found in search and AI answers?

There are no scripts and no API keys. Your agent helps you write a short set of real buyer questions, you ask them yourself in ChatGPT (with search on) and Perplexity a few times each and note who gets cited, and then the agent goes through an on-site checklist with you. It doesn't hand you a made-up score or promise traffic. It tells you what you saw and what to look at.

## Install
This repo is the skill folder (`SKILL.md` sits at the top), so clone or copy it into your agent's skills folder as `ai-citation-check`. The folder name has to match the `name` in SKILL.md.

- Claude Code: `~/.claude/skills/` (or `.claude/skills/` in one project)
- Cursor: `~/.cursor/skills/` (or `.cursor/skills/` in one project)
- Other agents that read SKILL.md: their own skills folder, often `.agents/skills/`

For example:
```bash
mkdir -p ~/.claude/skills
git clone https://github.com/mausoftskills/ai-citation-check ~/.claude/skills/ai-citation-check
```

Then ask your agent something like:
> Help me check whether ChatGPT and Perplexity cite example.com. Our competitors are rival.example and other.example.

## What it covers
1. Scope: your key pages, domains, brand and the short names people use for it, and a few competitors.
2. A question set of 10-20 buyer questions with a sensible mix (category, how-to, comparison, fact, a few brand questions counted separately), worded the way people really type.
3. Asking them by hand, three times per engine in fresh chats, and recording cited, named and who else got cited in a simple table.
4. Reading the results: citation counts, which pages get cited, named vs cited, and what the winning competitor pages have that yours don't.
5. An on-site checklist: robots.txt for search crawlers vs training crawlers (blocking training is your call, not a bug), CDN bot blocking, noindex, nosnippet and Bing's noarchive, text that only shows up after JavaScript, quotable answer-first passages, JSON-LD, and llms.txt as information only.
6. A short write-up with fixes in order and the caveats.

## What the paid version adds
This checklist is meant to be useful on its own. The paid pack, [AI SEO Citation Audit](https://www.agensi.io/skills/ai-seo-citation-audit) ($19), does the same job with tooling, so the checks are repeatable and the citation numbers stand up month to month:

- A site checker script that reads robots.txt with the RFC 9309 matching rules for Googlebot, Bingbot and the AI crawlers, path by path and across redirects, tests whether your firewall or CDN refuses AI crawler user agents while letting browsers in, and checks noindex, nosnippet, max-snippet and noarchive in both meta tags and headers, JavaScript-only text (with an optional headless browser render), JSON-LD and llms.txt, saving the evidence to a file.
- A passage checker that scores every paragraph on a page against six quotability checks and shows the weakest ones with the reason.
- Live citation tests through the OpenAI and Perplexity APIs with your own keys: 15-30 questions, several runs each, a dry run that shows the call count and worst-case cost before anything is spent, and every answer saved as evidence.
- Citation rates with confidence intervals, "read but not cited" detection, brand-name matching with aliases, and a monthly comparison that says up, down, likely, or no clear change.
- A crawler reference, a fixes guide for every finding, a question-set guide, and a report template.

## Limits
Doing this by hand gives you a rough picture, not a measurement. Answers change from one try to the next and from one day to the next, and a dozen questions asked three times is a small sample. Google AI Overviews and AI Mode can't be tested directly, so for Google you can only check that your pages are ready to be used. Nothing here guarantees citations.

OpenAI, ChatGPT, Perplexity, Google, Bing, Copilot and other product names are trademarks of their owners. This project is not affiliated with or endorsed by any of them.

## License
MIT. See [LICENSE](LICENSE).
