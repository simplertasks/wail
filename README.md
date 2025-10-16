# WAIL — Web AI Language

## 📜 WAIL Specification Overview

**WAIL (Web AI Markup Language)** is a proposed **markup specification** for creating AI-driven, step-based web applications using simple, declarative syntax.

A WAIL-compliant runtime should be able to:

- Parse a `<script type="wail">` block containing `<meta-data>`, `<view>`, `<data>`, `<ai-generated>`, and optional auxiliary tags.
- Handle `{variable}` interpolation consistently across views.
- Execute `<ai-generated>` instructions using any LLM backend (e.g., Groq, OpenAI, Anthropic).
- Manage state locally or via syncable storage.
- Render steps in an intuitive, mobile-friendly UI flow.

The implementation shown below is an **example WAIL runtime**, built with **vanilla JavaScript**, **PicoCSS**, **Dexie.js**, and **Marked.js**, demonstrating one possible way to realize the WAIL specification in a single self-contained HTML file.

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![No Dependencies](https://img.shields.io/badge/dependencies-zero-green)

WAIL (Web AI Markup Language) is an experimental open-source framework that lets you build AI-powered web applications using only HTML, Markdown, and JSON — no JavaScript or backend required.

A complete WAIL app is just one HTML file that runs anywhere: locally, offline, or on the web.

---

## 🚀 Key Features

- **Single-file apps** — everything (UI, logic, data, AI, persistence) lives inside one HTML file.
- **No JavaScript or CSS required** — authors only write simple markup inside a `<script type="wail">` block.
- **Markdown-driven UI** — easy to design content and steps.
- **AI-ready** — connect to Groq API (free tier available, ~30 requests/min).
- **Offline-first** — built with Dexie.js for local database storage.
- **Mobile-friendly** — responsive layout powered by PicoCSS.
- **Declarative AI scripting** — define what the AI should do, not how to do it.

---

## ⚡ Quick Start

1. Download `index.html` from this repository
2. Get a free API key from [console.groq.com](https://console.groq.com)
3. Open the HTML file in your browser
4. Enter your API key and start building!

<!-- [Try the live demo →](YOUR_GITHUB_PAGES_URL) -->

---

## 🧠 How It Works

A WAIL app combines two parts in one file:

1. **WAIL Runtime**  
   The JavaScript engine that interprets and renders the app — handling navigation, data binding, AI calls, and persistence.

2. **WAIL Script**  
   A simple markup section inside your HTML:

```html
<script type="wail">
  <meta-data>
  {
    "title": "Cities Quiz",
    "author": "J. Smith",
    "description": "A simple quiz testing knowledge of cities."
  }
  </meta-data>

  <ai-generated>
  {
    "ai-selected-city": "randomly select one city from {cities}",
    "ai-grade": "assign only a single letter grade A, B, C, D, or F"
  }
  </ai-generated>

  <view name="welcome">
  # Welcome
  Ready to start your city quiz?
  </view>

  <view name="input">
  Tell us three facts about {ai-selected-city}.
  </view>

  <data name="cities">
  ["London, England", "Tokyo, Japan", "Paris, France"]
  </data>
</script>
```

The runtime parses this script, renders each `<view>` as a step in a wizard, and handles AI-driven variables like `{ai-selected-city}`, `{ai-grade}`, etc.

---

## 🧩 Example: Cities Quiz

The demo app (`index.html`) shows how a WAIL script can:

- Randomly select a city with AI
- Collect user input
- Ask the model to evaluate responses
- Generate a letter grade and fun fact
- Save results locally in Dexie

---

## 📖 WAIL Syntax Reference

| Tag                               | Purpose                        | Example           |
| --------------------------------- | ------------------------------ | ----------------- |
| `<meta-data>`                     | App title, author, description | JSON object       |
| `<view name="">`                  | Wizard step/screen             | Markdown content  |
| `<data name="">`                  | Static data arrays/objects     | JSON or line list |
| `<ai-generated>`                  | AI instructions                | JSON with prompts |
| `<splash>`                        | Entry screen (API key)         | Markdown content  |
| `<help>`, `<about>`, `<settings>` | Auxiliary modals               | Markdown content  |

**Variable Interpolation:**

- Use `{variable-name}` to reference metadata, data, form inputs, or AI-generated content
- Variables are automatically replaced throughout your views

---

## 💬 Creating WAIL Scripts

You only need to know:

- **Basic HTML** (for wrapping your app)
- **Markdown** (for content formatting)
- **JSON** (for metadata and AI instructions)

No need to write or modify any JavaScript — the runtime takes care of everything.

You can even ask ChatGPT or another LLM to generate or edit just the WAIL script for you.

---

## 🎯 Perfect For

- **Educators**: Create interactive quizzes and assignments
- **Researchers**: Quick survey tools with AI analysis
- **Content Creators**: Story generators, writing assistants
- **Prototypers**: Test AI workflows without infrastructure
- **Tinkerers**: Experiment with AI without learning full-stack development

---

## 🌍 Portability

Every WAIL app is a self-contained HTML file:

- Share by email
- Post to GitHub Pages or any static host
- Open directly from your computer — no server needed
- Works offline (Dexie.js caches data locally)

Optional: Dexie can be extended to sync with the cloud, making backups and multi-device sync possible.

---

## ⚖️ Why WAIL?

| Traditional Approach       | WAIL                   |
| -------------------------- | ---------------------- |
| React + Node + DB + API    | One HTML file          |
| npm install, build, deploy | Just open in browser   |
| Hundreds of files          | 1 file                 |
| Requires coding skills     | Markdown + JSON        |
| Need hosting/server        | Works offline          |
| Complex state management   | Automatic data binding |

---

## 🧰 Tech Stack

| Component    | Purpose                   |
| ------------ | ------------------------- |
| PicoCSS      | Clean, responsive UI      |
| Dexie.js     | Local storage (IndexedDB) |
| Marked.js    | Markdown rendering        |
| Lucide Icons | Vector icons              |
| Notyf        | Notifications             |
| Groq API     | AI model integration      |

All libraries loaded via CDN — no build process required.

---

## 🧠 Philosophy

> “AI applications should be as easy to write as Markdown documents.”

WAIL aims to democratize small AI apps — perfect for educators, creators, and curious tinkerers who understand content and structure but don’t want to code full web apps.

It’s inspired by the simplicity of HTML and Markdown, proving that powerful AI applications don’t require complex frameworks or infrastructure.

---

## 🛠️ Roadmap

- [ ] **Cloud sync** — Optional Dexie cloud backup
- [ ] **Themes** — Dark mode and custom color schemes
- [ ] **Templates** — Library of starter WAIL scripts
- [ ] **Multi-model** — Support for OpenAI, Anthropic APIs
- [ ] **Plugin system** — Reusable components and extensions
- [ ] **Visual editor** — GUI for creating WAIL scripts
- [x] **Local storage** — Dexie.js integration ✅
- [x] **Wizard UI** — Step-by-step navigation ✅

---

## 🤝 Contributing

WAIL is experimental and welcomes contributions!

- 🐛 Report bugs in [Issues](../../issues)
- 💡 Suggest features in [Discussions](../../discussions)
- 📝 Share your WAIL apps in Show & Tell
- 🔧 Submit pull requests

All skill levels welcome — whether you’re improving docs, suggesting features, or sharing creative WAIL scripts!

---

## 📄 License

MIT License — free to use, modify, and share.

---

## 💬 Acknowledgements

WAIL is inspired by the simplicity of HTML and Markdown, and powered by open web technologies:

- [PicoCSS](https://picocss.com/) for beautiful minimalist styling
- [Dexie.js](https://dexie.org/) for effortless IndexedDB
- [Marked.js](https://marked.js.org/) for Markdown parsing
- [Lucide](https://lucide.dev/) for crisp icons
- [Groq](https://groq.com/) for blazing-fast AI inference

It’s a small experiment in making AI part of the web’s natural language.

---

## 🔗 Resources

- [Documentation](../../wiki) (coming soon)
- [Examples Gallery](../../discussions/categories/show-and-tell)
- [Groq API Docs](https://console.groq.com/docs)
- [WAIL Script Templates](../../tree/main/templates) (coming soon)

---

**Built with ❤️ for the open web**
