## 🏗️ Story Spark — Architecture Overview (Portfolio Version)

This document provides a high-level architectural overview of the Story Spark application, focusing on the technologies used, how they interact, and the application flow. Sensitive implementation details, proprietary logic, and API code have been intentionally excluded per project security requirements.

## 🌐 1. System Architecture Summary

Story Spark is built as a full-stack AI web application using:

- Next.js (frontend + backend in one framework)
- React (declarative UI)
- Next.js API Routes (serverless backend)
- OpenAI API (AI story generation)
- Vercel (hosting, deployment, serverless execution)

The architecture follows a client → serverless API → OpenAI → serverless API → client cycle.

## 🧩 2. High-Level Architecture Diagram
```
                      ┌─────────────────────────────┐
                      │        Client (UI)           │
                      │  Next.js + React Frontend    │
                      │------------------------------│
                      │• User interacts with UI      │
                      │• Forms, buttons, modules     │
                      │• Sends requests to backend   │
                      └───────────────┬──────────────┘
                                      │
                                      ▼
                    ┌─────────────────────────────────┐
                    │       Serverless Backend        │
                    │       Next.js API Routes        │
                    │---------------------------------│
                    │• Validates input (high-level)   │
                    │• Formats request for AI model   │
                    │• Sends secure call to OpenAI    │
                    │• Handles response                │
                    └──────────────────┬──────────────┘
                                      │
                                      ▼
                     ┌────────────────────────────────┐
                     │            OpenAI API          │
                     │        (GPT Models Used)       │
                     │--------------------------------│
                     │• Processes prompt               │
                     │• Generates structured output    │
                     └──────────────────┬─────────────┘
                                       │
                                       ▼
                       ┌────────────────────────────────┐
                       │     Serverless Backend         │
                       │ (Processes & returns response) │
                       └──────────────────┬─────────────┘
                                          │
                                          ▼
                          ┌────────────────────────────────┐
                          │           Client (UI)          │
                          │• Renders generated output      │
                          │• Displays story modules        │
                          └────────────────────────────────┘
```
## 🧱 3. Application Layers
<h3> **3.1 Frontend (Next.js + React)** </h3>

The UI is built using React components rendered within Next.js pages.

Responsibilities include:
- Rendering interactive writing modules
- Collecting user story inputs
- Sending requests to backend API routes
- Showing structured AI outputs
- Handling loading/error states

All sensitive operations (API keys, AI prompt construction, logic, etc.) are handled server-side only.

**3.2 Backend (Next.js API Routes)**

The backend uses serverless functions provided by Vercel + Next.js:
- Receives writing prompts from the frontend
- Performs high-level validation
- Constructs safe requests for AI model
- Sends/receives data from OpenAI
- Returns structured results to the frontend

These routes run in isolated, auto-scaling serverless environments.

**3.3 AI Integration (OpenAI API)**

The application integrates with:
- GPT-4 / GPT-5.1 / latest available model
- JSON-mode or structured outputs where appropriate
- Secure server-side requests only

OpenAI is used for:
- Spark generation
- Character building
- Worldbuilding
- Plot and beat creation
- Scene drafting
- Writing voice transformations

All prompts, templates, and logic required for these features are stored in a private backend repository and are not included in this public repo.

**3.4 Deployment (Vercel)**

The application is deployed on Vercel, which provides:

- Continuous deployment from GitHub
- Preview deployments for feature branches
- Production deployment for public use
- Serverless function hosting
- SSL, CDN, caching, and routing

Environment variable management (API keys never exposed in frontend)

## 🔐 4. Security Considerations

This public repository intentionally excludes:
- All source code
- All API routes
- All prompt engineering logic
- All OpenAI integration code
- All environment variables
- Any business-proprietary features

Sensitive code is stored in a private repository and may be shared with recruiters upon request.

## 📦 5. Future Architecture (v2) Roadmap

_(High-level only — safe to share publicly)_

- More modular architecture
- Improved UI state management
- Custom user data persistence
- On-device editing tools
- Expanded writing frameworks
- Additional AI-powered story engines

## 💼 6. Contact

To request access to the private version of the repository (for recruiters/hiring managers), please email: 📧 vanisha.pierce@gmail.com 
