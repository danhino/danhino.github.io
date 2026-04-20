# Daniel Hinojosa - Personal Portfolio

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Deployed-brightgreen)](https://danhino.github.io)
[![AI Agent](https://img.shields.io/badge/AI%20Agent-Live-4ade80)](https://danhino.github.io/ai-agent.html)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

A modern, responsive personal portfolio website showcasing my experience as a Technical Program Manager specializing in enterprise integrations, API platforms, and FinTech solutions — with an embedded AI agent that answers recruiter and hiring manager questions about my background.

## 🌟 Live Demo

Visit the live site at: [danhino.github.io](https://danhino.github.io)
Chat with the AI agent at: [danhino.github.io/ai-agent.html](https://danhino.github.io/ai-agent.html)

## 📋 Overview

This portfolio highlights:
- **20+ years** of experience in mortgage and financial services technology
- **200+ integrations** delivered across REST and SOAP APIs
- Expertise in MISMO 3.4, OAuth 2.0/JWT, AWS Lambda, Azure DevOps
- Leadership in enterprise-scale programs and cross-functional teams
- Independent consulting projects: AI claims processor (ERA/EOB) and maintenance ticketing system
- Side project: Fuerza Home Services (React Native bilingual home services marketplace)
- **AI-powered resume agent** for recruiters and hiring managers

## 🛠️ Technologies Used

- **Frontend**: Vanilla HTML5, CSS3, JavaScript (ES6+)
- **Styling**: Custom CSS with CSS Variables for theming
- **Fonts**: Google Fonts (JetBrains Mono, Syne, IBM Plex Mono, IBM Plex Sans)
- **Icons**: Inline SVG
- **Hosting**: GitHub Pages
- **AI Agent**: Anthropic Claude API (`claude-haiku-4-5-20251001`) via Cloudflare Worker proxy
- **SEO**: Open Graph, Twitter Cards, JSON-LD structured data
- **Version Control**: Git

## 🎨 Features

- **Responsive Design**: Optimized for desktop, tablet, and mobile
- **Dark Theme**: Modern dark terminal color scheme with green accents
- **Interactive Elements**:
  - Typing animation in hero section
  - Smooth scrolling navigation
  - Fade-in animations on scroll
  - GitHub projects integration
- **AI Resume Agent**:
  - Full-page chat interface at `/ai-agent.html`
  - Floating widget launcher embedded in the main portfolio
  - Category filters (Experience, Skills, Projects, Contact)
  - Clickable recruiter question chips
  - Download Resume CTA (PDF + DOCX)
  - Mobile-responsive with horizontal scrolling chip strip
  - Covers full competency profile: cloud/infra (AWS, Terraform), observability (CloudWatch, Splunk), AI/NLP, Agile delivery, and more
- **Performance Optimized**: Lightweight, fast-loading static site
- **SEO Optimized**: Meta description, Open Graph tags, Twitter Cards, canonical URL, JSON-LD structured data
- **Accessibility**: Semantic HTML and keyboard navigation

## 📁 Project Structure

```
danhino.github.io/
├── index.html                           # Main portfolio page (with floating AI widget)
├── ai-agent.html                        # Full-page AI resume agent
├── favicon.svg                          # Site favicon (portfolio)
├── favicon-agent.svg                    # Site favicon (AI agent page)
├── og-image.png                         # Open Graph preview image (1200x630)
├── Daniel_Hinojosa_Resume_Styled.pdf    # Resume PDF
├── Daniel_Hinojosa_Resume_Styled.docx   # Resume Word doc
└── README.md                            # This file
```

## 🤖 AI Agent Architecture

The AI agent allows anyone visiting the portfolio to ask natural language questions about my experience, skills, and availability — without exposing any API credentials in the browser.

```
Browser → Cloudflare Worker (proxy) → Anthropic Claude API
              ↑ API key lives here only, encrypted at rest
```

**Security model:**
- The Anthropic API key is stored as an encrypted secret in a Cloudflare Worker
- The browser never sees the key — it only calls the Worker endpoint
- CORS is locked to `https://danhino.github.io` only
- Rate limiting: 20 requests per IP per hour via Cloudflare Workers KV

**Cloudflare Worker:** `daniel-aiagent-proxy.dan-hinojosa.workers.dev`
**Model:** `claude-haiku-4-5-20251001` (fast, cost-efficient for conversational Q&A)
**KV namespace:** `rate-limit-store` bound as `RATE_LIMIT`

### Updating the Agent's Knowledge

The AI agent's profile data lives in the `SYSTEM_PROMPT` constant near the top of `ai-agent.html`. Update it whenever your resume, projects, or job search status changes — no backend changes required.

## 🚀 Deployment

This site is automatically deployed via GitHub Pages from the `main` branch.

### Local Development

1. Clone the repository:
   ```bash
   git clone https://github.com/danhino/danhino.github.io.git
   cd danhino.github.io
   ```

2. Open `index.html` in your browser or use a local server:
   ```bash
   # Using Python
   python -m http.server 8000

   # Using Node.js
   npx serve .
   ```

3. Make changes and test locally before committing.

> **Note:** The AI agent requires the Cloudflare Worker to be deployed and the `ANTHROPIC_API_KEY` secret to be set. Local testing will return CORS errors since the Worker only accepts requests from `https://danhino.github.io`.

### Customization

To adapt this portfolio for your own use:

1. Update the CSS variables in `:root` for colors and branding
2. Replace content in the HTML sections (About, Experience, Contact)
3. Update the `SYSTEM_PROMPT` in `ai-agent.html` with your own profile data
4. Deploy your own Cloudflare Worker and update the fetch URL in both HTML files
5. Add your `ANTHROPIC_API_KEY` as a secret in the Worker settings
6. Update the GitHub username in the JavaScript config
7. Add your own resume files

## 📞 Contact

- **Email**: dan.hinojosa@gmail.com
- **LinkedIn**: [linkedin.com/in/danhinojosa](https://linkedin.com/in/danhinojosa)
- **GitHub**: [github.com/danhino](https://github.com/danhino)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Built with vanilla HTML · AI agent powered by Claude (`claude-haiku-4-5-20251001`) · Hosted on GitHub Pages · © 2026 Daniel Hinojosa
