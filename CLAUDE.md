# CodeLearn AI

## Project
Free coding learning platform with an AI tutor. Users can ask coding questions, run code in the browser, and learn any programming language for free.

## Stack
- Pure HTML/CSS/JS (no frameworks)
- Single file: `index.html`

## Deployment
- GitHub: `kereyevzh90-pixel/AI_Code_Maker`
- Hosted on Vercel: `https://ai-code-maker-wqy1.vercel.app`
- Deploy: push to GitHub → Vercel auto-deploys

## Site Structure (sections in order)
1. **Nav** — logo + links: Languages, Playground, AI Tutor, FAQ
2. **Hero** — headline, CTA buttons, demo code window
3. **How it works** — 3 steps
4. **Languages** — 12 language cards (click → AI explains that language)
5. **Why CodeLearn AI** — 4 feature cards
6. **Code Playground** — tabs: Python, JavaScript, HTML, Game, JSON
7. **AI Tutor chat** — live chat powered by pollinations.ai
8. **FAQ** — accordion
9. **Footer**

## AI Chat
- API: `GET https://text.pollinations.ai/{prompt}?model=openai-large&system={system}`
- Plain text response (no JSON parsing)
- Conversation history stored in `chatHistory` array, included as context in each request

## Code Playground
- **Python** — runs via Piston API (`https://emkc.org/api/v2/piston/execute`)
- **JavaScript** — runs in iframe with full DOM/Canvas access, console.log shown at bottom
- **HTML** — rendered in iframe (sandbox)
- **Game** — JS in iframe with pre-created `<canvas id="gameCanvas">` filling full screen
- **JSON** — parsed and pretty-printed client-side
- Fullscreen button (⛶) to expand output pane

## Rules
- After every code change, always commit and push to GitHub automatically (no need to ask).
