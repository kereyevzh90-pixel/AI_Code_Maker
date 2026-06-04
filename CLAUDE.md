# CodeLearn AI

## Project
Free coding learning platform with an AI tutor. Users can ask coding questions, run code in the browser, follow a structured learning path, and learn any programming language for free.

## Stack
- Pure HTML/CSS/JS (no frameworks)
- Single file: `index.html`

## Deployment
- GitHub: `kereyevzh90-pixel/AI_Code_Maker`
- Hosted on Vercel: `https://ai-code-maker-wqy1.vercel.app`
- Deploy: push to GitHub → Vercel auto-deploys

## Site Structure (sections in order)
1. **Nav** — logo + links: Languages, Playground, AI Tutor, FAQ
2. **Hero** — headline, "Start Learning 🎓" CTA (opens learning modal), demo code window
3. **Onboarding quiz** — 3 steps: language choice (8 languages with descriptions) → skill level → age → personalized recommendation
4. **How it works** — 3 steps
5. **Languages** — 12 language cards (click → AI explains that language)
6. **Downloads** — 13 cards linking to official installers (Python, Node.js, Java, VS Code, Rust, Go, MySQL, Git, C#/.NET, Swift/Xcode, Android Studio, PHP, Ruby, HTML/CSS)
7. **Why CodeLearn AI** — 4 feature cards
8. **Code Playground** — tabs: Python, JavaScript, HTML, Game, JSON
9. **AI Tutor chat** — live chat powered by Groq API
10. **FAQ** — accordion
11. **Footer**

## Learning Path Modal
- Opens via "Start Learning 🎓" button or onboarding result
- Screen 1: Pick language (7 languages with descriptions)
- Screen 2: Pick level (Beginner / Some basics / Intermediate)
- Screen 3: Duolingo-style path — nodes in sine wave layout, connected by dotted SVG line
  - Beginner/Some basics → locked path, starts from node 0
  - Intermediate → all nodes unlocked, pick any
  - Progress saved in `localStorage` per language (`clp_{lang}`)
- Screen 4: Lesson view — AI generates structured lesson (Explanation + Code Example + Exercise), mini Q&A chat for that topic, "Done → next lesson" button
- Curricula: Python (16), JavaScript (14), HTML/CSS (12), Java (13), C++ (13), SQL (12), Rust (12)

## AI Chat
- API: Groq (`https://api.groq.com/openai/v1/chat/completions`)
- Model: `llama-3.3-70b-versatile`
- Conversation history stored in `chatHistory` array, sent with every request
- System prompt: expert coding tutor, responds in user's language

## Code Playground
- **Python** — runs via Pyodide (WebAssembly, in-browser, no API). First load ~10MB, then cached. Line numbers + error line highlighting (red)
- **JavaScript** — runs in iframe, code injected via `JSON.stringify` + `eval` (safe). console.log shown at bottom
- **HTML** — rendered in iframe (sandbox)
- **Game** — JS in iframe with pre-created `<canvas id="gameCanvas">` filling full screen
- **JSON** — parsed and pretty-printed client-side
- Fullscreen button (⛶) to expand output pane
- Line numbers sidebar, synced scroll, Tab = 4 spaces

## Rules
- After every code change, always commit and push to GitHub automatically (no need to ask).
