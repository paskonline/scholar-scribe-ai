# Scholar Scribe AI 🎓

**Scholar Scribe AI** is an intelligent, client-side research tool designed to bridge the gap between academic reading and systematic literature reviews. It allows researchers to upload journal articles and instantly extract structured methodology, theoretical frameworks, and research objectives into a clean, exportable matrix.

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen.svg?style=for-the-badge)](https://paskonline.github.io/scholar-scribe-ai/)

---

## ✨ Key Features

- **Automated Data Extraction:** Scans papers to extract 17 critical fields including:
  - Theoretical & Practical Problem Backgrounds.
  - Research Objectives (Main & Specific).
  - Research Questions & Hypotheses.
  - Methodology (Population, Sampling, Sample Size, Analysis Methods).
- **Multi-Model Support:** Plug in your own API key for **Google Gemini (Free Tier supported)**, OpenAI (GPT-4o), Anthropic (Claude), or DeepSeek.
- **Privacy-Centric:** No data is uploaded to a central server. Your API keys and research data stay in your browser's `localStorage`.
- **Dual Format Support:** Native parsing for both `.pdf` and `.docx` files.
- **Thesis-Ready Export:** Download your entire matrix as a `.csv` file for Excel/SPSS or save a `.json` backup of your progress.

## 🚀 How to Use

1. **Access the Tool:** Visit the [Live Demo](https://paskonline.github.io/scholar-scribe-ai/).
2. **Setup Provider:** - Click the **Info (i)** icon to see instructions on how to get a free API key.
   - Select your provider (e.g., Gemini) and paste your key.
3. **Upload Articles:** Drag and drop your research papers into the upload zone.
4. **Build your Matrix:** The tool will parse the methodology section and populate the table automatically.
5. **Export:** Click **Export CSV** to move your work into your final thesis document.

## 🛠️ Technical Stack

- **Frontend:** React 18 (via UMD), Tailwind CSS.
- **Parsers:** PDF.js (PDF extraction), Mammoth.js (.docx text processing).
- **Architecture:** 100% Client-side (no backend required).

## ⚖️ License

Distributed under the MIT License. See `LICENSE.md` for more information.

---
*Created by Asitha - Empowering researchers through AI.*
