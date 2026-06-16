# Prior Knowledge: Web Frontend Engineering Background

User has 2-3 years of professional frontend experience with Vue 3 and React, uses Vite as build tool, and has worked with Firebase for backend services. Also has hands-on experience building a Python FastAPI backend. Has created a basic Expo + React Native prototype but self-assesses understanding of RN internals (bridge, native modules, threading) as superficial.

**Evidence:** User's self-report; confirmed by detailed description of tech stack and specific knowledge gaps.

**Implications:**
- React fundamentals (hooks, component lifecycle, JSX) can be assumed — no need to re-teach React itself
- Build tooling concepts (bundling, hot reload, env vars) are understood — Vite knowledge transfers partially to Metro
- API design and REST concepts are solid from FastAPI experience
- The main gap is the **mobile runtime model** — how RN differs from browser-based React
- Navigation, gestures, animations, native modules, and app store deployment are all new or shallow
- Lesson design should map web concepts to RN equivalents, highlighting where the mental model diverges
