# Immediate Security Actions - Tactical Response Plan

**Created:** November 2, 2025  
**Status:** ACTIVE  
**Priority:** CRITICAL  
**Owner:** Group ICT Manager  
**Related Documents:** 
- Web Infrastructure & Security Strategy (comprehensive strategy)
- Planner Strategy Presentation (business context)

---

## 🚨 CRITICAL ACTIONS (Next 7 Days)

### Day 1-3: Incident Response & Investigation

- [ ] **Incident Documentation**
  - Create incident timeline and document all known facts
  - Identify attack vector if possible (check logs, file changes)
  - Determine if other environments/sites compromised
  - Notify stakeholders (leadership, affected teams)
  
- [ ] **Immediate Containment**
  - Take compromised UAT site offline OR restrict access via IP whitelist
  - Change ALL credentials:
    - [ ] Hosting admin passwords
    - [ ] Database passwords
    - [ ] FTP/SSH access credentials
    - [ ] CMS admin passwords
    - [ ] API keys and tokens
  - [ ] Enable 2FA/MFA on all administrative accounts
  - [ ] Review user accounts and remove any unauthorized accounts

- [ ] **Production Security Audit**
  - Scan production Lugna planner for indicators of compromise
  - Check file integrity (compare with known good backups)
  - Review access logs for suspicious activity
  - Verify no backdoors or malicious code

### Day 3-7: Security Hardening

- [ ] **Update All Software**
  - Update WordPress core (if applicable)
  - Update all plugins and themes
  - Update server OS and dependencies
  - Patch any known vulnerabilities

- [ ] **Implement Basic Security Controls**
  - [ ] Install security plugin (Wordfence, Sucuri, or iThemes Security)
  - [ ] Enable file integrity monitoring
  - [ ] Disable directory browsing
  - [ ] Remove unused plugins/themes
  - [ ] Harden file permissions

- [ ] **Google Safe Browsing Remediation**
  - [ ] Document all remediation steps taken
  - [ ] Request Google Safe Browsing review at https://safebrowsing.google.com/
  - [ ] Monitor delisting status
  - [ ] Set up Google Search Console if not already configured

---

## 🔧 HIGH PRIORITY ACTIONS (Days 7-14)

### Environment Quick Wins

- [ ] **Separate UAT Domain Immediately**
  - Create new subdomain: `uat-planner.lugna-staging.com` (or similar)
  - Point to isolated server/hosting if possible (even if temporary)
  - Add prominent "UAT ENVIRONMENT - NOT FOR PRODUCTION USE" banner
  - Implement basic authentication (htpasswd or similar)
  - Add noindex meta tags and robots.txt disallow

- [ ] **Inventory All Web Properties**
  - [ ] List all planners (Lugna, Wardrobe, Glass, Signs, Pool/Garden)
  - [ ] List all WordPress sites (19 identified)
  - [ ] Document current hosting provider for each
  - [ ] Identify which sites share infrastructure
  - [ ] Mark business criticality (Critical, High, Medium, Low)

- [ ] **SixT4 Hosting Assessment**
  - Schedule call with SixT4 to understand:
    - [ ] How many servers are sites hosted on?
    - [ ] Are dev/UAT/production on same servers?
    - [ ] What backup procedures are in place?
    - [ ] What access controls exist?
    - [ ] What security monitoring is in place?
    - [ ] What are monthly costs vs managed hosting?

---

## 📋 MEDIUM PRIORITY ACTIONS (Days 14-30)

### Planning & Documentation

- [ ] **Define Environment Standards**
  - Document in environment-separation-standards.md (see separate doc)
  - Review and approve with IT governance
  - Communicate to all development teams

- [ ] **Create Migration Plan**
  - Prioritize sites for migration (security risk × business impact)
  - Get quotes from managed WordPress hosts (WP Engine, Kinsta, Cloudways)
  - Estimate AWS costs for serverless planner migration
  - Create phased migration timeline (30/60/90 day milestones)
  - Get budget approval

- [ ] **Update IT Governance**
  - Add web infrastructure security to governance agenda
  - Define approval process for new web properties
  - Establish security review requirements
  - Create change management procedures for production deployments

### Security Tooling

- [ ] **Implement Basic Monitoring**
  - [ ] Set up UptimeRobot or similar for uptime monitoring
  - [ ] Configure SSL certificate expiry monitoring
  - [ ] Set up alerts (email, SMS, Slack)
  - [ ] Create status dashboard

- [ ] **Enable WAF Protection**
  - Evaluate: Cloudflare (easiest), AWS WAF, other
  - Start with free tier for immediate protection
  - Configure for at least production sites initially
  - Enable DDoS protection

---

## ✅ SUCCESS CRITERIA (30 Days)

- [ ] **Incident Resolved**
  - UAT site cleaned and secured OR rebuilt
  - Google Safe Browsing delisting confirmed
  - No production sites compromised
  - All credentials rotated and secured

- [ ] **Environment Separation**
  - UAT has different domain from production
  - UAT behind authentication or IP restriction
  - Clear visual indicators of non-production environments
  - Documented standards in place

- [ ] **Risk Reduction**
  - All administrative accounts have 2FA/MFA
  - Basic security monitoring operational
  - Inventory of all web properties complete
  - Migration plan approved and funded

- [ ] **Governance**
  - Security incident reviewed with leadership
  - Infrastructure modernization strategy approved
  - Budget allocated for Phase 1 migration
  - Responsibilities assigned and communicated

---

## 🔥 ESCALATION TRIGGERS

Escalate to leadership immediately if:

- [ ] Production sites show signs of compromise
- [ ] Customer data potentially exposed
- [ ] Additional security incidents occur
- [ ] Google delisting not resolved within 30 days
- [ ] SixT4 unable to provide required security controls
- [ ] Budget required exceeds $50k for remediation

---

## 📞 KEY CONTACTS

| Role | Contact | Phone | Email |
|------|---------|-------|-------|
| **Group ICT Manager** | [Name] | [Phone] | [Email] |
| **Executive Sponsor** | [Name] | [Phone] | [Email] |
| **SixT4 Partner Contact** | [Name] | [Phone] | [Email] |
| **IT Support Partner** | [Name] | [Phone] | [Email] |
| **Emergency Escalation** | [Name] | [Phone] | [Email] |

---

## 📊 DAILY STATUS TRACKING (Days 1-14)

### Day 1: [Date]
- [ ] Completed: _______________
- [ ] Blockers: _______________
- [ ] Next: _______________

### Day 2: [Date]
- [ ] Completed: _______________
- [ ] Blockers: _______________
- [ ] Next: _______________

### Day 3: [Date]
- [ ] Completed: _______________
- [ ] Blockers: _______________
- [ ] Next: _______________

### Day 7: [Date]
- [ ] Completed: _______________
- [ ] Blockers: _______________
- [ ] Next: _______________

### Day 14: [Date]
- [ ] Completed: _______________
- [ ] Blockers: _______________
- [ ] Next: _______________

### Day 30: [Date]
- [ ] Completed: _______________
- [ ] Remaining Issues: _______________
- [ ] Next Phase: _______________

---

## 📝 LESSONS LEARNED (To be completed after 30 days)

### What Went Well
- 

### What Could Be Improved
- 

### Actions to Prevent Recurrence
- 

### Process Improvements
- 

---

**Next Review:** Daily for first 14 days, then weekly until complete  
**Document Owner:** Group ICT Manager  
**Last Updated:** November 2, 2025

