# AI Daily

The day's AI news in five minutes, by StateLess Squad: https://statelesssquad.github.io/statelesssquad-public-ai-news-blog/

No build step. `index.html` is one static page that reads the YAML in `news/` when it loads, so a new day goes
live as soon as its file is on `main` (GitHub Pages serves the branch root).

## How a day gets here

Every morning a scheduled agent gathers the past 24 hours of AI news and answers in the format below. A small
publisher script checks the answer (dates, https links, lengths, allowed kinds), writes `news/YYYY-MM-DD.yaml`,
adds the day to `news/index.yaml` and commits both to `main`.

## Format

`news/YYYY-MM-DD.yaml`, one per day:

```yaml
date: 2026-10-25
headline: "The day in one line"
summary: "Two or three sentences on the day."
items:
  - title: "Story title"
    summary: "One or two sentences."
    source: example.com
    url: https://example.com/story
    kind: model   # model | research | product | industry | safety | policy
```

`news/index.yaml`, newest first:

```yaml
issues:
  - { date: 2026-10-25, count: 7 }
```

## Files

- `index.html`: the page (vanilla JS; fonts from Google Fonts)
- `vendor/js-yaml.min.js`: [js-yaml](https://github.com/nodeca/js-yaml) 4.1.0, MIT licence
- `news/`: the issues

Links in the stories go to their original publishers; summaries are short and written fresh. Informational only.
