# 🎓 Undergraduate Thesis — Presentation

This repository contains the **presentation slides** for my undergraduate thesis, built with [Slidev](https://github.com/slidevjs/slidev) — an open-source tool for creating interactive, Markdown-based slides powered by Vue.

* 🌐 **Live Slides:** [gh/thesis-slides/](https://humankernel.github.io/thesis-slides/)
* 📘 **Thesis Document:** [gh/main.pdf](https://humankernel.github.io/thesis/main.pdf)
* 💻 **Thesis Code:** [gh/rag](https://github.com/humankernel/rag)

## 🧩 Getting Started

To run the slides locally:

```bash
bun install
bun dev
```

Then open your browser at **[http://localhost:3030](http://localhost:3030)**.

## 📝 Editing the Slides

All slide content is written in **Markdown** and located in [`slides.md`](./slides.md).
Edits automatically update in real time while running `bun dev`.

## 📦 Build for Deployment

To build a static version of the slides (output in `dist/`):

```bash
bun run build
```

The generated site can be served with any static web server or deployed automatically using **GitHub Actions** (as configured in this repo).

## 📚 Learn More

* 📘 [Slidev Documentation](https://sli.dev/)
* 💻 [Slidev GitHub Repository](https://github.com/slidevjs/slidev)

Would you like me to make a short **“About this thesis”** paragraph (like a 2–3 sentence summary of the research topic) to include at the top for context?
