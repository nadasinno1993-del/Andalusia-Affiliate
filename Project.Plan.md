# Andalusia Affiliate — Doctor App
## Complete Product & Engineering Plan

Prepared as a practical, beginner-friendly blueprint you can hand to a designer or developer and start building immediately. Based on your logo, brand colors, the "Fast. Simple. Reliable." slogan, the Doctor App flow you provided, and the visual language of the Andalusia Hospitals Egypt platform (bilingual Arabic/English, clean clinical UI, green & gold identity).

---

## 1. App Name

**Andalusia Affiliate**

This name is already strong — keep it. Here's the reasoning behind why it works, so you can defend it in stakeholder conversations:

- **"Andalusia"** ties directly to the parent brand (Andalusia Hospitals Group), inheriting trust, recognition, and the medical credibility patients and doctors already associate with it.
- **"Affiliate"** signals precisely what the app is: a dedicated portal for *affiliated/partner doctors* — not patients, not the general public — who refer procedures and cases into the Andalusia network. It sets the right expectation the moment someone downloads it.
- The mosaic star/lantern mark in your logo (green outline, gold center) reflects Andalusian-Islamic architectural heritage — a subtle nod to the "Andalusia" name's historical origin, while still feeling like a modern medical-tech mark.

**Optional internal/short name:** "Andalusia Affiliate" can be shortened to **"AA Doctor Portal"** internally by the engineering team for repo/package naming (e.g. `andalusia-affiliate-app`).

---

## 2. Slogan

> **"Fast. Simple. Reliable."**

This is kept as provided — it's an excellent fit because it maps 1:1 onto the three things a busy doctor actually cares about when referring a case:
- **Fast** → AI document scanning, 15-minute pricing turnaround, 10-minute coordinator confirmation
- **Simple** → one clear linear flow, no clutter, doctor-only interface
- **Reliable** → transparent pricing, confirmed scheduling, secure payment

---

## 3. Concept & Idea

### Core Idea
Andalusia Affiliate is a **mobile-first referral and case-submission portal for affiliated doctors**. Instead of calling a hospital coordinator, faxing documents, or waiting days for a price quote, a doctor:

1. Scans a patient's medical document with their phone camera,
2. Lets AI extract/read the document,
3. Enters procedure details,
4. Gets a firm price back from the hospital,
5. Books an operation slot,
6. Confirms and pays,
7. Rates the experience afterward.

The entire hospital-side pricing, coordination, and scheduling logic happens behind the scenes; the doctor only sees a clean, linear, "next step" experience.

### Target Audience
- **Primary:** Independent and affiliated doctors, clinics, and small practices who refer patients to Andalusia Hospitals for procedures, surgeries, or diagnostics they cannot perform themselves.
- **Secondary (future phase):** Referral coordinators/agents working on behalf of multiple doctors; clinic administrative staff submitting on a doctor's behalf.
- **Not in scope for this app:** Patients themselves (they would use a separate patient-facing app), hospital internal staff/back-office (they use the existing HMIS/reporting system you referenced).

### Problem It Solves
Today, referring a procedure to a hospital partner network is typically:
- Manual (phone calls, WhatsApp, paper forms)
- Slow (pricing takes days, no visibility into status)
- Opaque (doctor doesn't know if the request was received, priced, or scheduled)
- Error-prone (documents get lost or misread)

Andalusia Affiliate compresses this into a single, trackable, mobile app flow — reducing coordination time from days to minutes and giving the doctor real-time visibility at every stage.

---

## 4. User Flow

This is your provided flow, organized as a formal step-by-step journey with decision branches:

```
1. Onboarding
   └── Doctor opens app → Sign Up with mobile number → Set password → Login

2. Home
   └── "Welcome, Doctor" → Tap "Create New Request"
        (Home also shows: list of past/active requests + their status)

3. New Request
   └── Choose: "Take a Photo" (camera) OR "Upload from Gallery"
        → Document attached

4. AI Scan Processing
   └── "Scanning document…" (loading state)
        → "Your document is being analyzed" (progress state)
        → "Scan completed successfully" (success state)
        → [If scan fails] → "Couldn't read document, retake photo?" (retry loop)

5. Procedure Details
   └── Enter procedure name (free text or searchable list)
        → Add external tools/equipment needed (optional field)
        → Tap "Submit request for pricing"

6. Pricing — Waiting
   └── "Your request is under review"
        → "Estimated response time: 15 minutes"
        → Push notification sent when ready

7. Pricing — Result
   └── "Total cost: [amount]"
        → Doctor taps "Accept" or "Reject"
        → [If Reject] → back to Home, request marked "Cancelled"
        → [If Accept] → proceed to scheduling

8. Schedule Operation
   └── Select date → Select time → Choose from available slots → Confirm

9. Coordinator Confirmation
   └── "Waiting for coordinator confirmation"
        → "You will receive confirmation within 10 minutes"
        → Push notification when confirmed

10. Payment
    └── "Proceed to payment" → Choose "InstaPay" or "Bank Transfer"
         → Upload payment proof (if bank transfer) or redirect to InstaPay
         → Payment status: Pending → Confirmed

11. After Operation
    └── Hospital marks case complete → Doctor sees "Operation completed successfully"

12. Rating & Feedback
    └── Star rating → Optional comment → "Submit feedback"
         → Return to Home; request archived under "Completed"
```

**Key UX principle:** at every waiting step (scanning, pricing, coordinator confirmation, payment), the doctor should be able to leave the app and come back — status is always visible on the Home screen, and push notifications close the loop.

---

## 5. Wireframes (Structured Text Layout)

### Screen 1 — Login / Sign Up
```
[Status bar]
[Andalusia Affiliate logo, centered, top 20%]
"Andalusia Affiliate"
"Fast. Simple. Reliable."

[Tab switch: Login | Sign Up]

Phone Number       [______________]
Password           [______________]  (Sign Up only: Confirm Password)

[ Login / Create Account — full-width primary button, green ]

"Forgot password?" (text link, small, centered)
Language toggle (EN / AR) — top-right corner
```

### Screen 2 — Home
```
[Top bar]  Andalusia Affiliate logo (small) ......... [Profile icon]
"Welcome, Doctor [Name]"

[ + Create New Request ]  ← large primary button, gold accent, full-width

--- "Your Requests" ---
[Card] Request #1024   Status: Pricing Review     >
[Card] Request #1023   Status: Scheduled          >
[Card] Request #1020   Status: Completed ★★★★★     >

[Bottom nav: Home | Requests | Notifications | Profile]
```

### Screen 3 — New Request
```
"Upload or capture a medical document"

[ 📷 Take a Photo ]     [ 🖼 Upload from Gallery ]
   (two large tappable cards side-by-side)

[Preview thumbnail appears once selected]
[ Continue → ] (disabled until a document is attached)
```

### Screen 4 — AI Scan Processing
```
(Centered, full-screen state, no navigation to prevent interruption)
[Animated scanning icon / progress ring]
"Scanning document…"
   ↓ (after processing)
"Your document is being analyzed"
   ↓ (on success)
✅ "Scan completed successfully"
[ Continue → ]
```

### Screen 5 — Procedure Details
```
"Procedure Details"

Procedure Name      [______________] (autosuggest dropdown)
External Tools (optional)  [______________]
Notes (optional)     [______________]

[ Submit Request for Pricing ] ← primary button
```

### Screen 6 — Pricing Waiting
```
[Illustration: clock / hourglass]
"Your request is under review"
"Estimated response time: 15 minutes"

[ Back to Home ] (secondary/ghost button — doesn't cancel the request)
```

### Screen 7 — Pricing Result
```
"Pricing Result — Request #1024"

Total Cost
[  4,200 EGP  ]  ← large, bold, centered

"Do you want to proceed?"

[ ✅ Accept ]     [ ❌ Reject ]
 (green, primary)  (outline, red text)
```

### Screen 8 — Schedule Operation
```
"Select Operation Date"
[Calendar picker]

"Available Time Slots"
[ 9:00 AM ] [ 11:30 AM ] [ 2:00 PM ] [ 4:30 PM ]
 (chip buttons, selected state = filled gold)

[ Confirm Slot ]
```

### Screen 9 — Coordinator Confirmation
```
[Illustration: calendar + checkmark, pending state]
"Waiting for coordinator confirmation"
"You will receive confirmation within 10 minutes"

[ Back to Home ]
```

### Screen 10 — Payment
```
"Proceed to Payment"

[ Pay via InstaPay ]   → opens InstaPay deep link / QR
[ Pay via Bank Transfer ] → shows bank details + "Upload Proof of Payment"

Payment status badge: Pending / Confirmed
```

### Screen 11 — After Operation
```
[Illustration: checkmark / celebration]
"Operation completed successfully"
[ Rate Your Experience → ]
```

### Screen 12 — Rating & Feedback
```
"Rate your experience"
★ ★ ★ ★ ★  (tap to select)

"Leave a comment"
[ Text area ______________ ]

[ Submit Feedback ]
```

**Navigation model:** bottom tab bar (Home, Requests, Notifications, Profile) is visible everywhere *except* the linear request flow (Screens 3–11), which is a full-screen guided flow with a back arrow only — this keeps the doctor focused on completing one request at a time, matching your note that the workflow should be "clean, simple, focused on speed and clarity."

---

## 6. UI Design

### Color Palette (derived directly from your logo)

| Role | Color | Hex (approx.) | Usage |
|---|---|---|---|
| Primary / Brand | Deep Forest Green | `#1F4A3D` | Headers, primary buttons, icons, logo mark |
| Accent | Warm Gold | `#B4914E` | Highlights, active states, dividers, "Affiliate" label style |
| Background | Warm Cream / Ivory | `#F6EFE2` | App background, cards |
| Surface | Off-white | `#FFFFFF` | Cards, input fields, modals |
| Text — Primary | Charcoal | `#22221F` | Body text |
| Text — Secondary | Warm Gray | `#7A756B` | Captions, placeholders |
| Success | Muted Green | `#2E7D5B` | "Completed", "Confirmed" states |
| Warning / Pending | Gold-Amber | `#C79A3E` | "Under review", waiting states |
| Error / Reject | Muted Red | `#B3453D` | Reject button, error states |

This keeps the app visually consistent with the existing Andalusia brand and hospital website (which also uses deep green + gold on light backgrounds), so the doctor recognizes it instantly as "Andalusia."

### Typography
- **Latin (English):** *Poppins* or *Inter* for UI text (clean, modern, highly legible on mobile) — use **Semibold** for headings, **Regular** for body.
- **Arabic:** *Tajawal* or *Cairo* (both are free, designed for UI, and pair well visually with Poppins/Inter) — essential since the platform is bilingual (as seen on andalusiaegypt.com).
- **Logo wordmark style:** keep the serif "Andalusia" as-is only in branding/splash contexts; use the sans-serif fonts above for all in-app UI text for readability at small sizes.
- Scale suggestion: H1 24px / H2 20px / Body 16px / Caption 13px, generous line-height (1.4–1.5) for medical/legal clarity.

### Design Style
- **Minimal, clinical-modern** — lots of white/cream space, one primary action per screen, no visual clutter.
- **Card-based** components with soft rounded corners (12–16px radius), echoing the rounded-square logo tile.
- **Full RTL support** — Arabic layout must mirror correctly (right-aligned text, mirrored icons/back arrows) since the parent brand is Arabic-first.
- **Micro-interactions:** subtle progress animations on the AI scanning screen, gentle success checkmarks, haptic feedback on button taps — reinforces "Fast. Simple. Reliable." emotionally, not just functionally.

---

## 7. Frontend

### Recommended Technology
- **Framework:** **React Native (with Expo)** — single codebase for iOS + Android, fastest path from this plan to an App Store/Play Store build, huge ecosystem for camera/document scanning and push notifications.
  - *Alternative if you prefer native performance and have separate iOS/Android teams:* Swift (iOS) + Kotlin (Android).
- **Navigation:** `react-navigation` (stack navigator for the linear request flow, bottom-tab navigator for Home/Requests/Notifications/Profile).
- **State management:** `Zustand` or `Redux Toolkit` (Zustand is lighter-weight and easier for beginners).
- **Camera / document capture:** `expo-camera` + `expo-image-picker` for gallery upload.
- **Forms:** `react-hook-form` for the Procedure Details form.
- **Push notifications:** `expo-notifications` (or Firebase Cloud Messaging directly).
- **Internationalization:** `i18next` + `react-i18next` for full EN/AR bilingual + RTL support.
- **Styling:** `NativeWind` (Tailwind CSS for React Native) so the color palette/typography tokens above map directly to reusable utility classes.

### Structure & Components
```
/src
  /screens
    Auth/ (LoginScreen, SignUpScreen)
    Home/ (HomeScreen, RequestCard)
    NewRequest/ (UploadScreen, ScanProcessingScreen, ProcedureDetailsScreen)
    Pricing/ (PricingWaitingScreen, PricingResultScreen)
    Scheduling/ (ScheduleScreen, CoordinatorConfirmationScreen)
    Payment/ (PaymentScreen)
    Feedback/ (CompletionScreen, RatingScreen)
    Profile/ (ProfileScreen, NotificationsScreen)
  /components
    PrimaryButton, StatusBadge, DocumentPreview, StarRating, SlotChip, LoadingState
  /navigation
    AuthStack.js, AppTabs.js, RequestFlowStack.js
  /services
    api.js (axios instance), authService.js, requestService.js, paymentService.js
  /store
    useAuthStore.js, useRequestStore.js
  /i18n
    en.json, ar.json
  /theme
    colors.js, typography.js, spacing.js
```

Each screen in the linear flow (Screens 3–11) is a **controlled step** that reads/writes to a single `currentRequest` object in the store, so the doctor's progress is never lost if they background the app.

---

## 8. Backend

### Recommended Technology
- **Runtime/Framework:** **Node.js with NestJS** (TypeScript) — structured, scalable, great fit for a healthcare-adjacent product where clear module boundaries (Auth, Requests, Pricing, Scheduling, Payments) matter.
  - *Alternative:* Laravel (PHP) — worth strongly considering since the existing Andalusia HMIS/reporting system you linked appears to run on a similar enterprise-PHP stack, which would simplify integration and let one backend team maintain both.
- **API style:** REST (simplest for a mobile client) with a versioned base path (`/api/v1/...`); GraphQL is optional but likely overkill for this scope.
- **Authentication:** JWT-based auth (access + refresh tokens), phone number + OTP verification for sign-up (use a provider like Twilio Verify or a local Egyptian SMS gateway).
- **File storage:** Uploaded medical documents go to **S3-compatible object storage** (AWS S3 or DigitalOcean Spaces), never stored directly in the database.
- **AI Document Scanning:** Use a document/OCR AI service (e.g., Google Cloud Vision OCR, AWS Textract, or Anthropic/Claude with vision for structured field extraction) — backend receives the image, calls the OCR/AI service, stores extracted text/fields against the request.
- **Background jobs / queues:** `BullMQ` (Redis-backed) for anything async — the AI scan step, "pricing review" simulation, and notification dispatch should all be queued jobs, not blocking HTTP requests.
- **Notifications:** Firebase Cloud Messaging (push) + optional SMS for critical status changes (pricing ready, coordinator confirmed).

### Request Handling Logic (example: Pricing flow)
```
1. Mobile app → POST /api/v1/requests  (with procedure details + document reference)
2. Backend validates payload → creates Request row (status: "pending_pricing")
3. Backend enqueues an OCR job (if document not yet processed) → AI service extracts text
4. Backend enqueues a "pricing" job → routed to internal pricing team dashboard
5. Hospital pricing staff (via internal admin panel, not this app) sets a price
6. Backend updates Request status → "priced" → triggers push notification to doctor
7. Doctor's app polls or receives a push → GET /api/v1/requests/:id → renders Pricing Result screen
8. Doctor accepts → POST /api/v1/requests/:id/accept → status → "awaiting_schedule"
```

This same pattern (create → queue → external actor updates status → notify → mobile app reacts) repeats for scheduling, coordinator confirmation, and payment — keeping the API predictable and each stage independently testable.

---

## 9. Database

### Recommended Type
**PostgreSQL** — relational, strong support for structured medical/financial records, transactional integrity (important for payments and pricing), and works cleanly with NestJS via `TypeORM` or `Prisma`.

### Main Data Models

```
Doctor
- id (uuid)
- full_name
- phone_number (unique)
- password_hash
- clinic_name (optional)
- specialty (optional)
- language_preference (en/ar)
- created_at

Request
- id (uuid)
- doctor_id (FK → Doctor)
- status (enum: draft, scanning, pending_pricing, priced, accepted, rejected,
           awaiting_schedule, scheduled, awaiting_confirmation, confirmed,
           awaiting_payment, paid, completed, rated, cancelled)
- procedure_name
- external_tools (nullable text)
- notes (nullable text)
- price_amount (nullable decimal)
- currency (default: EGP)
- created_at / updated_at

Document
- id (uuid)
- request_id (FK → Request)
- file_url (S3 path)
- ocr_text (nullable, raw AI extraction)
- ocr_status (enum: pending, processing, success, failed)
- created_at

ScheduleSlot
- id (uuid)
- request_id (FK → Request)
- operation_date
- operation_time
- confirmed_by_coordinator (boolean)
- created_at

Payment
- id (uuid)
- request_id (FK → Request)
- method (enum: instapay, bank_transfer)
- amount
- status (enum: pending, confirmed, failed)
- proof_file_url (nullable, for bank transfer)
- created_at

Feedback
- id (uuid)
- request_id (FK → Request)
- rating (1–5)
- comment (nullable text)
- created_at

Notification
- id (uuid)
- doctor_id (FK → Doctor)
- request_id (nullable FK → Request)
- title
- body
- read (boolean)
- created_at
```

**Relationships:** One `Doctor` → many `Requests`. One `Request` → one `Document`, one `ScheduleSlot`, one `Payment`, one `Feedback` (all optional/nullable until that stage is reached). This lets you query a doctor's full request history and current status with a single joined query for the Home screen.

---

## 10. Integration

### Frontend ↔ Backend
- The React Native app communicates over **HTTPS REST**, using an `axios` instance with a base URL per environment (dev/staging/prod) and an interceptor that automatically attaches the JWT access token and refreshes it on expiry.
- Every screen transition in the linear request flow (3–11) corresponds to a specific REST endpoint call, so the mobile app is a fairly "thin" client — almost all business logic (pricing rules, scheduling availability, payment verification) lives server-side, which is safer for a healthcare/financial product.

### Authentication
- **Phone + OTP sign-up:** app sends phone number → backend triggers SMS OTP via Twilio Verify (or a local Egyptian SMS provider) → doctor enters code → backend issues JWT pair.
- **Session handling:** access token (short-lived, ~15 min) + refresh token (long-lived, ~30 days, stored securely via `expo-secure-store` / iOS Keychain / Android Keystore).

### Key APIs (example set)
```
POST   /api/v1/auth/register
POST   /api/v1/auth/verify-otp
POST   /api/v1/auth/login
POST   /api/v1/auth/refresh

POST   /api/v1/requests
GET    /api/v1/requests
GET    /api/v1/requests/:id
POST   /api/v1/requests/:id/document
POST   /api/v1/requests/:id/accept
POST   /api/v1/requests/:id/reject
POST   /api/v1/requests/:id/schedule
POST   /api/v1/requests/:id/payment
POST   /api/v1/requests/:id/feedback

GET    /api/v1/notifications
```

### Third-Party Services
| Purpose | Suggested Service |
|---|---|
| SMS OTP verification | Twilio Verify or a local Egyptian SMS gateway |
| Document OCR / AI extraction | Google Cloud Vision, AWS Textract, or a Claude vision-based extraction service |
| File storage | AWS S3 / DigitalOcean Spaces |
| Push notifications | Firebase Cloud Messaging |
| Payments — InstaPay | InstaPay merchant integration (via a licensed Egyptian payment aggregator, e.g. Fawry or Paymob, which support InstaPay rails) |
| Payments — Bank transfer | Manual reconciliation flow: doctor uploads proof → hospital finance team confirms via internal admin panel |
| Crash/analytics monitoring | Sentry (errors) + a lightweight analytics tool (e.g., Amplitude or Firebase Analytics) |

### How it connects to the existing Andalusia ecosystem
Since this app serves affiliated doctors of the same Andalusia Hospitals Group that runs the HMIS/reporting system and the public andalusiaegypt.com site, the cleanest integration path is:
- Reuse the **same Doctor identity** where possible (single sign-on against an existing staff/affiliate directory) instead of creating a second, disconnected user database.
- Have the **pricing, scheduling, and payment confirmation steps** write into (or be triggered by) the existing internal hospital admin/reporting system, rather than duplicating that logic in the new app's backend — the mobile app becomes a doctor-facing "front door" into workflows the hospital staff already manage internally.

---

## Build Order (Recommended, for a Small Team)

1. **Week 1–2:** Auth (phone + OTP), Home screen skeleton, design system (colors/typography/components) in Figma.
2. **Week 3–4:** New Request → Document Upload → basic OCR integration (can start with a stubbed/mock OCR response).
3. **Week 5:** Procedure Details → Pricing waiting/result (backend admin can manually set price at first, before automating).
4. **Week 6:** Scheduling + Coordinator Confirmation.
5. **Week 7:** Payment (start with Bank Transfer manual-proof flow; add InstaPay integration once a payment aggregator contract is in place).
6. **Week 8:** Completion + Rating/Feedback, push notifications end-to-end, polish + bilingual QA (EN/AR + RTL), then internal beta with 5–10 real affiliated doctors before public release.

---

*This plan is intentionally scoped to a Doctor-only MVP, matching your note that "all actions are initiated by the doctor" with "no visibility for other roles." Hospital-side staff (pricing, coordination, finance) are assumed to continue using the existing internal admin/HMIS system, with this app writing into that same backend data layer rather than a parallel one.*
