# LAX Commit Coach - AI System Documentation

**Version:** 2.0  
**Effective Date:** November 24, 2025  
**Last Updated:** November 24, 2025  
**Document Owner:** Rob Parker, Founder & CEO  
**Status:** Active - All Systems Documented

---

## 1. Overview

### 1.1 Purpose

This document provides comprehensive documentation of all AI systems deployed within LAX Commit Coach, including their capabilities, limitations, data usage, and human oversight mechanisms.

### 1.2 Product Context

**LAX Commit Coach** is an AI-powered recruiting platform for **men's high school lacrosse players** seeking men's college lacrosse programs. The platform helps student-athletes navigate the recruiting process through intelligent recommendations, communication tracking, and personalized guidance.

**Target Users:**
- Men's high school lacrosse players (Classes 2025-2030)
- Parents/guardians of student-athletes
- Club coaches and recruiting coordinators

---

## 2. AI System Inventory

### 2.1 System Summary

| ID | System Name | AI Provider | Status | Risk Level |
|----|-------------|-------------|--------|------------|
| LAX-AI-001 | Commit Coach Chatbot | Google Gemini | Production | Medium |
| LAX-AI-002 | College Recommendation Algorithm | Custom Logic | Production | Medium |
| LAX-AI-003 | Email Classification System | Google Gemini | Production | Low |
| LAX-AI-004 | Recruiting Health Score | Custom Logic | Production | Low |

---

## 3. System Details

### 3.1 LAX-AI-001: Commit Coach Chatbot

**Purpose:** Provide 24/7 conversational recruiting guidance to student-athletes.

**Technology:**
- Model: Google Gemini (via Lovable AI Gateway)
- Interface: Floating chat button accessible from all pages
- Context: User profile, saved colleges, communication history, activities

**Capabilities:**
- Answer recruiting strategy questions
- Analyze prospect day emails and coach communications
- Provide personalized advice based on user profile
- Log communications and complete tasks via conversation
- Explain college fit scores and recommendations

**Limitations:**
- Cannot make commitments on behalf of users
- Cannot contact coaches directly
- Cannot guarantee recruiting outcomes
- May occasionally provide imperfect advice
- Knowledge based on training data (not real-time)

**Human Oversight:**
- Users can ignore or override any chatbot advice
- All actions require user confirmation
- Feedback system allows rating responses ✅
- Admin dashboard for feedback review ✅
- Kill switch for immediate disable ✅

**Data Inputs:**
- User's question/message
- User profile (academic, athletic, preferences)
- Saved colleges and evaluations
- Communication history
- Recent activities

**Data Outputs:**
- Conversational response (text)
- Optional: action execution (log communication, complete task)

---

### 3.2 LAX-AI-002: College Recommendation Algorithm

**Purpose:** Match students with appropriate college lacrosse programs based on their profile and preferences.

**Technology:**
- Custom scoring algorithm
- Database of 390+ NCAA men's lacrosse programs
- 12-factor weighted scoring system

**Capabilities:**
- Calculate fit scores for all colleges
- Rank recommendations by fit
- Filter by division, region, size, setting
- Explain scoring breakdown
- Update dynamically as user updates preferences

**Limitations:**
- Scores are estimates, not guarantees
- Cannot predict coach interest or admission decisions
- Limited to data in college database
- Does not account for factors not in user profile

**Human Oversight:**
- Users set their own preference weights
- Users can override any recommendation
- Fit scores are explanations, not mandates
- Algorithm validation ensures quality ✅
- Admin controls for system disable ✅

**Data Inputs:**
- User academic profile (GPA, test scores)
- User athletic profile (position, stats)
- User preferences (12 importance weights)
- User categorical preferences (division, region, size, setting)
- College database attributes

**Data Outputs:**
- Ranked list of colleges with fit scores
- Score breakdown by factor
- Tier classifications (Reach, Target, Safety)

**Privacy-by-Design:**
The algorithm does NOT receive or process:
- Gender (product scoped to men's lacrosse)
- Race or ethnicity
- Household income
- Disability status

The algorithm CANNOT discriminate on these factors because it has no access to this data.

---

### 3.3 LAX-AI-003: Email Classification System

**Purpose:** Analyze forwarded recruiting emails to identify college, coach, and interest indicators.

**Technology:**
- Google Gemini for content analysis
- MIME parsing for email extraction
- Pattern matching for coach identification

**Capabilities:**
- Identify college(s) mentioned in emails
- Extract coach information (name, role, email)
- Classify interest level (High, Mixed, Marketing)
- Detect personalization indicators
- Support multi-college emails

**Limitations:**
- Accuracy depends on email clarity
- May not detect all implicit signals
- Cannot verify coach authenticity
- Confidence varies by email type

**Human Oversight:**
- User reviews all classifications before saving
- Confidence scores indicate certainty level ✅
- User can edit or override any detection
- Toggle to save or ignore coach contacts
- Admin incident reporting for errors ✅

**Data Inputs:**
- Forwarded email content (raw or parsed)
- User's college list for context

**Data Outputs:**
- Detected college(s)
- Detected coach information
- Interest classification
- Confidence score
- Suggested actions

---

### 3.4 LAX-AI-004: Recruiting Health Score

**Purpose:** Provide a holistic measure of recruiting progress and momentum.

**Technology:**
- Custom algorithm combining multiple factors
- Weighted scoring on 0-100 scale
- Trend analysis over time

**Capabilities:**
- Calculate overall health score
- Break down by component
- Track trends over time
- Identify areas needing attention
- Provide actionable recommendations

**Limitations:**
- Aggregate measure, not predictive of outcomes
- Based on platform activity only
- Does not measure external recruiting factors
- Simplified model of complex process

**Human Oversight:**
- Score is informational only
- Users decide how to act on insights
- Components are transparent
- Admin controls for system disable ✅

**Data Inputs:**
- Communication frequency and recency
- Number of colleges saved and researched
- Task completion rate
- Platform engagement metrics
- Pipeline stage distribution

**Data Outputs:**
- Overall score (0-100)
- Component scores
- Trend direction
- Improvement suggestions

---

## 4. Transparency Features ✅ IMPLEMENTED

### 4.1 AI Disclosure Modal

**Implementation:** November 24, 2025

When users first access the dashboard, they see a one-time disclosure modal explaining:
- Which features are AI-powered
- What the AI can and cannot do
- How to provide feedback
- How to report issues

Users must acknowledge before proceeding.

### 4.2 AI Badges

**Implementation:** November 24, 2025

Visual indicators appear throughout the application identifying AI-powered features:
- Chatbot interface
- College recommendations
- Email analysis results
- Health score display
- Fit scoring results

Badge includes tooltip explaining AI involvement.

### 4.3 Explainability Features

**Fit Score Breakdown:**
Users can see how each of the 12 factors contributes to a college's fit score.

**Chatbot Reasoning:**
Chatbot explains its recommendations with context from user profile.

**Email Classification Confidence:**
System indicates high/medium/low confidence on detections.

---

## 5. Feedback Mechanisms ✅ IMPLEMENTED

### 5.1 Response Rating

**Implementation:** November 24, 2025

Every chatbot response includes thumbs up/down buttons:
- **Thumbs Up:** Positive feedback recorded
- **Thumbs Down:** Prompts for reason selection
  - Inaccurate information
  - Not relevant to my question
  - Too generic
  - Inappropriate content
  - Other

### 5.2 Incident Reporting

**Implementation:** November 24, 2025

Users can report AI issues via dedicated button:
- Incident type selection
- Affected feature identification
- Description text field
- Automatic context capture (URL, timestamp)

### 5.3 Admin Review Dashboards

**AI Feedback Dashboard (/admin/ai-feedback):**
- View all feedback received
- Filter by rating type, date, feature
- Analyze satisfaction trends
- Export data for analysis

**AI Incidents Dashboard (/admin/ai-incidents):**
- View reported incidents
- Manage incident status (New, Reviewing, Resolved)
- Track resolution notes
- Prioritize by severity

---

## 6. Safety Controls ✅ IMPLEMENTED

### 6.1 Emergency Kill Switch

**Implementation:** November 24, 2025

**Location:** /admin/ai-controls

**Capabilities:**
- "Disable All AI" button requires typing confirmation
- Immediately disables all AI features
- Application continues functioning with AI disabled
- Clear visual indication of disabled state
- One-click restore when ready

### 6.2 Individual Feature Toggles

Each AI system can be independently enabled/disabled:
- [ ] Chatbot
- [ ] Recommendations
- [ ] Email Classification
- [ ] Health Score

### 6.3 Graceful Degradation

When AI features are disabled:
- Chatbot shows "temporarily unavailable" message
- Recommendations show static college list
- Email review allows manual entry only
- Health score hidden or shows cached value

---

## 7. Data Handling

### 7.1 Data Collection Principles

**Minimum Necessary:** Only collect data required for functionality.

**Purpose Limitation:** Data used only for stated purposes.

**User Control:** Users can view, export, and delete their data.

### 7.2 Data Not Collected

LAX Commit Coach intentionally excludes:
| Data Type | Reason Not Collected |
|-----------|---------------------|
| Gender | Product scoped to men's lacrosse |
| Race/Ethnicity | Not relevant to recruiting match |
| Household Income | Not relevant to recruiting match |
| Disability Status | Not relevant to recruiting match |

### 7.3 AI Data Processing

**Chatbot:**
- Messages sent to Google Gemini for processing
- Responses generated based on context provided
- Conversation history retained for continuity
- User can delete conversation history

**Recommendations:**
- All processing done locally/server-side
- No external AI calls for recommendations
- User profile data not shared externally

**Email Classification:**
- Email content sent to Google Gemini for analysis
- Processed content not retained by AI provider
- User controls what emails to forward

### 7.4 Data Retention

| Data Type | Retention Period |
|-----------|------------------|
| Chat Messages | Until user deletes |
| Feedback Ratings | Indefinite (anonymized) |
| Incident Reports | 2 years |
| Validation Results | Indefinite |

---

## 8. Quality Assurance

### 8.1 Algorithm Validation ✅ IMPLEMENTED

**Testing Infrastructure:**
- 100+ validation profiles covering all dimensions
- Automated test execution calling real edge function
- Results analysis dashboard
- Exportable validation reports

**Test Dimensions:**
- GPA Range (4 levels)
- Test Score Range (4 levels)
- Position (6 positions)
- Geographic Region (5 regions)
- Graduation Year (4 years)

**Latest Results (November 24, 2025):**
| Metric | Result |
|--------|--------|
| Profiles Tested | 100 |
| Zero-Result Profiles | 0 (full coverage) |
| Avg Recommendations/Profile | 10 |
| Overall Avg Match Score | 89.44 |
| Match Score Range | 73.6 - 95.0 |

**Validation Findings:**
- Algorithm differentiates by qualifications with 21+ point score range
- Higher GPA + Athletic Rating → Higher match scores (up to 95)
- Lower credentials → Lower but still viable scores (73-85)
- All profile combinations receive relevant recommendations

### 8.2 Ongoing Monitoring

- Weekly feedback review
- Monthly validation runs
- Quarterly comprehensive testing
- Incident-triggered investigations

---

## 9. Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | Nov 2025 | Initial documentation |
| 2.0 | Nov 24, 2025 | Added implemented features, validation results |

---

## 10. Contact Information

**AI System Questions:**
- Email: help@laxcommitcoach.com

**Incident Reporting:**
- In-app: Report AI Issue button
- Email: help@laxcommitcoach.com

**Data Requests:**
- Email: privacy@laxcommitcoach.com

---

*This document is part of the LAX Commit Coach AI Governance Framework.*
