# Evidence Judge: standalone demo

A static website: no server code and no build step. Everything needed is in this folder.

## Put it online with GitHub Pages (about 5 minutes)
1. On github.com, create a new **public** repository, e.g. `evidence-judge`.
2. Click **Add file → Upload files** and drag in everything in this folder (index.html, img/, model/). Commit.
3. Go to **Settings → Pages**, under "Build and deployment" choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
4. After about a minute the site is live at `https://<your-username>.github.io/evidence-judge/`.

Alternative without Git: drag this folder onto https://app.netlify.com/drop (needs a free account to keep the site).

## What runs where
- **Stage 1 (similarity ranking):** all-MiniLM-L6-v2 runs in the visitor's browser, so it works for anyone with no key or account. The page downloads the model once (23 MB, the files in `model/`).
- **Stage 2 (LLM judge) and image descriptions:** visitors paste their own OpenAI key (default model gpt-4.1, the thesis model) or Anthropic key. The key stays in the browser tab and is sent only to that provider. Nothing is stored.

## Test locally
Run `python3 -m http.server` in this folder and open http://localhost:8000. Opening index.html directly from disk will not load the model, because browsers block fetch() on file:// pages.
