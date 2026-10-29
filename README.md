# Agentic-based Multimodal HyperGraphRAG as Reranker: interactive demo

A static website: no server code and no build step. Everything needed is in this folder.

## Put it online with GitHub Pages (about 5 minutes)
1. On github.com, create a new **public** repository, e.g. `evidence-judge`.
2. Click **Add file → Upload files** and drag in everything in this folder (index.html, img/, model/). Commit.
3. Go to **Settings → Pages**, under "Build and deployment" choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
4. After about a minute the site is live at `https://<your-username>.github.io/evidence-judge/`.

Alternative without Git: drag this folder onto https://app.netlify.com/drop (needs a free account to keep the site).

## What runs where
- **Stage 1 (similarity ranking):** all-MiniLM-L6-v2 runs in the visitor's browser (plain JavaScript, `model/`, 23 MB). It works for anyone, with no key or account.
- **Stage 2 (judge) and image descriptions.** There are three choices:
  - **Qwen2.5 in the browser (default):** open source, via WebLLM (`vendor/`). Needs WebGPU (current Chrome or Edge). Models: Qwen2.5-1.5B, 3B (default) or 7B. Images are described with Phi-3.5-vision, because WebLLM has no Qwen vision model. On first use the model downloads from Hugging Face and is then cached in the browser.
  - **Qwen2.5-VL on your own laptop via Ollama:** `ollama pull qwen2.5vl:7b`, then `OLLAMA_ORIGINS=https://omarmellouli.github.io ollama serve`.
  - **Claude API:** the visitor pastes their own Anthropic key. The key stays in the browser tab.

## Test locally
Run `python3 -m http.server` in this folder and open http://localhost:8000. Opening index.html directly from disk will not load the model, because browsers block fetch() on file:// pages.
