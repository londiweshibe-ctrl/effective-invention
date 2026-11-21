# Biznest – Copilot instructions

## Product
Biznest is a mobile-first PWA that helps South African SMEs and first-time borrowers become financially visible and get funded. Users build a business profile, upload documents, see a business health score, apply for a loan, and compare offers from lending partners. Biznest earns a percentage on funded deals and says so openly.

## Users
Small business owners on mobile and patchy data, often first-time borrowers, not financially literate, wary of fintech. Every screen must use plain language (no banking jargon), say what happens next, and say why we ask for sensitive data.

## Stack
Next.js (App Router, TypeScript), Tailwind CSS, PostgreSQL + Prisma, NextAuth (phone/email OTP), S3-compatible encrypted storage, Zod validation, Vitest + Playwright, GitHub Actions CI. Use pnpm.

## Rules
- Mobile-first at 390px width. One primary action per screen. Progressive disclosure.
- Low-bandwidth: no heavy libraries, compress images client-side before upload, resumable uploads, offline-tolerant forms.
- Accessibility: 16px minimum body text (12px only for captions), 48px minimum touch targets, WCAG AA contrast, real <button>/<a>/<label> elements, no emoji as icons.
- ZAR format "R 1 500,00", dates DD/MM/YYYY. All user-facing strings go through an i18n layer (English first; isiZulu, isiXhosa, Afrikaans later).
- Never hide fees. Never present the health score as a credit score or a verdict. It is guidance.
- POPIA: explicit, logged consent before any data is shared with a partner. Users can download and delete their data. Encrypt documents at rest. Never log document contents or ID numbers.
- Biznest refers; lenders decide. Only NCR-registered partners (store NCR number).
- Never commit secrets. Use .env.example. Use seed data with clearly fictional names only.
- Write tests for business logic (scoring, offer comparison, consent) and one Playwright test per core journey step.

## Design tokens
Font: Inter. Green #0B5D45 (primary, headers), gold #F2B705 (accent on green only), background #F5F6F2, ink #14201B, muted text #4A5750, borders #DDE2DC, light green #E3F1EA (best-value highlight, success chips). Cards: white, 1px border, 14px radius, 14px padding. Buttons: 48px tall, 12px radius, solid green primary, outlined secondary. Header: green block with "Biznest · <section>" in gold above a 22px bold white title. Bottom nav: Docs, Score, Status, Offers, Data.

## Data model
User, Business, Document, HealthScore, Application, Partner, Offer, ConsentRecord, Notification, AuditLog.
