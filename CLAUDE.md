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
1. **Nav** — logo + links: Languages, Downloads, Playground, AI Tutor, FAQ + "Start Learning 🎓" button (opens learning modal). All nav links use custom scroll offset (200px) to show section titles properly.
2. **Hero** — headline, "Start Learning 🎓" + "Ask AI Tutor →" buttons, demo code window
3. **Onboarding quiz** — 3 steps: language choice (8 languages with descriptions) → skill level → age → personalized recommendation card with "Open learning path 🎓" button
4. **How it works** — 3 steps
5. **Languages** — 12 language cards (click → AI explains that language)
6. **Downloads** — 14 cards linking to official installers/docs (Python, Node.js, Java, VS Code, Rust, Go, MySQL, Git, C#/.NET, Swift/Xcode, Android Studio, PHP, Ruby, HTML/CSS)
7. **Why CodeLearn AI** — 4 feature cards
8. **Code Playground** — tabs: Python, JavaScript, HTML, Game, JSON
9. **AI Tutor chat** — live chat powered by Groq API
10. **FAQ** — accordion
11. **Footer**

## Learning Path Modal
- Opens via "Start Learning 🎓" in nav or hero, or from onboarding result
- Screen 1: Pick language (7 languages with descriptions)
- Screen 2: Pick level (Beginner / Some basics / Intermediate)
- Screen 3: Duolingo-style path — nodes in zigzag layout, connected by dotted SVG line
  - Zigzag pattern: center → right → left → center (repeating), offset = min(100, containerW/4)
  - Beginner/Some basics → starts from node 0, next node unlocked
  - Intermediate → all nodes unlocked, pick any
  - Progress saved in `localStorage` per language (`clp_{lang}`)
  - Node labels shown below each node
- Screen 4: Lesson view — AI generates structured lesson (Explanation + Code Example + Exercise), mini Q&A chat for that topic, "Done → next lesson" button
- Curricula: Python (16), JavaScript (14), HTML/CSS (12), Java (13), C++ (13), SQL (12), Rust (12)

## AI Chat
- API: Groq (`https://api.groq.com/openai/v1/chat/completions`)
- Model: `llama-3.3-70b-versatile`
- Conversation history stored in `chatHistory` array, sent with every request
- System prompt: expert coding tutor, responds in user's language

## Code Playground
- Width: max 1400px, padding 40px sides
- Height: 650px (editor + output)
- **Python** — runs via Pyodide (WebAssembly, in-browser, no API). First load ~10MB, then cached
- **JavaScript** — runs in iframe, code injected via `JSON.stringify` + `eval` (safe). console.log shown at bottom
- **HTML** — rendered in iframe (sandbox)
- **Game** — JS in iframe with pre-created `<canvas id="gameCanvas">` filling full screen. Canvas name must be `gameCanvas` not `canvas`
- **JSON** — parsed and pretty-printed client-side
- Features: line numbers sidebar (synced scroll), error line highlighting in red (parses `File "<exec>", line X`), auto-closing brackets/quotes `( [ { " '`, Tab = 4 spaces, Backspace removes pair
- Fullscreen button (⛶) to expand output pane

## Rules
- After every code change, always commit and push to GitHub automatically (no need to ask).
