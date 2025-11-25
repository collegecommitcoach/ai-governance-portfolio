# LAX Commit Coach - AI Incident Response Plan

**Version:** 2.0  
**Effective Date:** November 24, 2025  
**Last Updated:** November 24, 2025  
**Document Owner:** Rob Parker, Founder & CEO  
**Status:** Active - Response Infrastructure Implemented

---

## 1. Purpose

This plan establishes procedures for identifying, responding to, and resolving incidents related to AI systems within LAX Commit Coach. The goal is to minimize harm, restore service, and prevent recurrence.

---

## 2. Scope

This plan covers incidents involving:
- LAX-AI-001: Commit Coach Chatbot
- LAX-AI-002: College Recommendation Algorithm
- LAX-AI-003: Email Classification System
- LAX-AI-004: Recruiting Health Score

---

## 3. Incident Detection ✅ IMPLEMENTED

### 3.1 Detection Channels

| Channel | Description | Status |
|---------|-------------|--------|
| User Feedback (Thumbs Down) | Negative ratings on AI responses | ✅ Live |
| User Incident Reports | Dedicated "Report AI Issue" feature | ✅ Live |
| Admin Monitoring | Dashboards for feedback and incidents | ✅ Live |
| Error Logs | System-level error detection | ✅ Live |
| User Support | Email reports from users | ✅ Available |

### 3.2 Incident Report Form

Users can report issues via the "Report AI Issue" button with:
- **Incident Type:** Inaccuracy, Bias concern, Inappropriate content, Harmful output, Privacy concern, Technical error, Other
- **Affected Feature:** Chatbot, Recommendations, Email Analysis, Health Score, Other
- **Description:** Free-text explanation
- **Automatic Context:** Page URL, timestamp, user ID

### 3.3 Admin Dashboards

**AI Incidents Dashboard (/admin/ai-incidents):**
- View all reported incidents
- Filter by type, status, feature, date
- Manage incident lifecycle
- Track resolution

**AI Feedback Dashboard (/admin/ai-feedback):**
- Monitor satisfaction rates
- Identify feedback spikes
- Analyze common issues

---

## 4. Incident Classification

### 4.1 Severity Levels

| Level | Name | Description | Response Time |
|-------|------|-------------|---------------|
| P0 | Critical | Safety risk, data breach, complete system failure | < 4 hours |
| P1 | High | Significant user impact, systematic errors | < 24 hours |
| P2 | Medium | Noticeable issues, partial feature degradation | < 1 week |
| P3 | Low | Minor issues, edge cases | Next sprint |

### 4.2 Severity Examples

**P0 - Critical:**
- AI providing advice that could harm user safety
- Personal data exposed to other users
- Systematic discrimination detected
- NCAA compliance violation in guidance

**P1 - High:**
- Chatbot consistently providing incorrect information
- Recommendation algorithm returning wrong results
- Email classification causing data loss
- Multiple users reporting same serious issue

**P2 - Medium:**
- Occasional incorrect recommendations
- Slow response times affecting user experience
- Minor inaccuracies in email parsing
- Single-user reports of unusual behavior

**P3 - Low:**
- Cosmetic issues in AI responses
- Edge case handling gaps
- Feature requests disguised as incidents
- Isolated, non-reproducible issues

### 4.3 Incident Types

| Type | Description | Typical Severity |
|------|-------------|-----------------|
| Safety | Output that could cause harm | P0-P1 |
| Accuracy | Incorrect information or recommendations | P1-P2 |
| Privacy | Data handling concerns | P0-P1 |
| Performance | Speed or availability issues | P2-P3 |
| Fairness | Concern about biased treatment | P1-P2 |
| Technical | System errors or failures | P1-P3 |

---

## 5. Response Procedures

### 5.1 Immediate Response (All Incidents)

**Step 1: Acknowledge (Within 30 minutes)**
- Mark incident as "Reviewing" in admin dashboard
- Initial assessment of severity
- Determine if emergency action needed

**Step 2: Assess Severity**
- Review incident details
- Check for related reports
- Determine scope of impact
- Assign severity level (P0-P3)

**Step 3: Escalate if Needed**
- P0/P1: Immediate action required
- P2/P3: Queue for scheduled resolution

### 5.2 P0/P1 Response Protocol

```
HOUR 0-1: CONTAIN
├── Assess: Is this actively causing harm?
├── If YES: Activate emergency kill switch
├── If PARTIAL: Disable specific affected feature
├── Notify: Alert any affected users if needed
└── Document: Log all actions taken

HOUR 1-4: INVESTIGATE
├── Reproduce: Can we recreate the issue?
├── Scope: How many users affected?
├── Root Cause: What caused this?
└── Document: Log findings

HOUR 4-24: RESOLVE
├── Fix: Implement correction
├── Test: Verify fix works
├── Deploy: Push fix to production
├── Re-enable: Restore disabled features
└── Verify: Confirm normal operation

HOUR 24-72: FOLLOW-UP
├── User Communication: Notify affected users
├── Post-Incident Review: What happened and why
├── Prevention: What changes prevent recurrence
└── Documentation: Update procedures if needed
```

### 5.3 P2/P3 Response Protocol

```
DAY 1: TRIAGE
├── Confirm: Verify the issue exists
├── Prioritize: Place in backlog appropriately
├── Communicate: Update incident status
└── Document: Log initial findings

WEEK 1-2: RESOLVE
├── Investigate: Root cause analysis
├── Fix: Implement solution
├── Test: Verify correction
└── Deploy: Release fix

POST-FIX: CLOSE
├── Update Status: Mark as resolved
├── Document: Resolution notes
└── Monitor: Watch for recurrence
```

---

## 6. Emergency Controls ✅ IMPLEMENTED

### 6.1 Emergency Kill Switch

**Location:** /admin/ai-controls

**Activation:**
1. Navigate to AI Controls admin page
2. Click "Disable All AI Features"
3. Type "DISABLE" to confirm
4. All AI features immediately disabled

**Effect:**
- Chatbot shows "temporarily unavailable"
- Recommendations show static list
- Email classification disabled
- Health score hidden

**Restoration:**
1. Navigate to AI Controls admin page
2. Toggle individual features back on, OR
3. Click "Enable All AI Features"
4. Verify normal operation

### 6.2 Individual Feature Controls

Each AI system can be independently controlled:
- Toggle Chatbot on/off
- Toggle Recommendations on/off
- Toggle Email Classification on/off
- Toggle Health Score on/off

This allows surgical response to issues affecting single features.

---

## 7. Communication Templates

### 7.1 User Notification - Active Issue

**Subject:** LAX Commit Coach - Temporary AI Feature Update

```
Hi [Name],

We've identified an issue with [feature name] and have temporarily 
disabled it while we implement a fix.

What this means for you:
- [Feature] is temporarily unavailable
- All other features continue to work normally
- Your data is safe and unaffected

We expect to restore full functionality within [timeframe].

Thank you for your patience.

The LAX Commit Coach Team
```

### 7.2 User Notification - Resolution

**Subject:** LAX Commit Coach - Feature Restored

```
Hi [Name],

Good news! The issue with [feature name] has been resolved and 
full functionality is restored.

What happened:
[Brief, non-technical explanation]

What we did:
[Brief description of fix]

Thank you for your patience and for being part of LAX Commit Coach.

The LAX Commit Coach Team
```

### 7.3 Internal Incident Log Template

```
INCIDENT ID: INC-YYYY-MM-DD-###
REPORTED: [Date/Time]
REPORTER: [User ID or Admin]
SEVERITY: [P0/P1/P2/P3]

DESCRIPTION:
[What happened]

AFFECTED SYSTEM(S):
[LAX-AI-001/002/003/004]

IMPACT:
[Number of users, scope of issue]

TIMELINE:
- [Time]: Incident reported
- [Time]: Acknowledged
- [Time]: Investigation began
- [Time]: Root cause identified
- [Time]: Fix implemented
- [Time]: Resolved

ROOT CAUSE:
[What caused the issue]

RESOLUTION:
[What was done to fix it]

PREVENTION:
[What changes prevent recurrence]

LESSONS LEARNED:
[Key takeaways]
```

---

## 8. Post-Incident Review

### 8.1 When to Conduct

- All P0 incidents: Required within 72 hours
- All P1 incidents: Required within 1 week
- P2 incidents: As needed
- P3 incidents: Not required

### 8.2 Review Format

**Participants:** AI Risk Owner + anyone involved in response

**Agenda:**
1. Incident summary
2. Timeline review
3. What went well
4. What could improve
5. Action items

**Output:**
- Written summary
- Action items with owners
- Updates to this plan if needed

### 8.3 Continuous Improvement

After each review:
- Update incident response procedures if gaps found
- Add new test cases to validation suite
- Update monitoring/alerting if detection was slow
- Share learnings with team

---

## 9. Incident Tracking

### 9.1 Status Workflow

```
NEW → REVIEWING → INVESTIGATING → RESOLVED
                              ↘ DISMISSED (if invalid)
```

**Status Definitions:**
- **New:** Just reported, not yet reviewed
- **Reviewing:** Admin is assessing the report
- **Investigating:** Active work to resolve
- **Resolved:** Issue fixed, documented
- **Dismissed:** Invalid report or duplicate

### 9.2 Required Fields for Closure

Before marking "Resolved":
- [ ] Root cause identified
- [ ] Fix implemented and verified
- [ ] Resolution notes documented
- [ ] User notified (if applicable)
- [ ] Post-incident review scheduled (P0/P1)

---

## 10. Roles and Responsibilities

### 10.1 AI Risk Owner (Founder/CEO)

- Final decision authority on P0/P1 response
- Approval for emergency actions
- User communications for serious incidents
- Post-incident review leadership

### 10.2 Development Team

- First-line incident triage
- Technical investigation
- Fix implementation
- Testing and deployment
- Documentation

### 10.3 On-Call Expectations

Given current team size:
- Check incident dashboard daily
- Email notifications for new P0/P1 incidents
- Response within 4 hours for P0
- Response within 24 hours for P1

---

## 11. External Dependencies

### 11.1 Google Gemini (AI Provider)

**If Gemini is unavailable:**
- Chatbot: Show "temporarily unavailable"
- Email Classification: Disable, allow manual entry
- Monitor Google Cloud Status page
- No action possible except wait for restoration

**Contact:** Google Cloud Support (if enterprise agreement)

### 11.2 Supabase (Database/Auth)

**If Supabase is unavailable:**
- Entire application affected
- Monitor Supabase Status page
- No AI-specific response needed

### 11.3 Lovable (Hosting)

**If Lovable is unavailable:**
- Entire application affected
- Monitor Lovable Status page
- No AI-specific response needed

---

## 12. Testing This Plan

### 12.1 Quarterly Drill

Conduct tabletop exercise quarterly:
1. Present hypothetical incident scenario
2. Walk through response steps
3. Identify gaps or confusion
4. Update plan as needed

### 12.2 Kill Switch Test

Test emergency controls quarterly:
1. Activate kill switch (in non-peak hours)
2. Verify all AI features disabled
3. Verify app functions without AI
4. Restore features
5. Verify normal operation

---

## 13. Document Maintenance

### 13.1 Review Schedule

- **Quarterly:** Review and update procedures
- **Post-Incident:** Update if gaps found
- **Annually:** Comprehensive review

### 13.2 Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | Nov 2025 | Initial plan |
| 2.0 | Nov 24, 2025 | Added implemented features, detailed workflows |

---

## 14. Quick Reference Card

### Emergency Response Checklist

```
□ Assess: Is this P0 (safety/breach) or P1 (major impact)?
□ Contain: Kill switch if needed (/admin/ai-controls)
□ Communicate: Notify affected users if needed
□ Investigate: Find root cause
□ Fix: Implement solution
□ Verify: Test fix works
□ Restore: Re-enable features
□ Document: Log everything
□ Review: Schedule post-incident review
```

### Key Contacts

| Role | Contact |
|------|---------|
| AI Risk Owner | Rob Parker (Founder) |
| Support Email | help@laxcommitcoach.com |
| Incident Dashboard | /admin/ai-incidents |
| Kill Switch | /admin/ai-controls |

---

*This document is part of the LAX Commit Coach AI Governance Framework.*
