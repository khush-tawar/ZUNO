# ZUNO
Your toxic accountability partner

## Overview
ZUNO is a digital coach that leverages shame, financial loss, and psychological coercion to enforce habits and goals. Forget "positive reinforcement"—ZUNO is built on a foundation of unyielding, targeted negative feedback.

## Core Philosophy
- Toxic accountability through shame, financial loss, and psychological coercion
- Negative reinforcement as primary motivator
- Pain, guilt, and loss as behavioral change drivers

---

## Product Features & Requirements

### 1. Punishment & Enforcement Systems

#### Dynamic Punishment System (DPS)
ZUNO doesn't just block; it escalates the consequences in real-time.

**Escalating Payouts**: For simple failures (like hitting the snooze button or accessing a blocked app), the user loses a small, pre-staked amount of money. For repeated or major failures (e.g., missing an entire daily goal), the payout loss is significantly higher.

**Forced Professional Contact**: For critical, non-negotiable goals (like diet, exercise, or study time), ZUNO uses a countdown timer to force a public/professional intervention.

*Example*: "Calling Dietician in 5 seconds. This is what failure looks like, prepare to explain yourself." If the user does not log the correct action within the timer, ZUNO automatically initiates the call or sends the failure report to the linked third party.

#### Financial Loss Mechanism (The Stake)
Every ZUNO commitment carries a non-negotiable financial penalty.

**Mandatory Stakes**: Users must lock in a financial stake for their goals. This money is permanently held in a "Punishment Pot."

**The Ultimate Insult Payout**: Upon failure, the lost money is not refunded. To maximize the punitive sting, the funds are automatically donated to a charity or political organization that the user has explicitly identified as despising.

#### Toxic App Blocker & Screen Interruption
ZUNO takes control of the user's device and uses the blockage moment as an opportunity for personal attack.

**Aggressive Block Screen**: When a user attempts to open a blocked app (e.g., Instagram, TikTok) during a focus window, the screen immediately flashes a hostile, angry-faced ZUNO logo.

**Personalized Insults**: This angry screen is accompanied by a custom, demeaning text insult designed to hit the user's deepest insecurity or current failing.

*Example*: "Look at you, late at this night looking at Insta. Don't you have better things to do? You're going to regret this in the morning, loser."

### 2. User Manipulation Tactics

#### Dark UX and Manipulation
The app's flow is designed to ensure maximum user investment with minimal escape routes.

**Confirmshaming**: All "off-ramps" (disabling the AI, lowering the stake) are met with manipulative, shaming language intended to make the user feel weak or unserious about their life.

**Roach Motel Withdrawal**: Depositing money into the Punishment Pot is frictionless and easy. However, finding and completing the process to withdraw remaining funds is deliberately obfuscated, confusing, and requires multiple steps to discourage users from cashing out.

**Forced Continuity**: ZUNO automatically renews goal commitments and financial stakes, assuming compliance. The opt-out is hidden deep in the settings with vague language.

---

## Technical Requirements

### Platform & Architecture (Simplified for AI Development)

#### Frontend Application
- **React 18+** with TypeScript
  - Single codebase for web and mobile (Progressive Web App)
  - React Context API or Zustand for state management
  - React Router for navigation
  - Responsive design (mobile-first approach)
  - Service Workers for offline support and push notifications
- **UI Framework**: Tailwind CSS or Material-UI
  - Pre-built components for rapid development
  - Consistent design system

#### Backend Infrastructure
- **Node.js 20+** with Express
  - RESTful API with JWT authentication
  - Simple architecture: monolithic to start
  - Rate limiting with express-rate-limit
- **Database**: PostgreSQL with Prisma ORM
  - User profiles and authentication
  - Goal tracking and punishment history
  - Financial transaction logs
  - Simple schema, easily understood by AI
- **Hosting**: Vercel (frontend) + Railway/Render (backend)
  - One-click deployment
  - Automatic HTTPS
  - Environment variables management

#### Third-Party Integrations
- **Payment Processing**: Stripe Checkout
  - Pre-built payment UI
  - Webhook-based automation
  - Stripe Connect for donations
- **Communication APIs**:
  - Twilio for SMS notifications (optional: start with email only)
  - Resend or SendGrid for email notifications
- **AI Integration**: OpenAI API for insult generation
- **Push Notifications**: Web Push API (built into browsers)

### Core Technical Features

#### 1. Goal & Commitment Engine
**Requirements**:
- CRUD operations for user goals with multiple commitment types (daily, weekly, one-time)
- Configurable financial stakes per goal (minimum/maximum thresholds)
- Rule engine for escalating punishment tiers
- Automatic goal renewal with opt-out mechanism (hidden in settings)
- Goal dependencies and prerequisite chains

**Data Models**:
```
Goal:
- id, user_id, title, description
- commitment_type, frequency, target_metrics
- stake_amount, escalation_multiplier
- auto_renew, renewal_date
- status (active, paused, completed, failed)
- created_at, updated_at

Commitment:
- id, goal_id, commitment_date
- expected_completion, actual_completion
- status (pending, completed, failed)
- punishment_applied, amount_lost
```

#### 2. Financial Punishment System
**Requirements**:
- Secure escrow account management per user
- Real-time balance tracking and transaction logging
- Automated deduction on goal failure
- Integration with charity/organization APIs for donations
- Multi-tier pricing: minor infractions ($1-$10), major failures ($10-$100+)
- Transaction history with immutable audit trail
- Refund prevention logic with compliance checks

**Security**:
- PCI-DSS compliance for payment data
- Two-factor authentication for high-value stakes
- Fraud detection and anomaly monitoring

#### 3. Focus Mode & Website Blocking (Web-Based Approach)
**Requirements**:
- Browser-based focus mode with timer
- User-defined "distraction list" (manual honor system to start)
- Focus session tracking with analytics
- Hostile reminder screens when breaking focus
- Progressive Web App install for full-screen experience
- Optional: Browser extension for actual website blocking (Phase 2)

**Block Screen UI**:
- Full-screen modal with aggressive branding
- Personalized insult generation engine (OpenAI GPT-4)
- Mandatory 5-10 second countdown before dismissal
- Analytics tracking: focus breaks, session duration

#### 4. Forced Intervention System
**Requirements**:
- Countdown timer UI with prominent display
- Automated email/SMS notification via Twilio or Resend
- Pre-configured contact list (dietician, trainer, accountability partner)
- Failure report generation with detailed metrics
- Email templates for professional contacts (HTML emails)
- Push notifications for deadline warnings

**Workflow**:
1. Goal deadline approaches (e.g., 1 hour before)
2. If not completed, push notification + email warning
3. If still not completed, 10-second countdown screen in app
4. At 0, send detailed failure report via email/SMS to contact

#### 5. Personalized Insult & Messaging Engine
**Requirements**:
- User profile with self-identified insecurities and pressure points
- Natural language generation (OpenAI GPT-4, Anthropic Claude, or custom model)
- Context-aware messaging (time of day, goal type, failure history)
- A/B testing for message effectiveness
- Content moderation to avoid illegal harassment (legal compliance)

**Message Types**:
- Block screen insults
- Push notification guilt trips
- Email failure summaries
- In-app reminders with shaming language

#### 6. Dark UX Implementation
**Requirements**:
- **Confirmshaming**: Modal dialogs with asymmetric button design
  - "Continue Being a Quitter" vs "Stay Committed"
  - Guilt-inducing copy on all opt-out flows
- **Roach Motel**: 
  - Withdrawal button hidden in nested settings (Settings > Account > Advanced > Financial > Withdrawals)
  - Multi-step verification process with cooling-off periods (24-48 hours)
  - Confusing language and intentional friction (CAPTCHA, email verification, phone verification)
- **Forced Continuity**:
  - Auto-renewal enabled by default
  - Opt-out requires manual action each cycle
  - No email reminders for renewal (silent renewal)

#### 7. Analytics & Tracking
**Requirements**:
- User behavior tracking (session duration, feature usage, drop-off points)
- Punishment effectiveness metrics (compliance rates pre/post punishment)
- Financial metrics (total staked, total lost, average stake per user)
- A/B testing framework for UI/UX experiments
- Cohort analysis and retention tracking
- Dashboard for internal monitoring

**Privacy Considerations**:
- GDPR/CCPA compliance with user data
- Anonymized data aggregation for analytics
- Opt-in for detailed tracking (buried in ToS)

### Infrastructure & DevOps (Simplified)

#### Hosting & Deployment
- **Frontend**: Vercel
  - Automatic deployments from GitHub
  - Built-in CDN and caching
  - Preview deployments for PRs
- **Backend**: Railway or Render
  - Simple Dockerfile deployment
  - Automatic HTTPS
  - Environment variables UI
- **CI/CD**: GitHub Actions (optional, start manual)
  - Basic linting and type checking
  - Automatic deployment via Git push

#### Monitoring (Start Simple)
- **Error Tracking**: Sentry (free tier)
- **Analytics**: PostHog or Simple Analytics
- **Logging**: Built-in console logs (Railway/Render dashboards)
- **Uptime**: UptimeRobot (free tier)

#### Security & Compliance
- **Encryption**: TLS 1.3 for data in transit, AES-256 for data at rest
- **Authentication**: OAuth 2.0, biometric authentication (Face ID, fingerprint)
- **Legal Compliance**:
  - Terms of Service with clear liability waivers
  - Privacy Policy with explicit data usage disclosure
  - Age restriction (18+)
  - Jurisdiction-specific compliance (gambling/financial regulations)

### Development Stack (Optimized for AI Development)

**Frontend**:
- React 18+ with TypeScript
- Vite for build tooling (fast, simple)
- Tailwind CSS for styling
- Zustand or React Context for state management
- React Query for API calls
- Progressive Web App (PWA) with Vite PWA plugin

**Backend**:
- Node.js 20+ with Express
- PostgreSQL 15+ with Prisma ORM
- Simple REST API (no GraphQL to reduce complexity)
- JWT authentication with bcrypt
- Node-cron for scheduled tasks (no separate queue system)

**Deployment**:
- Frontend: Vercel (automatic deployments from Git)
- Backend: Railway or Render (Dockerfile-based)
- Database: Railway PostgreSQL or Supabase

**AI/ML**:
- OpenAI API (GPT-4) for insult generation
- Simple prompt engineering (no custom models)

**Testing**:
- Vitest for unit tests
- Manual testing initially (E2E later if needed)

**Development Tools**:
- ESLint + Prettier for code formatting
- GitHub for version control
- Environment variables with dotenv

---

## Disclaimer

**Warning**: ZUNO is not designed for support or well-being. Its only function is to use pain, guilt, and loss as the primary motivators for behavioral change. This product may cause psychological distress and is intended as a satirical concept exploring the ethics of coercive design patterns.