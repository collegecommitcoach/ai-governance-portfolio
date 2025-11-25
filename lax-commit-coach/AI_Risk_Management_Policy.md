# LAX Commit Coach - AI Risk Management Policy

**Version:** 2.0  
**Effective Date:** November 24, 2025  
**Last Updated:** November 24, 2025  
**Document Owner:** Rob Parker, Founder & CEO  
**Status:** Active - Features Implemented

---

## 1. Purpose and Scope

### 1.1 Purpose

This policy establishes the governance framework for artificial intelligence systems deployed within LAX Commit Coach, ensuring responsible development, deployment, and operation of AI features that serve men's high school lacrosse players navigating the college recruiting process.

### 1.2 Scope

This policy applies to all AI-powered features within LAX Commit Coach:

| System ID | System Name | Status |
|-----------|-------------|--------|
| LAX-AI-001 | Commit Coach Chatbot | Production |
| LAX-AI-002 | College Recommendation Algorithm | Production |
| LAX-AI-003 | Email Classification System | Production |
| LAX-AI-004 | Recruiting Health Score | Production |

### 1.3 Product Scope

LAX Commit Coach v1.0 serves **men's high school lacrosse players** seeking men's college lacrosse programs. A separate women's lacrosse version is planned as a distinct product with its own college database and sport-specific features.

---

## 2. Governance Structure

### 2.1 Roles and Responsibilities

**AI Risk Owner (Founder/CEO)**
- Ultimate accountability for AI risk management
- Approval authority for AI system changes
- Review and sign-off on incident response actions
- Quarterly review of AI governance effectiveness

**Development Team**
- Implementation of AI safety controls
- Monitoring system performance and errors
- First-line response to AI incidents
- Documentation of system changes

**External Advisors (As Needed)**
- Independent review of AI governance practices
- Specialized expertise for complex issues
- Audit support and compliance guidance

### 2.2 Review Cadence

| Review Type | Frequency | Responsible Party |
|-------------|-----------|-------------------|
| Incident Review | As needed | AI Risk Owner |
| Feedback Analysis | Weekly | Development Team |
| Validation Testing | Monthly | Development Team |
| Policy Review | Quarterly | AI Risk Owner |
| Comprehensive Audit | Annually | External + Internal |

---

## 3. AI Risk Tolerance Framework

### 3.1 Risk Categories

**Zero Tolerance (Immediate Action Required)**
- AI outputs that could endanger student safety
- Systematic discrimination in recommendations
- Privacy breaches exposing user data
- NCAA compliance violations in guidance

**Managed Acceptance (Monitor and Mitigate)**
- Occasional inaccurate recommendations
- Response latency issues
- Minor user experience friction
- Edge case handling gaps

**Acceptable Risk (Normal Operations)**
- Variance in recommendation fit scores
- User preference for human vs. AI guidance
- Feature adoption rate variations

### 3.2 Risk Response Matrix

| Risk Level | Response Time | Action Required |
|------------|---------------|-----------------|
| Critical | < 4 hours | Emergency kill switch, incident response |
| High | < 24 hours | Feature disable, root cause analysis |
| Medium | < 1 week | Investigation, remediation planning |
| Low | Next sprint | Backlog, scheduled improvement |

---

## 4. Trustworthy AI Principles

LAX Commit Coach AI systems adhere to these principles:

### 4.1 Valid and Reliable
- Algorithm validation testing across 100+ profile combinations
- Match scores range from 73.6 to 95.0 based on qualifications (21+ point differentiation)
- Consistent outputs for identical inputs
- Regular performance monitoring

### 4.2 Safe
- Emergency kill switch for all AI features ✅ **IMPLEMENTED**
- Guardrails preventing harmful outputs
- Human oversight for critical decisions

### 4.3 Secure and Resilient
- Rate limiting on AI endpoints
- Input validation and sanitization
- Graceful degradation when AI unavailable

### 4.4 Accountable and Transparent
- AI disclosure modal for all users ✅ **IMPLEMENTED**
- AI-powered badges on relevant features ✅ **IMPLEMENTED**
- Clear documentation of AI capabilities and limitations

### 4.5 Explainable and Interpretable
- "Why this recommendation?" explanations
- Fit score breakdowns by factor
- Chatbot reasoning visible to users

### 4.6 Privacy-Enhanced
- Minimum necessary data collection
- No demographic data collected (gender, race, income)
- User control over data sharing

### 4.7 Fair
- Algorithm cannot discriminate on factors it cannot see
- Appropriate differentiation based on qualifications (intentional)
- Coverage validation ensuring all profile types receive recommendations

---

## 5. Implemented Controls

### 5.1 Transparency Controls

| Control | Description | Status |
|---------|-------------|--------|
| AI Disclosure Modal | One-time acknowledgment explaining AI features | ✅ Implemented |
| AI Badges | Visual indicators on AI-powered features | ✅ Implemented |
| Capability Descriptions | Clear explanation of what AI can/cannot do | ✅ Implemented |

### 5.2 Feedback Controls

| Control | Description | Status |
|---------|-------------|--------|
| Thumbs Up/Down | Rating system on chatbot responses | ✅ Implemented |
| Feedback Reasons | Categorization of negative feedback | ✅ Implemented |
| Report AI Issue | User-initiated incident reporting | ✅ Implemented |

### 5.3 Monitoring Controls

| Control | Description | Status |
|---------|-------------|--------|
| Admin Feedback Dashboard | Review and analyze user feedback | ✅ Implemented |
| Admin Incident Dashboard | Track and manage reported issues | ✅ Implemented |
| Usage Tracking | Monitor AI feature usage patterns | ✅ Implemented |

### 5.4 Safety Controls

| Control | Description | Status |
|---------|-------------|--------|
| Emergency Kill Switch | Disable all AI features instantly | ✅ Implemented |
| Individual Feature Toggles | Enable/disable specific AI systems | ✅ Implemented |
| Graceful Degradation | App functions when AI disabled | ✅ Implemented |

### 5.5 Quality Assurance Controls

| Control | Description | Status |
|---------|-------------|--------|
| Algorithm Validation | Test recommendation quality across profiles | ✅ Implemented |
| Coverage Analysis | Ensure all profile types get results | ✅ Implemented |
| Validation Reporting | Exportable validation results | ✅ Implemented |

---

## 6. Privacy-by-Design

### 6.1 Data Not Collected

LAX Commit Coach intentionally does not collect:
- Gender (product serves men's lacrosse specifically)
- Race or ethnicity
- Household income
- Disability status

**Implication:** The recommendation algorithm cannot discriminate on these factors because it has no access to this information.

### 6.2 Data Collected and Used

The algorithm uses only recruiting-relevant factors:
- Academic profile (GPA, test scores)
- Athletic profile (position, measurements, stats)
- Preferences (division, region, school size, setting)
- Importance weights (12 factors rated by user)

### 6.3 User Data Rights

Users can:
- View all data collected about them
- Export their data
- Delete their account and all associated data
- Control parent portal access

---

## 7. Compliance Framework

### 7.1 NIST AI RMF Alignment

This policy implements the NIST AI Risk Management Framework:

| Function | Implementation |
|----------|----------------|
| GOVERN | This policy, roles, accountability structure |
| MAP | AI system documentation, risk identification |
| MEASURE | Validation testing, feedback collection, monitoring |
| MANAGE | Incident response, kill switch, remediation |

### 7.2 Domain-Specific Compliance

- **NCAA Guidelines:** AI outputs reviewed for compliance with recruiting rules
- **FERPA Considerations:** Student data protected appropriately
- **State Privacy Laws:** Architecture supports compliance requirements

---

## 8. Policy Maintenance

### 8.1 Review Schedule

- **Quarterly:** Review policy effectiveness, update as needed
- **Post-Incident:** Review and update after any significant AI incident
- **Annually:** Comprehensive review with external input

### 8.2 Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | Nov 2025 | Initial policy |
| 2.0 | Nov 24, 2025 | Updated with implemented features, validation results |

---

## 9. Approval

**Approved By:** Rob Parker, Founder & CEO  
**Date:** November 24, 2025  
**Next Review:** February 2026

---

*This document is part of the LAX Commit Coach AI Governance Framework.*
