# LAX Commit Coach - AI Governance

> **Note:** This repository contains documentation and implementation materials for LAX Commit Coach. The source code is maintained in a private repository as this is an active commercial product. For a live demonstration, visit [laxcommitcoach.com](https://laxcommitcoach.com)

---

## Rob Parker | AI Implementation, Governance & Compliance

I build AND govern AI systems for production environments. This portfolio demonstrates real-world implementation of the NIST AI Risk Management Framework (AI RMF) for a production-ready AI-powered SaaS platform.

I've built production AI systems and implemented comprehensive governance frameworks to ensure they're safe, fair, and transparent.

---

## AI Governance Implementation

### NIST AI RMF Compliance Documentation

| Document | Purpose | NIST Functions Addressed |
|----------|---------|--------------------------|
| [AI Risk Management Policy](./lax-commit-coach/AI_Risk_Management_Policy.md) | Governance framework, risk tolerances, accountability | GOVERN 1.2, 1.4, 4.1, 4.2 |
| [AI Testing & Assessment Procedures](./lax-commit-coach/AI_Testing_Procedures.md) | Bias testing, safety validation, TEVV methodology | MAP 2.3, MEASURE 1.1, 2.1, 2.6, 2.11 |
| [AI System Documentation](./lax-commit-coach/AI_System_Documentation.md) | Transparency, user disclosures, limitations | MAP 1.1, 2.2, MEASURE 2.8, 2.9 |
| [AI Incident Response Plan](./lax-commit-coach/AI_Incident_Response_Plan.md) | Incident classification, response procedures, recovery | MANAGE 2.3, 2.4, 4.1, 4.3 |
| [Implementation Roadmap](./lax-commit-coach/NIST_Implementation_Roadmap.md) | Technical specifications, development priorities | Full framework alignment |

### AI Governance Metrics

| Metric | Target | Status |
|--------|--------|--------|
| Algorithm score differentiation | 20+ points by qualifications | Achieved (21+ points) |
| Critical incident response time | <4 hours | Procedures Defined |
| User AI disclosure rate | 100% | Implemented |
| AI system documentation coverage | 100% | Complete |
| Profile coverage (zero-result rate) | 0% | Achieved |

---

## AI Systems Under Governance

This platform includes **5 production AI systems** that I designed, built, and now govern:

### 1. AI Recruiting Chatbot
**Risk Level:** Medium | **Status:** Production

- **Function:** Contextually-aware guidance based on user's communication history, preferences, and recruiting stage
- **Technology:** Google Gemini via Lovable AI Gateway
- **Governance Controls:**
  - User disclosure and consent mechanisms
  - Response safety filtering
  - NCAA compliance validation
  - Feedback collection (thumbs up/down)
  - Emergency disable capability
  - Pre-computed context system for consistency

### 2. College Recommendation Engine
**Risk Level:** Medium | **Status:** Production

- **Function:** Multi-factor matching algorithm (recruiting fit, academic profile, preferences)
- **Technology:** Custom 5-factor scoring algorithm + AI explanation generation
- **Governance Controls:**
  - Algorithm validation testing across 100+ profile combinations
  - 21+ point score differentiation by qualifications (73.6 - 95.0 range)
  - Explainability features ("Why this recommendation?")
  - Transparent scoring methodology documentation
  - Privacy-by-design: no demographic data (race, gender, income) collected
  - Interest override system for demonstrated school engagement

### 3. Automated Fit Calculation System (NEW)
**Risk Level:** Low-Medium | **Status:** Production

- **Function:** Calculates objective fit scores for saved colleges based on 5 factors
- **Technology:** PostgreSQL functions (`calculate_college_fit`, `calculate_college_fit_batch`)
- **Scoring Factors:**
  - Recruiting Fit (35%): User percentile vs. college recruiting ceiling
  - Academic Fit (30%): GPA/test scores vs. acceptance rate
  - Location Fit (15%): Region preference match
  - Size Fit (10%): School size preference match
  - Setting Fit (10%): Urban/suburban/rural preference match
- **Governance Controls:**
  - Signal-based interest overrides (phone calls, visits trump calculated fit)
  - Transparent breakdown shown to users
  - No financial fit scoring (avoids judging family financial situations)
  - Confidence indicators for inferred data

### 4. Email Classification System
**Risk Level:** Low-Medium | **Status:** Production

- **Function:** Interest level analysis (HIGH/MIXED/MARKETING) for recruiting emails
- **Technology:** MIME parsing + Gemini AI analysis
- **Governance Controls:**
  - Confidence scoring (high/medium/low)
  - Human review before action
  - Privacy-preserving processing
  - Accuracy monitoring

### 5. Pre-Computed Intelligence System (NEW)
**Risk Level:** Low | **Status:** Production

- **Function:** Generates intelligence briefings for chatbot context
- **Technology:** Edge function + Gemini AI analysis
- **Outputs:**
  - Recruiting snapshot (player status summary)
  - Pipeline intelligence (school categorization)
  - Communication insights (patterns, response rates)
  - Strategic priorities (urgent actions)
  - Fit reality assessment (interest-aware school categorization)
  - Recruiting level analysis (percentile validation)
- **Governance Controls:**
  - Signal-based percentile inference with confidence levels
  - Interest override detection
  - Graceful fallback for missing data
  - No automated actions (advisory only)
    
### Parent Access Security (February 2026)

Implemented centralized, time-bounded parent access controls for student data:

- **`is_active_parent_of()`** - Security definer function enforcing 90-day verification window
- **11 protected tables** including `user_ai_context` (AI-generated recruiting intelligence)
- **Auto-refresh mechanism** - verification extends on dashboard load, preventing lockout for active parents
- **Zero inline policy checks** - all parent access flows through centralized function for auditability

This ensures parents of minor users (14-18 year olds) have appropriate data access that automatically expires if the relationship becomes stale, protecting student privacy while enabling family coordination.
---

## Governance Framework Highlights

### Trustworthy AI Principles (NIST AI RMF Aligned)

| Principle | Implementation |
|-----------|----------------|
| **Valid & Reliable** | Accuracy testing, performance monitoring, error tracking |
| **Safe** | NCAA compliance validation, harmful content filtering, safety boundaries |
| **Secure & Resilient** | Prompt injection protection, API security, emergency kill switch |
| **Accountable & Transparent** | User disclosures, AI badges, decision explanations |
| **Explainable** | "Why this recommendation?" features, fit breakdown display, interest override reasons |
| **Privacy-Enhanced** | Data minimization, user control, consent mechanisms, no financial judgment |
| **Fair** | Privacy-by-design (no demographic data collected), algorithm validation testing |

### Risk Tolerance Framework

```
ZERO TOLERANCE:
├── AI providing harmful recruiting advice
├── Coverage gaps (profiles with zero recommendations)
├── Privacy breaches or data exposure
└── NCAA rule violations in guidance

MANAGED ACCEPTANCE:
├── Minor accuracy variations (<5% error rate)
├── Temporary service degradation
└── Non-critical feature issues

ACCEPTABLE:
├── Response time variations
├── Cosmetic inconsistencies
└── Minor UX issues
```

### Incident Response Structure

```
P0 (Critical) → Response <4 hours
├── Harmful AI advice
├── Security breach
├── Systematic bias detected
└── Privacy violation

P1 (High) → Response <24 hours
├── Significant accuracy issues
├── Moderate bias detected
└── Extended service outage

P2/P3 (Medium/Low) → Response <1 week
├── Minor issues
├── Enhancement requests
└── Documentation updates
```

---

## 🔧 Technical Architecture

### AI Integration Stack
- **AI Provider:** Google Gemini (via Lovable AI Gateway)
- **Backend:** Supabase (PostgreSQL with Row-Level Security)
- **Frontend:** React 18, TypeScript, Tailwind CSS
- **Architecture:** Serverless edge functions, real-time sync
- **Security:** JWT authentication, RLS policies, encrypted data

### Governance Infrastructure
- **Monitoring:** Real-time AI health dashboard
- **Feedback:** User rating system for AI responses
- **Reporting:** Incident reporting and tracking system
- **Controls:** Feature flags and emergency disable capability
- **Testing:** Automated bias testing pipeline

### Data Flow & Privacy
```
User Input → Validation → AI Processing → Safety Check → Response
                ↓                              ↓
         Audit Logging              Feedback Collection
                ↓                              ↓
         Incident Detection         Continuous Improvement
```

### Fit Calculation Architecture (NEW)
```
User Profile → calculate_college_fit() → Objective Score
     +                    ↓
Communications → Interest Override Detection → Final Fit Level
     +                    ↓
User Ratings → Combined Display → Transparent Breakdown
```

---

## Platform Metrics

| Metric | Value |
|--------|-------|
| **AI Systems Governed** | 5 production-ready systems |
| **College Database** | 390+ NCAA programs |
| **Validation Profiles Tested** | 100+ profile combinations |
| **Match Score Differentiation** | 21+ points (73.6 - 95.0 range) |
| **Target Incident Response** | <4 hours (critical) |
| **Documentation Coverage** | 100% of AI systems |
| **User Input Reduction** | 92% (24 inputs → 2 star ratings) |

### Latest Algorithm Validation (January 2026)

| Metric | Result |
|--------|--------|
| Profiles Tested | 100 |
| Zero-Result Profiles | 0 (100% coverage) |
| Overall Avg Match Score | 89.44 / 100 |
| Score Range | 73.6 - 95.0 |

**Finding:** Algorithm successfully differentiates by academic and athletic credentials. Higher-qualified profiles receive match scores up to 95, while lower-credential profiles score 73-85.

### Fit Calculation System Validation

| Metric | Result |
|--------|--------|
| Factors Calculated Automatically | 5 (100% of objective factors) |
| User Inputs Required | 2 (reduced from 24) |
| Interest Override Detection | Phone calls, campus visits, personalized emails |
| Financial Fit | Removed (avoids presumptuous judgment) |

---

## Platform Capabilities

### Simplified Evaluation System (NEW)
- **Before:** 12 factors × 2 inputs each = 24 user inputs required
- **After:** 2 star ratings (overall vibe, program feel)
- **Automated:** 5-factor objective fit calculated without user input
- **Transparent:** Full breakdown shown to users explaining each score
- **Interest-Aware:** Schools showing interest override calculated fit

### Engagement & Adoption Analytics
- Profile completion tracking for activation metrics
- Activity logging with streak tracking
- Gamification system (badges, levels, achievements)
- Progress milestones with behavioral reinforcement

### Relationship Intelligence
- Communication sentiment analysis
- Response time analytics
- Engagement trend identification
- Proactive at-risk detection
- **Interest override detection (coach calls, visit invites)**

### Visual Pipeline Management
- Drag-and-drop stage tracking
- Real-time progression analytics
- Automated follow-up reminders
- Journey mapping visualization
- **Fit badges on every college card**
- **Pipeline balance warnings**

### Multi-Stakeholder Access
- Role-based access control
- Parent portal with read-only access
- Configurable notification preferences
- Secure invitation system

---

## Professional Background

### Why I'm Uniquely Qualified for AI Governance

**Technical Implementation Experience:**
- Built 5 production AI systems from scratch
- Integrated Google Gemini AI for real-time guidance
- Designed multi-factor recommendation algorithms
- Implemented sentiment analysis and classification systems
- **Designed simplified evaluation system reducing user friction by 92%**

**Governance & Risk Management:**
- Implemented NIST AI RMF for production systems
- Created comprehensive bias testing methodology
- Designed incident response procedures
- Built transparency and accountability mechanisms
- **Implemented interest override system for demonstrated engagement**

**Enterprise Stakeholder Management:**
- 8 years Customer Success leadership at Dell Technologies
- Experience communicating complex topics to executives
- Track record of cross-functional program management
- Deep understanding of organizational change management

**Unique Perspective:**
> "I've sat in the founder's seat making AI product decisions, felt the tension between speed and safety, and systematically implemented governance to ensure our AI was trustworthy. I understand both the technical challenges and the business pressures—and how to balance them responsibly."

### Proactive Governance Philosophy

I built governance BEFORE scaling—not as a reactive cleanup after problems emerged. This demonstrates:
- Forward-thinking risk management
- Mature product development approach
- "Shift left" compliance philosophy
- Understanding that trust is built early, not retrofitted

---

## Seeking Opportunities In

- **AI Governance Manager** — Implementing AI risk management frameworks
- **Responsible AI Program Manager** — Driving organizational AI safety initiatives
- **AI Compliance Manager** — Ensuring regulatory alignment (EU AI Act, NIST)
- **AI Risk Manager** — Assessing and mitigating AI system risks
- **Trust & Safety Manager** — Building safe AI user experiences

---

## Contact

- **LinkedIn:** [linkedin.com/in/robrparker](https://www.linkedin.com/in/robrparker)
- **Email:** robrparker@gmail.com
- **Location:** Charlotte, NC (Remote preferred)
- **Live Demo:** [laxcommitcoach.com](https://laxcommitcoach.com)

---

## Repository Structure

```
ai-governance-portfolio/
├── README.md                          # This file
├── lax-commit-coach/
│   ├── AI_Risk_Management_Policy.md   # GOVERN function
│   ├── AI_Testing_Procedures.md       # MEASURE function
│   ├── AI_System_Documentation.md     # MAP function
│   ├── AI_Incident_Response_Plan.md   # MANAGE function
│   └── NIST_Implementation_Roadmap.md # Implementation guide
└── resources/
    ├── APPLICATION_OVERVIEW.md        # Full platform documentation
    └── COMMIT_COACH_AI_PROMPTS.md     # AI personality & prompts
```

---

*Built by Rob Parker — Founder, Broadlake Technologies*

*Last Updated: January 2026*
updated with simplified college fit system
