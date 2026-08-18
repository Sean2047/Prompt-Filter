# Prompt Filter

A tiny, single-file web tool: type a question, pick a filter, get back a sharper prompt to paste into whatever AI you're using.

**[Try it](./index.html)** — no install, no account, nothing sent anywhere.

## What it does

You give it a plain question. It wraps that question in a chosen "filter" — a way of thinking about the question, or a way of talking about the answer — and hands you back a ready-to-paste prompt. The filter doesn't answer anything itself; it just reshapes the ask before you hand it to your AI of choice.

- **Runs entirely client-side.** Fixed templates, no model calls, nothing leaves the browser.
- **No backend, no account, no cost.** It's one HTML file — open it locally or host it anywhere static.

## Filters

**Focused** — different ways of reasoning through a question:

| Filter | What it does |
|---|---|
| Minimalist | Conclusion first, no padding, 3–5 bullets max |
| Socratic | Surfaces assumptions and asks probing questions before offering a tentative starting stance |
| Scientist | Scientific reasoning: hypotheses, evidence strength, confounders, stated limitations |
| Multiple Perspectives | Lays out genuinely competing positions without forcing false balance |
| Feynman | Plain-language, analogy-first explanation for a total beginner |
| Consultant | Structured, actionable: situation → options → recommendation → risks → next steps |

**Playful** — different voices, with more creative license:

| Filter | What it does |
|---|---|
| Devil's Advocate | Actively challenges the framing — real objections, sorted by how decisive they are |
| Poet | Vivid, image-driven language without sacrificing accuracy |
| Late-Night DJ | Warm, casual, talking-to-a-friend energy |
| Movie Trailer Voice | Big, dramatic, "in a world..." narration |
| Roast Comedian | Sharp, funny, roasts the topic (not you) |
| Rap Battle | Rhyming freestyle verse |

## How a prompt is built

Every generated prompt follows the same shape:

```
Question: {your question}

- [accuracy rule — see below]
- Apply the approach only where it genuinely helps
- [optional: open/close bookend — see below]
- Respond in the same language as the question above

Approach:
{the filter's specific instructions}
```

A few rules apply underneath the hood, regardless of which filter is picked:

- **Accuracy baseline.** Every filter is told the goal is a genuinely useful answer — the filter shapes *delivery*, not substance. Filters marked with creative license (the four wilder Playful ones) are explicitly allowed obvious hyperbole and absurd framing, but not fabricated facts that could pass as real.
- **No false certainty.** If a question has no single settled answer — it's unsettled, contested, or depends on circumstances only you know — the prompt asks the AI to say so plainly instead of inventing a confident answer.
- **Summary bookend (optional toggle).** When on, the AI opens with a one-line plain take and closes by restating it, so the styled middle can go all-in without drifting from the facts. Socratic gets its own version of this — its bookend is a *tentative* starting stance, not a final answer, matching what the filter is actually for.

## Using it

1. Open `prompt-filter.html` in any browser (double-click it, or host it — see below).
2. Type your question.
3. Pick a filter.
4. Copy the generated prompt and paste it into your AI of choice.

You can edit the generated text before copying — it won't be touched unless you change the question, filter, or toggle.

## Hosting it

It's a static file, so any of these work and are free:

- **GitHub Pages** — push it to a repo, rename to `index.html`, enable Pages.
- **Netlify Drop / Vercel / Cloudflare Pages** — drag the file into the browser, get a URL.

No backend, no environment variables, no build step.

## License

Licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/) — free to use, share, and adapt for personal or non-commercial purposes, with attribution. Commercial use requires permission (see the header comment in `prompt-filter.html` for contact info).

This is general information, not legal advice.
