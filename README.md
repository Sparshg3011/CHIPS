# CHIPS

**Cloud and Hardware Integration Platform for Small Software.** An agentic forward deployed engineer that sits between small software vendors and their customers and handles discovery, customization, deployment, integration and support, so small deals become economical for both sides.

This repo is a static site with two parts:

| Path | What it is |
|---|---|
| `/` (`index.html`) | Clickable prototype of the full loop: discovery chat → vendor matching → live sandbox → auto-generated spec (CSRS) → deployment with tests → after go-live changes, upgrades and support. Includes a seller-side console and an **Auto-play demo** button. |
| `/pitch/` (`pitch/index.html`) | Narrated, hand-drawn pitch film (17 scenes, about 5 minutes). Narration clips are in `pitch/vo/`. |
| `docs/pitch-script.md` | The narration as speaker notes, plus sources for every statistic. |

No build step and no dependencies to install. Fonts load from Google Fonts and the film's hand-drawn style uses [rough.js](https://roughjs.com/) from jsDelivr.

## Run it locally

```bash
python3 -m http.server 8000
# prototype: http://localhost:8000/
# pitch film: http://localhost:8000/pitch/
```

Open it through a local server rather than double-clicking the file, so the narration clips load.

## Deploy on Netlify

1. In Netlify, choose **Add new site → Import an existing project → GitHub** and pick this repo.
2. Leave **Build command** empty. **Publish directory** is `.` (already set in `netlify.toml`).
3. Deploy. The prototype is at the site root and the film at `/pitch/`.

Every push to `main` redeploys automatically.

## How the prototype works

- The agent's replies are scripted and run entirely in the browser; there is no backend or API key.
- Dashboard numbers are computed live from a 13-week sample of bakery orders, or from your own CSV (columns: `date, product, qty, price, cost`; `cost` and `date` are optional). Use **Sample CSV** in the sandbox to see the format.
- Vendor fit scores come from a simple capability model: core product, configuration, custom workflow, or not covered, weighted by must-have vs nice-to-have requirements.
- Pricing shown (DataVis plans, 15% success fee, $49/month care fee) is illustrative.
