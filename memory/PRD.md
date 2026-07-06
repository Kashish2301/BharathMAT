# BharathMAT — Bharat Election Media Intelligence

## Problem Statement
Build a responsive single-page AI web application called BharathMAT to help Indian citizens, journalists, election volunteers and fact-checkers quickly assess whether an image or text claim related to elections should be investigated further. This is NOT a fake detector — it provides AI-assisted risk assessment (Low/Medium/High) with warning signs and recommendations, and always advises verification through official sources.

## Architecture
- **Frontend**: React 19 + Tailwind CSS + Framer Motion + lucide-react icons + Sonner toasts
- **Backend**: FastAPI + Motor (MongoDB) + emergentintegrations LlmChat
- **LLM**: Claude Sonnet 4.6 (`claude-sonnet-4-6`) via Emergent Universal LLM Key
- **Vision**: Server fetches image URL, base64-encodes, sends via `ImageContent` to Claude

## User Personas
- Journalists verifying election-related media before publishing
- Election volunteers spotting suspicious viral claims
- Fact-checkers triaging incoming tips
- Concerned citizens vetting WhatsApp forwards

## Core Requirements (static)
- Never claim content is definitively real or fake
- Always show AI Risk Assessment disclaimer
- Return exactly 3 red flags per analysis
- Support both Image URL (vision) and Text/Quote input
- Generate downloadable/printable report

## Implemented (2026-02-06)
- [x] FastAPI backend with `/api/analyze` (text + image via Claude vision) and `/api/analyses` list endpoint
- [x] MongoDB persistence of every analysis
- [x] React dashboard with sticky header, shield logo, ELECTION SAFETY badge
- [x] Tabs for Image URL / Text-Quote
- [x] Animated confidence bar with shimmer
- [x] Color-coded risk card (Green / Orange / Red) with glow
- [x] 3 warning-sign cards (grid), recommendation card (blue border + lightbulb)
- [x] Empty / Loading / Error states
- [x] Report generation (in-page + PDF via browser print)
- [x] Persistent orange-bordered AI Risk Assessment disclaimer
- [x] Responsive mobile layout
- [x] Full E2E test pass (100% backend, 100% frontend)

## Prioritized Backlog
### P1
- Rate limiting / abuse protection on `/api/analyze`
- History drawer showing recent analyses from `/api/analyses`
- Copy-to-clipboard for report contents
### P2
- Multi-language UI (Hindi, Tamil, Bengali)
- Image upload (in addition to URL)
- Batch analysis
- Shareable report links
- Reverse-image-search integration hint
### P3
- Auth for saving analyses per user
- Team workspaces for newsrooms

## Next Tasks
- Consider adding a public "recent verified claims" feed (community + editorial)
- Add rate-limiting
- Optional: PDF export using jsPDF for pixel-perfect output instead of print dialog
