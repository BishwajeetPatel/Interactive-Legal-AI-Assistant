A prototype web-based chat assistant for Indian corporate & employment law (EPF Act 1952, TDS/TCS, Companies Act 2013). It provides contextual, section-referenced answers, quick-action buttons, and an interactive chat UI. The current build simulates AI responses client-side and is designed to be hooked to real models or APIs in a production deployment.

Table of contents

Project overview

Key features

Tech stack

Getting started (local)

Environment variables

Usage

Integrating a real AI model

Suggested improvements & roadmap

Security & legal notes

License & contributors

Project overview

This project is a responsive, accessible web application that simulates a legal AI assistant focused on Indian statutory topics: Employees’ Provident Fund (EPF), TDS/TCS rules, and Companies Act provisions. It is ideal as a prototype for internal compliance tools or client-facing legal help centers.

Use cases:

Internal compliance quick-reference for HR / Finance teams

Interview / demo project showcasing full-stack, real-time UI, and knowledge-driven dialogue flows

Foundation for a production assistant after adding backend, auth, and live AI integration

Key features

Modern responsive HTML/CSS chat UI with animations and typing indicators

Knowledge-base driven answers with section references (EPF Act 1952, TDS/TCS, Companies Act)

Intent detection & rule-based response simulation (neural network / decision-tree / random-forest stubs)

Conversation history + context awareness for follow-up Qs

Quick-query buttons for common questions (rates, forms, procedures)

Demo-only offline AI simulation (easy to replace with real APIs)

Tech stack

Frontend: HTML5, CSS3 (responsive, animations), Vanilla JavaScript

(Optionally) Backend: Node.js + Express (suggested for production)

Storage: JSON or DB (Mongo/Postgres) for logs & KB (current prototype uses in-memory / static JSON)

AI: Simulated models in JS (replace with OpenAI/Anthropic/Gemini/etc. via backend proxy)

Getting started (local)

Assumes you have Node.js installed if you want to run a local server. The UI also works as static files.

Clone the repo

git clone <repo-url>
cd legal-ai-assistant


If you want a static preview:

Open index.html in your browser.

To run with a simple Node static server (recommended for consistent behavior):

# install http-server globally (or use any static server)
npm install -g http-server
http-server -c-1 .  # -c-1 disables caching
# open http://localhost:8080


To run with an Express backend (example skeleton):

# inside project root
npm init -y
npm install express body-parser dotenv
# create server.js (example provided in docs/server-example.js)
node server.js

Environment variables

When integrating real services or running a backend, use .env:

# .env example
PORT=3000
OPENAI_API_KEY=sk-xxxx
AI_PROVIDER=openai
AI_MODEL=gpt-4o-mini
DB_URI=mongodb+srv://user:pass@cluster/mydb
JWT_SECRET=your_jwt_secret


Never commit keys to source control. Use a secrets manager for production.

Usage

Open the app in a browser.

Type a legal question (e.g., “What is the current EPF employer contribution rate?”) or use quick buttons.

The assistant returns a simulated answer referencing the law and section numbers.

Conversation history is shown on the left; click any message to copy or use as follow-up context.

Integrating a real AI model

Recommended architecture: Browser → Backend (Express) → AI Provider (OpenAI/Anthropic/GCP)
Reasons:

Keep API keys secure on the server

Implement rate-limiting, caching (responses), and prompt engineering centrally

Add logging, analytics, and audit trails for legal accuracy

High-level steps

Create an Express endpoint /api/chat to receive user messages and conversation context.

Build prompts that include the KB snippets and the user message (system + assistant + user style).

Call the AI provider API from backend, return responses to frontend.

Add fallback/hard-coded rules for high-risk legal claims or out-of-scope Qs.

Cache legal static content locally and only use the model for reasoning/formatting.

Prompt design tip: Always prompt the model to cite statutory sections and include a “confidence / source” line.

Suggested improvements & roadmap

Replace simulated AI responses with a secure backend connected to a modern LLM (OpenAI, Gemini, etc.).

Implement incremental KB updates and versioning to track legal amendments.

Add role-based authentication and request throttling for enterprise use.

Add PDF/Doc upload + extractor to answer questions about user documents.

Add human-in-the-loop review for high-stakes outputs (e.g., final legal advice).

Add automated tests for KB accuracy and end-to-end UI flows.

Security & legal notes

This prototype does not provide legal advice. It is for informational/demo purposes.

For production use: include disclaimers, logging, and a lawyer-review workflow.

Ensure compliance with data protection laws when storing user Q&A or uploaded documents.

Implement rate-limiting, XSS protections, CSRF tokens, and secure cookie/JWT handling.

License & contributors

License: add a LICENSE file (MIT suggested for demos)

Contributors: add your name(s) and contact info (example: Bishwajeet Patel — bishwajeetpatelbth@gmail.com
)

Acknowledge sources for statutes, official PDFs, or third-party libraries.
