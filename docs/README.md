# Project Page: Perception-aware 3DGS

This folder hosts the project page for

> **Beyond Visual Reconstruction Quality: Object Perception-aware 3D Gaussian Splatting for Autonomous Driving** (ICLR 2026)

built with the [Academic Project Page Template](https://github.com/eliahuhorwitz/Academic-project-page-template)
and styled after [AngleRoCL](https://wenjun-ji.github.io/anglerocl/).

## Publish via GitHub Pages

The page is designed to be served directly from the `docs/` folder of this repository.

1. Push this repository (including `docs/`) to GitHub.
2. In the repository, go to **Settings -> Pages**.
3. Under **Build and deployment** -> **Source**, select **Deploy from a branch**.
4. Set **Branch** to `main` and **Folder** to `/docs`, then click **Save**.

The page will be available at:

```
https://<user>.github.io/Perception-aware-3DGS/
```

A `.nojekyll` file is included so GitHub Pages serves the static files as-is.

## Customization

| File | What to change |
| --- | --- |
| `index.html` | Page content: title, authors, abstract, method, results tables, BibTeX |
| `static/images/teaser.png` | Teaser figure (Figure 1 of the paper) |
| `static/images/overview.png` | Method overview figure (Figure 2 of the paper) |
| `static/images/results_qualitative.png` | Qualitative comparison grid (Figure 4 of the paper) |
| `static/images/social_preview.png` | 1200x630 social-sharing preview image |
| `static/images/favicon.ico` | Browser favicon |

To replace any figure, overwrite the file in `static/images/` with the same name (or update the `<img src>` path in `index.html`), commit, and push; GitHub Pages updates automatically.

## Local preview

```bash
cd docs
python3 -m http.server 8000
# open http://localhost:8000
```