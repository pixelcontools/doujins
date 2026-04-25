# doujins

Multi-group nhentai cover gallery for community reading polls. Single static HTML page with localStorage-backed state.

Live at: https://pixelcontools.github.io/doujins/

## Features

- **Rounds**: Top-level collapsible groupings with editable names (seed: "Week 2 Round 1")
- **Groups**: Within each round, paste nhentai URLs or IDs (newline / comma / space separated)
- **Cover gallery**: Fetches metadata via the [nhentai v2 API](https://nhentai.net/api/v2/docs) through a CORS proxy, displays 7:10 cover cards with title and page count
- **Voting**: One vote per group via the round dot in the top-left of each card; click again to abstain
- **Persistence**: All state (rounds, groups, links, names, votes, collapsed state) cached in `localStorage` under the key `doujins-state-v1`
- **Reset**: Top-right button clears state and restores the seed

## Tech

- Vanilla HTML/CSS/JS — no build step, no dependencies
- nhentai v2 API: `GET /api/v2/galleries/{id}` (proxied through `corsproxy.io`)
- Cover thumbnails served direct from `t.nhentai.net`

## Local development

Just open `index.html` in a browser, or serve the directory:

```bash
npx serve .
```

## Deployment

GitHub Actions workflow [`deploy.yml`](.github/workflows/deploy.yml) syncs `index.html` into `docs/` on every push to `main`, then publishes `docs/` to GitHub Pages.

## Disclaimer

This is a front-end gallery tool. It fetches publicly available cover thumbnails and metadata from nhentai's JSON API. No content is hosted, proxied, or stored on this site beyond cover image and title. Same class of tooling as a Discord embed viewer.

## License

MIT
