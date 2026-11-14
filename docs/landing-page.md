# Presenting a library landing page

What we learned, from a survey and from practice, about the landing page of
an open source library, and above all what to put in the hero (the first
screen). As of 2026-11.

The case study at the end records how the landing page of
[gawa](https://github.com/kt3k/gawa) was rebuilt. gawa is a typed bridge
between a page inside a WebView and the native app that hosts it.

## Conclusions

1. **Put code in a library's hero.** Show how it reads in use, not an
   abstract diagram or a large logo.
2. **Make the headline say what the tool does, not its name.** A small
   wordmark is enough for the name and the logo.
3. **Fit the code in the first screen.** On a common laptop screen (about
   1280×800), the whole snippet should be visible without scrolling.
4. **Show both ends of a tool that connects two sides.** Put the caller and
   the handler side by side so the matching names read at a glance.

## The hero by kind of tool

| Kind | What the hero shows | Examples |
|---|---|---|
| Library or SDK | Code that uses it | tRPC, Hono, Tailwind |
| Runtime or CLI | Install command, benchmarks | Vite, Bun, Biome, Effect |
| Large framework or product | Logo, animation, product UI | Tauri, Electron, Astro |

- No surveyed page puts an abstract layer diagram in the hero (a stack such
  as "Page / library / WebView").
- The pages that show a large logo are large frameworks, or pages with
  almost nothing in the hero (htmx, Zod). A small library has little reason
  to copy them.
- Tailwind and Biome put input next to output. The same idea shows "call,
  then get a result".

## Tools that connect two sides

Examples of tools with two ends: client and server, page and native app,
main thread and worker.

- **tRPC**: the hero shows only the calling side, with one line saying the
  types come from the server. The "How it works" section right after puts
  both sides next to each other.
- **Comlink**: pairs the main-thread code with the worker code.
- **Capacitor**: puts the web TypeScript and the native Swift in the same
  set of tabs.

The recommended shape:

- The caller on the left, the handler on the right. When the handler side
  has several languages (Swift and Kotlin, for example), switch them with
  tabs.
- Arrows between the two show which side calls and which side answers (for
  example `call →` and `← emit`).
- Use the same method name on both ends so the eye can follow the match.
- On a narrow screen, stack the two and turn the arrows vertical. Or, like
  tRPC, show only the caller and link to the handler.

## After the hero

Right after the hero, the usual order is customer logos or feature cards,
then a three-step "How it works", then features, social proof, and a final
call to action.

If the feature cards already do the job of the three steps, do not add a
"How it works" section on top of them.

## Evidence

- **[Evil Martians: We studied 100 dev tool landing pages](https://evilmartians.com/chronicles/we-studied-100-devtool-landing-pages-here-is-what-actually-works-in-2025)**:
  centered heroes are the norm, with one visual under a large headline.
  Libraries and SDKs with little UI usually show a code snippet. Working
  code beats claims, concrete numbers beat adjectives, and plain beats
  flashy.
- **[DEV: Landing pages that convert for developer tools](https://dev.to/whoffagents/landing-pages-that-convert-for-developer-tools-patterns-that-actually-work-3c8k)**:
  code or a demo in the first screen says more, faster, than long copy.
- **Where attention goes**: a Nielsen Norman Group finding that 57% of
  viewing time is spent on the first screen is widely quoted
  ([secondary source](https://mixpanel.com/blog/optimizing-above-the-fold);
  the original was not checked).
- **Why the headline matters**: many visitors are said to decide whether to
  read on from the headline and the start of the subheadline alone
  ([reference](https://www.flint.com/blog/landing-page-headline-testing-statistics);
  a vendor blog, so discount its numbers).

No study that compares logo sizes directly was found. The conclusions above
are a judgment from agency and vendor articles and from real pages.

### Pages surveyed

Checked against each site's source on GitHub: tRPC, Hono, Zod, Valibot,
Vite, Tauri, Capacitor, htmx, Astro, Tailwind, Biome, Effect, Electron,
Comlink.

Bun and Hotwire are from memory and unverified. Deno, Expo, and Alpine could
not be fetched. The live sites were not reachable from the survey's network,
so the deployed pages may differ.

## Case study: the gawa landing page

1. **Starting point**: the right side of the hero held a three-row layer
   list: "Page: `call` / `on`", "gawa: typed RPC and events", "WebView". The
   row name and the API names sat on one line and read as "page call on",
   and the native side that `call` reaches was missing from the picture.
2. **First pass**: the layer list was replaced by the page's
   `bridge.call("kv.get", …)` and `bridge.on("back", …)` next to the app's
   `router.register("kv.get")` and `emit("back")` (Swift and Kotlin tabs),
   with `call →` and `← emit` arrows between them.
3. **Second pass**: a large kanji 側 at the top used about 170px of the first
   screen, so even at 1280×900 only the first lines of the code were
   visible. 側 became a small seal next to the wordmark, and the h1 changed
   from the name "gawa" to "A thin, typed bridge between a web page and the
   app that hosts it." At 1280×800 the whole code pair is now visible.

Lessons:

- Keep brand elements (a kanji name, for example), but do not let them take
  the space of the first screen.
- Check the result with screenshots at desktop size (1280×800), phone width
  (390px), and in dark mode, and measure where the bottom of the code pair
  lands.
