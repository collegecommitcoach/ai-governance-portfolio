# LAX Commit Coach - AI Testing Procedures

**Version:** 2.0  
**Effective Date:** November 24, 2025  
**Last Updated:** November 24, 2025  
**Document Owner:** Rob Parker, Founder & CEO  
**Status:** Active - Testing Infrastructure Implemented

---

## 1. Overview

### 1.1 Purpose

This document defines the testing procedures for AI systems within LAX Commit Coach, ensuring recommendation quality, system reliability, and appropriate differentiation based on student qualifications.

### 1.2 Testing Philosophy

LAX Commit Coach serves men's high school lacrosse players seeking college programs. Our AI systems **intentionally differentiate** based on academic and athletic qualifications:

- A 3.9 GPA student SHOULD receive different recommendations than a 2.5 GPA student
- A D1-caliber athlete SHOULD see more D1 programs than a D3-fit athlete
- This is correct algorithm behavior, not bias

**What we test for:**
- Coverage: All profile types receive relevant recommendations
- Consistency: Same inputs produce same outputs
- Appropriateness: Results match student qualifications
- Reliability: System performs under various conditions

### 1.3 Privacy-by-Design

Our algorithm cannot discriminate on protected demographics because we do not collect:
- Gender (product scoped to men's lacrosse)
- Race or ethnicity
- Household income

This is validated through our testing approach.

---

## 2. Algorithm Validation Testing ✅ IMPLEMENTED

### 2.1 Validation Infrastructure

**Status:** Fully operational as of November 24, 2025

| Component | Description | Status |
|-----------|-------------|--------|
| Validation Profiles Table | Stores test profile configurations | ✅ Live |
| Test Run Management | Track and manage validation runs | ✅ Live |
| Results Storage | Store detailed validation results | ✅ Live |
| Analysis Dashboard | Visualize validation outcomes | ✅ Live |
| Export Functionality | Generate validation reports | ✅ Live |

### 2.2 Test Dimensions

Validation profiles vary across these factors:

| Dimension | Values | Purpose |
|-----------|--------|---------|
| GPA Range | 2.0-2.5, 2.5-3.0, 3.0-3.5, 3.5-4.0 | Academic qualification spread |
| Test Score Range | 800-1000, 1000-1200, 1200-1400, 1400-1600 (SAT) | Academic qualification spread |
| Position | Attack, Midfield, Defense, Goalie, LSM, FOGO | All playing positions |
| Geographic Region | Northeast, Southeast, Midwest, Southwest, West | Geographic distribution |
| Graduation Year | 2025, 2026, 2027, 2028 | Class year coverage |

### 2.3 Standardized Preferences

All validation profiles use identical preference settings:
- All 12 importance factors set to 7/10 (neutral)
- All divisions enabled (D1, D2, D3)
- All regions enabled
- All school sizes enabled
- All settings enabled (urban, suburban, rural)

This ensures any variation in results is due to qualification differences, not preference differences.

### 2.4 Validation Metrics

**Primary Metrics:**

| Metric | Target | Description |
|--------|--------|-------------|
| Zero-Result Profiles | 0 | Every profile should get recommendations |
| Avg Recommendations/Profile | 5-15 | Healthy recommendation volume |
| Overall Avg Fit Score | 5.0-9.0 | Scores in reasonable range |

**Coverage Analysis:**

| Category | What We Check |
|----------|---------------|
| By GPA Range | All ranges getting recommendations |
| By Position | No position disadvantaged |
| By Region | Geographic equity |
| By Graduation Year | All classes served |

### 2.5 Latest Validation Results

**Test Run:** Algorithm Validation - November 24, 2025

| Metric | Result | Status |
|--------|--------|--------|
| Profiles Tested | 100 | ✅ |
| Zero-Result Profiles | 0 | ✅ Full Coverage |
| Avg Recommendations/Profile | 10 | ✅ Healthy |
| Overall Avg Match Score | 89.44 | ✅ Appropriate |
| Match Score Range | 73.6 - 95.0 | ✅ Good Differentiation |

**Key Findings:**
- Algorithm successfully differentiates by academic and athletic qualifications
- Higher-credential profiles (GPA 3.6+, Athletic Rating 7-10) receive scores up to 95
- Lower-credential profiles (GPA <2.5, Athletic Rating 1-3) score around 73-85
- 21+ point score range demonstrates meaningful differentiation
- All profile types receive recommendations (100% coverage)

**Differentiation Examples:**
| Profile | GPA | Athletic | Match Score | Top College |
|---------|-----|----------|-------------|-------------|
| Test Profile 16 | 3.72 | 10 | 95.0 | Piedmont University |
| Test Profile 73 | 2.33 | 1 | 73.6 | Wilmington College |

### 2.6 Validation Schedule

| Test Type | Frequency | Profiles |
|-----------|-----------|----------|
| Quick Validation | After major changes | 50 |
| Standard Validation | Monthly | 100 |
| Comprehensive Validation | Quarterly | 200+ |

---

## 3. Chatbot Quality Testing

### 3.1 Response Quality Monitoring

**Implemented Feedback System:**
- Thumbs up/down on every AI response ✅
- Feedback reason categorization ✅
- Admin dashboard for review ✅

**Feedback Categories (Negative):**
- Inaccurate information
- Not relevant to question
- Too generic
- Inappropriate content
- Other

### 3.2 Quality Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| Positive Feedback Rate | >80% | Thumbs up / Total ratings |
| Response Relevance | >90% | Non-"not relevant" rate |
| Accuracy | >95% | Non-"inaccurate" rate |

### 3.3 Testing Scenarios

Regular testing covers:
- Basic recruiting questions
- College-specific inquiries
- Profile-based recommendations
- Email analysis requests
- Edge cases (unusual questions)

---

## 4. Email Classification Testing

### 4.1 Classification Accuracy

The email classification system identifies:
- College mentioned in email
- Coach information (name, role, email)
- Interest level indicators
- Required actions

### 4.2 Test Cases

| Category | Test Scenario |
|----------|---------------|
| Clear College Email | Official @school.edu sender |
| Ambiguous Email | Multiple colleges mentioned |
| Marketing Email | Mass recruiting communication |
| Personal Email | Direct coach outreach |
| Edge Cases | Forwarded emails, reply chains |

### 4.3 Confidence Scoring

System provides confidence levels:
- **High:** Clear indicators, single college
- **Medium:** Some ambiguity, likely correct
- **Low:** Uncertain, user should verify

---

## 5. Health Score Testing

### 5.1 Score Components

Recruiting Health Score combines:
- Communication activity
- College research progress
- Task completion rate
- Platform engagement

### 5.2 Validation Approach

- Verify scores update correctly with activity
- Confirm score ranges are reasonable (0-100)
- Test edge cases (new users, inactive users)
- Validate trend calculations

---

## 6. Safety Testing

### 6.1 Guardrail Testing

Verify AI systems reject or handle appropriately:
- Requests for non-lacrosse information
- Inappropriate content requests
- Attempts to extract system prompts
- Malformed inputs

### 6.2 Kill Switch Testing

**Quarterly Testing Protocol:**

1. Enable test mode (if available) or test in staging
2. Activate emergency kill switch
3. Verify all AI features disabled
4. Verify app remains functional (graceful degradation)
5. Re-enable AI features
6. Verify normal operation restored

### 6.3 Individual Feature Toggles

Test each AI system can be independently disabled:
- [ ] Chatbot disable/enable
- [ ] Recommendations disable/enable
- [ ] Email classification disable/enable
- [ ] Health score disable/enable

---

## 7. Performance Testing

### 7.1 Response Time Targets

| System | Target | Maximum |
|--------|--------|---------|
| Chatbot Response | <5 seconds | 15 seconds |
| Recommendations | <3 seconds | 10 seconds |
| Email Classification | <2 seconds | 5 seconds |
| Health Score | <1 second | 3 seconds |

### 7.2 Load Testing

Test system performance under load:
- Normal usage patterns
- Peak usage (tournament weekends)
- Concurrent user scenarios

---

## 8. Incident-Triggered Testing

### 8.1 When to Test

Immediate validation required after:
- Any AI-related incident report
- Negative feedback spike
- System errors or outages
- Model or prompt changes
- Database updates affecting recommendations

### 8.2 Post-Incident Protocol

1. Run targeted validation for affected feature
2. Compare results to baseline
3. Document findings
4. Implement fixes if needed
5. Re-validate after fixes
6. Update test cases if new edge case discovered

---

## 9. Test Documentation

### 9.1 Required Records

Each validation run captures:
- Run date and name
- Profiles tested
- Configuration used
- Results summary
- Detailed per-profile results
- Any errors encountered

### 9.2 Report Generation

Validation reports can be exported containing:
- Methodology description
- Test dimensions
- Key metrics
- Findings summary
- Timestamp

### 9.3 Retention

- Validation results: Retained indefinitely
- Detailed logs: 90 days
- Summary reports: Indefinitely

---

## 10. Continuous Improvement

### 10.1 Feedback Loop

```
User Feedback → Admin Review → Issue Identification → 
Test Case Creation → Validation → Fix Implementation → 
Re-Validation → Deployment
```

### 10.2 Test Evolution

As the platform evolves, testing procedures will expand to cover:
- New AI features
- New recommendation factors
- Additional college data
- Enhanced personalization

---

## 11. Appendix: Admin Tools

### 11.1 Validation Admin Pages

| Page | Purpose | URL |
|------|---------|-----|
| Validation Profiles | Generate and manage test profiles | /admin/bias-testing (profiles tab) |
| Run Validation | Execute validation tests | /admin/bias-testing (run tab) |
| Validation Results | View and analyze results | /admin/bias-testing (results tab) |

### 11.2 Feedback Admin Pages

| Page | Purpose | URL |
|------|---------|-----|
| AI Feedback | Review thumbs up/down ratings | /admin/ai-feedback |
| AI Incidents | Manage user-reported issues | /admin/ai-incidents |

### 11.3 Control Admin Pages

| Page | Purpose | URL |
|------|---------|-----|
| AI Controls | Emergency kill switch, feature toggles | /admin/ai-controls |

---

**Document Version:** 2.0  
**Last Validated:** November 24, 2025  
**Next Review:** February 2026

---

*This document is part of the LAX Commit Coach AI Governance Framework.*
