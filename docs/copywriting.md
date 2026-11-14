# Copywriting for a library landing page

What we learned about the words on an open source library's landing page:
the tagline, the headline, the feature text, and the notes around the code.
As of 2026-11.

The case study at the end records how the copy on the
[gawa](https://github.com/kt3k/gawa) landing page was reviewed. For what to
put in the hero and how to lay it out, see
[landing-page.md](landing-page.md).

## Conclusions

1. **Clear beats clever.** Visitors decide from the headline whether to
   stay. A line that needs interpretation loses them, however neat it is.
2. **Concrete beats abstract.** Developers are skeptical and value accurate
   information over hype. Name the thing, the platform, the version, the
   number. "Fast" says less than "150ms"; "works with all databases" says
   less than the list of databases.
3. **Say what the reader gets, not only how it works.** A mechanism ("serves
   files from a real origin") needs its consequence ("so the page gets the
   same-origin rules it has on the web"). Do not stretch the benefit until
   it is vague ("ship more code").
4. **Say each thing once.** On a short page, a phrase repeated in the hero
   and in a feature card reads as padding. Give each block its own job.
5. **Keep the brand in the name, not in the explanation.** A playful
   tagline is fine next to the wordmark, as long as it is still concrete and
   the headline does the explaining.

## Checks for each line

Read each line on the page and ask:

- **Could a reader who has never heard of the project say what it does
  after this line?** Applies to the headline above all.
- **Is there a word that refers to nothing?** "something", "seamless",
  "powerful", "next-generation", "streamline". Replace it with what it
  stands for.
- **Is there a number, a name, or a version that would make it concrete?**
  Platforms and minimum versions, what a call returns, what an error
  carries.
- **Does it say why the reader should care?** If a line states only a
  mechanism, add the consequence.
- **Does another block already say this?** If so, cut one of them or give
  it a different job.
- **Is the same text written the same way everywhere?** The page title, the
  social card text, the README, and the hero tagline should agree.

What is fine to keep:

- **Lists of what the tool does not do** ("no runtime, no plugin system, no
  CLI"). They are concrete, and for a small library they are a real
  differentiator.
- **Words that carry a comparison** ("thin" next to frameworks that do
  much more), as long as the comparison is real.
- **A call to action that names an action** ("Add a WebView anywhere and
  attach it").

## Evidence

- **[Lean Labs: Why clarity matters more than cleverness](https://www.leanlabs.com/faq/b2b-websites/why-clarity-matters-more-than-cleverness-in-website-copy)**
  and
  **[MarketSmiths: Clear or clever copy?](https://www.marketsmiths.com/2018/what-makes-for-better-branding-clear-or-clever-copy/)**:
  visitors decide from the headline and leave if the message needs
  interpretation. Wit is fine only when it does not cost clarity.
- **[Shorenstein Center: reading dies in complexity](https://shorensteincenter.org/reading-dies-complexity-online-news-consumers-prefer-simple-writing/)**:
  an analysis of more than 30,000 news headline experiments found that
  plain headlines got more clicks than complex ones. The strongest evidence
  here, though it is about news, not product pages.
- **[daily.dev: How to write developer-focused ad copy](https://business.daily.dev/blog/how-to-write-developer-focused-ad-copy)**:
  developers are logical and skeptical. Replace vague claims with
  measurable ones.
- **[Evil Martians: Don't copy these copywriting clichés](https://evilmartians.com/chronicles/hey-developer-tool-teams-dont-copy-these-copywriting-cliches)**:
  developer tool copy fails when it is too market-y, vague, or poorly
  written.
- **[dx.tips: Benefit layers](https://dx.tips/benefit-layers)**: lead with
  what the reader gets, but a chain of indirect benefits ends in something
  vague.

Widely quoted numbers were not used: "clear subject lines get 541% more
responses" (attributed to AWeber's tests) and "a clear page converted 330%
better" (attributed to MarketingSherpa) were found only in secondary
sources.

## Case study: the gawa landing page

| Where | Before | Problem | After |
|---|---|---|---|
| Tagline next to the wordmark | "the shell around something." | "something" refers to nothing. The page title and the social card already said "the shell around a WebView", so the text also disagreed with itself. | "the shell around a WebView." The README now says the same, with the meaning of 側 ("side"). |
| Note under the code pair | "The same method name on both ends, typed on both ends. Only your bundled page can call it. …" | "on both ends" twice. The origin sentence repeated feature card 03. | "One method name, typed on both ends. It attaches to the WKWebView or WebView already in your app." |
| Feature 01, real-origin serving | "Serve bundled files from a real origin instead of `file://`." | A mechanism with no consequence. | "… instead of `file://`, so the page gets the same-origin rules it has on the web." |
| Feature 02, typed RPC | "Request / reply RPC and events, typed on both ends." | Repeated the hero. | "A call returns a Promise with a typed result or a `GawaError`. The app can also push events to the page." |

Kept as they were:

- The headline "A thin, typed bridge between a web page and the app that
  hosts it." It says what the tool is, and "thin" carries the comparison
  with frameworks.
- "Nothing more: no runtime, no plugin system, no CLI, no opinion about your
  screens." A concrete list of what is left out.
- The closing call to action "Add a WKWebView or WebView anywhere and attach
  gawa to it." It names an action.

## How these conclusions were reached

This section records the questions asked, what was compared, and where the
evidence is weak, so the next review can repeat the work or challenge it.

### The question

After the hero layout was rebuilt ([landing-page.md](landing-page.md)), the
question was whether the words on the page were right, starting with the
tagline "the shell around something". It came from the page, not from a
checklist: the tagline was a translation of the project's name, and it was
not clear whether it helped or hurt.

### What was searched for

Three searches, each aimed at one claim:

1. **General principles**: is "clear beats clever" a real principle, and
   what does it mean in practice?
2. **Writing for developers**: what changes when the reader is a developer?
   Which words and patterns do they distrust?
3. **Evidence behind the principle**: is there research, not only blog
   advice, that clear headlines work better?

### How the evidence was weighed

From strongest to weakest:

1. **Controlled studies of headlines** (the news headline experiments). Many
   tests, but on news, not on product pages.
2. **Practitioner guides on developer marketing** (daily.dev, Evil
   Martians, dx.tips). Consistent with each other, but opinion, and
   sometimes from companies that sell advertising to developers.
3. **General marketing blogs**. Used only where they agreed with the
   above.
4. **Striking numbers** (541%, 330%, and the like). Not used, because no
   primary source was found.

The principles were accepted because sources of different kinds agreed on
the direction. None of them measured a library landing page.

### How the page was reviewed

1. Every visible line of the landing page was extracted from the page
   source, together with the page title, the social card text, and the
   README tagline.
2. Each line was put through the checks in "Checks for each line" above.
3. A line was changed only when a check failed and the fix was concrete.
   Lines that passed were kept on purpose and recorded as kept, so the
   next review knows they were looked at.
4. Where a test in the repository asserted the old text (the site check
   looked for "the shell around something"), the test was updated with the
   copy.

### Limits of this round

- No reader was asked. The review is one reviewer applying general advice.
- Nothing was measured: no analytics, no A/B test.
- The evidence for "clear beats clever" is strongest for news headlines and
  email subject lines, not for developer tool pages.
- Only the landing page was reviewed. The docs pages and their
  descriptions were not.

### Next time

- Run the same checks on every line again, including the lines kept this
  time. The page will have changed around them.
- Review the docs pages and the meta descriptions with the same checks.
- Show the headline alone to a few developers who do not know the project
  and ask what it does. That is the cheapest real test of the first check.
- If the project has traffic, compare clicks on the primary call to action
  before and after a copy change.
