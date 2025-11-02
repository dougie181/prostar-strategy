# Web Infrastructure & Security Strategy

**Document Purpose:** Define strategic approach to web hosting, security, and infrastructure following the Lugna 3D planner UAT security incident

**Date Created:** November 2, 2025  
**Alignment:** IT Strategy "Foundation First" approach  
**Review Frequency:** Quarterly (aligned with IT Strategy Governance Committee)

---

## 🚨 Triggering Event: Security Incident Analysis

### What Happened
- **Incident:** Lugna 3D planner UAT site defaced
- **Impact:** Google Safe Browsing flagged URL as malicious, browsers displayed security warnings
- **Business Risk:** Potential customer trust damage, brand reputation impact
- **Operational Impact:** Emergency response required, loss of UAT environment functionality

### Root Cause Analysis
1. **Environment Separation Failure**
   - Dev/UAT/Production shared domain structure
   - No clear separation between non-production and production environments
   - UAT environment publicly accessible with same domain authority as production

2. **Infrastructure Security Gaps**
   - Dev and UAT likely hosted on same infrastructure as production
   - Single point of compromise could affect multiple environments
   - No isolation between customer-facing and testing environments

3. **Operational Dependency Issues**
   - WordPress sites hosted by partner (SixT4), not managed hosting platform
   - Backup/restore/cloning requires partner intervention (no self-service)
   - Possible single-server hosting for multiple sites/environments
   - Limited visibility and control over infrastructure security

4. **Architectural Concerns**
   - Traditional server-based hosting increases attack surface
   - No mention of serverless or modern cloud-native architecture
   - Web applications potentially vulnerable to common attack vectors

---

## 🎯 Strategic Principles

### 1. **Environment Isolation**
**Principle:** Development, UAT, and Production environments must be completely isolated across domains, infrastructure, and network layers.

**Rationale:** 
- Prevents compromise of non-production environments from affecting production
- Enables secure testing without exposing production data or infrastructure
- Supports different security postures for different environment types

### 2. **Infrastructure Independence**
**Principle:** Non-production environments must not share physical or virtual infrastructure with production systems.

**Rationale:**
- Prevents lateral movement from compromised non-production systems
- Allows for different patching and update schedules
- Reduces risk of resource contention affecting production performance

### 3. **Modern Cloud-Native Architecture**
**Principle:** Customer-facing web applications should adopt serverless/cloud-native architecture where appropriate for security, scalability, and cost benefits.

**Rationale:**
- Reduced attack surface (no OS to patch, automatic scaling)
- Pay-per-use cost model aligns with variable traffic patterns
- Built-in redundancy and disaster recovery
- Automatic security updates and patching by cloud provider

### 4. **Self-Service Operations**
**Principle:** Internal teams should have self-service capabilities for common operations (backup, restore, cloning, monitoring) while maintaining security controls.

**Rationale:**
- Reduces dependency on external partners for routine operations
- Enables faster incident response and troubleshooting
- Lower operational costs over time
- Better visibility and control

### 5. **Defense in Depth**
**Principle:** Multiple layers of security controls at network, application, and data levels.

**Rationale:**
- Single control failure doesn't result in complete compromise
- Different attack vectors require different defensive measures
- Compliance and regulatory requirements often mandate layered security

---

## 🏗️ Strategic Architecture Recommendations

### Customer-Facing Web Applications (Planners, Calculators)

#### **Recommended Architecture: Serverless/Cloud-Native**

**Technology Stack:**
- **Frontend:** Static site hosting (AWS S3 + CloudFront, Azure Static Web Apps, or Netlify/Vercel)
- **Backend APIs:** Serverless functions (AWS Lambda, Azure Functions)
- **Database:** Managed database services (AWS RDS, Azure SQL, DynamoDB)
- **Authentication:** Managed auth services (AWS Cognito, Auth0)
- **CDN:** CloudFront, Azure CDN, or Cloudflare for performance and DDoS protection

**Benefits:**
- **Security:** No servers to manage, automatic patching, built-in DDoS protection
- **Scalability:** Automatic scaling based on demand
- **Cost:** Pay only for actual usage (especially beneficial for variable traffic)
- **Reliability:** Built-in redundancy across availability zones
- **Performance:** CDN edge caching for global performance
- **Maintenance:** Minimal operational overhead

**Considerations:**
- Initial migration effort required for existing planners
- Learning curve for serverless development patterns
- Potential vendor lock-in (mitigated by Infrastructure as Code)

#### **Environment Strategy for Planners:**

| Environment | Domain Pattern | Infrastructure | Security Level | Data |
|-------------|---------------|----------------|----------------|------|
| **Production** | `planner.lugna.online` | AWS Production account | Highest | Real products/pricing |
| **UAT** | `uat-planner.lugna-staging.com` | AWS Staging account | High | Sanitized data |
| **Development** | `dev-planner.lugna-dev.com` | AWS Dev account | Medium | Test data |
| **Local** | `localhost:3000` | Developer machines | Basic | Mock data |

**Key Requirements:**
- ✅ Different domains (prevents cross-environment cookies/sessions)
- ✅ Different AWS accounts (complete isolation)
- ✅ Different subdomain structure (clearly identifies environment)
- ✅ UAT/Dev not indexed by search engines (robots.txt, noindex meta tags)
- ✅ UAT/Dev behind authentication (basic auth or IP whitelist)

---

### Corporate Websites & WordPress Sites

#### **Recommended Architecture: Managed WordPress Hosting**

**Migration Path:**
- **Phase 1 (Immediate):** Move from SixT4 custom hosting to managed WordPress platform
  - Options: WP Engine, Kinsta, Cloudways, AWS Lightsail for WordPress
  - Priority: High-value customer-facing sites first
  
**Benefits:**
- **Security:** Automatic WordPress updates, built-in security monitoring, malware scanning
- **Performance:** WordPress-optimized infrastructure, automatic caching
- **Self-Service:** Dashboard access for backups, staging/cloning, monitoring
- **Support:** WordPress-specialized support teams
- **Compliance:** SOC 2, PCI DSS compliance for e-commerce

**Platform Comparison:**

| Platform | Best For | Pros | Cons | Est. Cost/Site |
|----------|----------|------|------|----------------|
| **WP Engine** | High-traffic, business-critical sites | Premium support, excellent performance, staging environments included | Higher cost | $30-100/month |
| **Kinsta** | Performance-focused sites | Google Cloud infrastructure, excellent speed | Mid-high cost | $35-100/month |
| **Cloudways** | Multiple sites, flexibility | Multi-cloud, pay-per-use, good value | More technical setup | $10-50/month |
| **AWS Lightsail** | Cost-conscious, technical teams | AWS integration, flexible, low cost | More management required | $5-20/month |

**Recommended:** Start with **WP Engine** or **Kinsta** for customer-facing sites, **Cloudways** for internal/lower-priority sites

#### **Environment Strategy for WordPress:**

| Environment | Hosting Approach | Access Control | Backup Frequency |
|-------------|------------------|----------------|------------------|
| **Production** | Managed hosting platform | Public | Daily automated |
| **Staging** | Platform staging feature | Password protected | On-demand |
| **Development** | Local Docker or platform dev env | Local only | Manual |

---

### Web Applications & Internal Tools

#### **Recommended Architecture: Platform-as-a-Service (PaaS)**

**Technology Options:**
- **Azure App Service** (if using Microsoft stack)
- **AWS Elastic Beanstalk** (for flexibility)
- **Google Cloud Run** (for containerized apps)
- **Heroku** (for rapid development/prototyping)

**Benefits:**
- Managed infrastructure with automatic patching
- Easy deployment and rollback
- Built-in monitoring and logging
- Good balance of control vs. management overhead

**Use Cases:**
- Internal business tools
- Admin dashboards
- Integration middleware
- Custom web applications requiring more control than serverless

---

## 🛡️ Security Architecture Standards

### Network Security

#### **1. Web Application Firewall (WAF)**
- **Requirement:** All customer-facing web applications must be behind a WAF
- **Implementation:** AWS WAF, Cloudflare, Azure Application Gateway
- **Rules:** OWASP Top 10 protection, rate limiting, geo-blocking if applicable
- **Cost:** ~$10-50/month depending on traffic

#### **2. DDoS Protection**
- **Requirement:** Automatic DDoS mitigation for all public-facing applications
- **Implementation:** CloudFront + AWS Shield (basic), Cloudflare
- **Tier:** Basic for most sites, Advanced for critical business applications

#### **3. SSL/TLS Certificates**
- **Requirement:** HTTPS only, TLS 1.2 minimum (prefer TLS 1.3)
- **Implementation:** Let's Encrypt (free) or AWS Certificate Manager
- **Renewal:** Automated renewal required
- **Monitoring:** Certificate expiry alerts

#### **4. Access Control**
- **Non-Production Environments:**
  - Basic authentication OR IP whitelist (VPN/office IPs)
  - Clear "NON-PRODUCTION" warnings on all pages
  - Robots.txt disallow all
  - No indexing by search engines

### Application Security

#### **1. Dependency Management**
- **Requirement:** Automated dependency vulnerability scanning
- **Tools:** Dependabot (GitHub), Snyk, AWS Inspector
- **Response SLA:** Critical vulnerabilities patched within 48 hours

#### **2. Code Security Scanning**
- **Requirement:** Static Application Security Testing (SAST) in CI/CD pipeline
- **Tools:** SonarQube, GitHub Advanced Security, Snyk Code
- **Frequency:** Every commit to main/production branches

#### **3. Security Headers**
- **Required Headers:**
  - Content-Security-Policy
  - X-Frame-Options: DENY
  - X-Content-Type-Options: nosniff
  - Strict-Transport-Security (HSTS)
  - Referrer-Policy
- **Validation:** Security Headers scanner (securityheaders.com)

#### **4. Authentication & Authorization**
- **Customer Authentication:** Managed service (Auth0, AWS Cognito)
- **Internal Tools:** SSO integration with Microsoft 365
- **Session Management:** Secure cookies, appropriate timeouts
- **API Security:** OAuth 2.0 / JWT tokens with short expiry

### Data Security

#### **1. Data Classification**
- **Public:** Marketing content, product information
- **Internal:** Business data, analytics, configurations
- **Confidential:** Customer PII, financial data, authentication credentials
- **Restricted:** Payment card data (PCI DSS scope)

#### **2. Encryption**
- **In Transit:** TLS 1.2+ for all data transmission
- **At Rest:** Encryption for all databases and file storage
- **Key Management:** AWS KMS, Azure Key Vault for encryption keys

#### **3. Backup & Recovery**
- **Production:** Daily automated backups, 30-day retention minimum
- **Recovery Testing:** Quarterly restore testing
- **Geographic Redundancy:** Backups in different region than primary
- **Immutable Backups:** Protection against ransomware

### Monitoring & Incident Response

#### **1. Security Monitoring**
- **Requirement:** Centralized logging and security event monitoring
- **Implementation:** AWS CloudWatch, Azure Monitor, Datadog
- **Alerts:** Critical security events trigger immediate notifications
- **Retention:** 90 days minimum for compliance

#### **2. Uptime Monitoring**
- **Requirement:** External uptime monitoring for all customer-facing applications
- **Tools:** UptimeRobot, Pingdom, StatusCake
- **SLA:** 99.5% uptime target
- **Alerting:** Multi-channel (email, SMS, Slack)

#### **3. Security Incident Response**
- **Playbook:** Documented incident response procedures
- **Team:** Defined roles and escalation paths
- **Communication:** Stakeholder notification templates
- **Post-Incident:** Root cause analysis and remediation tracking

---

## 📋 Tactical Action Plan

### Immediate Actions (Next 30 Days) - HIGH PRIORITY

#### **1. Lugna Planner Infrastructure Remediation**
**Status:** CRITICAL  
**Objective:** Secure all Lugna planner environments and prevent recurrence

- [ ] **Incident Investigation** (Days 1-3)
  - Document full timeline of security incident
  - Identify attack vector and vulnerabilities exploited
  - Assess scope: were other sites/environments compromised?
  - Preserve evidence and logs

- [ ] **Immediate Security Hardening** (Days 1-7)
  - Remove or completely rebuild compromised UAT environment
  - Audit production Lugna planner for indicators of compromise
  - Change all credentials (hosting, admin, database, API keys)
  - Enable 2FA/MFA on all administrative accounts
  - Update all software dependencies to latest secure versions

- [ ] **Environment Separation - Quick Wins** (Days 7-14)
  - Move UAT to different subdomain: `uat-planner.lugna-staging.com`
  - Implement basic authentication on UAT environment
  - Add noindex meta tags and robots.txt to UAT
  - Create clear visual indicators (banner) showing "UAT ENVIRONMENT"
  - If possible, move UAT to separate server/account immediately

- [ ] **Google Safe Browsing Remediation** (Days 1-14)
  - Request Google Safe Browsing review after cleanup
  - Monitor delisting status
  - Document remediation steps for Google
  - Implement Google Search Console monitoring

#### **2. Infrastructure Assessment**
**Status:** HIGH PRIORITY  
**Objective:** Understand current state and plan migration

- [ ] **SixT4 Hosting Audit** (Days 1-14)
  - Document all sites hosted by SixT4
  - Confirm server architecture (shared vs dedicated, how many servers)
  - Review current backup procedures and retention
  - Document access controls and admin capabilities
  - Assess hosting costs vs managed hosting alternatives
  - Review SLA and support response times

- [ ] **WordPress Site Inventory** (Days 7-14)
  - List all WordPress sites with business priority
  - Document plugins, themes, customizations
  - Identify sites with highest security/performance requirements
  - Classify sites by importance: Critical, High, Medium, Low

- [ ] **Web Application Inventory** (Days 7-14)
  - Document all customer-facing planners and calculators
  - Map current hosting infrastructure for each
  - Identify technology stack and dependencies
  - Assess migration complexity for each (Simple, Moderate, Complex)

#### **3. Strategic Planning & Governance**
**Status:** HIGH PRIORITY  
**Objective:** Establish framework for infrastructure modernization

- [ ] **Define Environment Standards** (Days 14-21)
  - Document domain naming conventions
  - Define infrastructure separation requirements
  - Create access control matrix by environment
  - Establish monitoring and alerting requirements

- [ ] **Create Migration Prioritization Matrix** (Days 14-21)
  - Score sites by: Security risk, Business impact, Migration complexity, Cost
  - Identify Phase 1 migration candidates (next 90 days)
  - Estimate timeline and resource requirements
  - Budget estimation for managed hosting migration

- [ ] **Update IT Governance Framework** (Days 21-30)
  - Add web infrastructure security to governance scope
  - Define approval process for new web properties
  - Establish security review requirements
  - Create change management procedures for production deployments

---

### Short-Term Actions (60-90 Days) - Phase 1 Migration

#### **4. Critical WordPress Site Migration**
**Priority:** Customer-facing sites first

- [ ] **Platform Selection & Setup** (Days 30-45)
  - Evaluate WP Engine vs Kinsta vs Cloudways
  - Create account and configure initial settings
  - Set up staging and production environments
  - Configure backup schedules and monitoring

- [ ] **Pilot Migration** (Days 45-60)
  - Select 1-2 lower-risk sites for pilot migration
  - Test backup/restore procedures
  - Validate performance and functionality
  - Document migration process and lessons learned
  - Train team on new platform

- [ ] **Priority Site Migration** (Days 60-90)
  - Migrate 3-5 highest priority WordPress sites
  - protectoraluminium.com.au
  - lugna.online
  - Other high-traffic customer-facing sites
  - Implement monitoring and security scanning
  - Document configuration and credentials in password manager

#### **5. Planner Infrastructure Planning**
**Priority:** Foundation for future serverless migration

- [ ] **Architecture Design** (Days 30-60)
  - Design serverless architecture for planner applications
  - Select cloud provider (AWS recommended based on features/cost)
  - Design multi-account strategy (Production, Staging, Development)
  - Plan CI/CD pipeline for automated deployments
  - Cost modeling and budget approval

- [ ] **Development Environment Setup** (Days 60-90)
  - Set up AWS accounts and organization structure
  - Configure development environment for new architecture
  - Create proof-of-concept serverless planner (simple calculator)
  - Test deployment pipeline and monitoring
  - Document development standards and practices

#### **6. Security Tooling Implementation**
**Priority:** Establish baseline security controls

- [ ] **Web Application Firewall** (Days 30-45)
  - Deploy Cloudflare or AWS WAF for customer-facing sites
  - Configure OWASP rule sets
  - Set up rate limiting and geo-blocking (if needed)
  - Enable DDoS protection

- [ ] **Monitoring & Alerting** (Days 45-75)
  - Configure uptime monitoring (UptimeRobot or similar)
  - Set up SSL certificate expiry monitoring
  - Implement security header scanning
  - Create incident notification channels (email, SMS, Slack)

- [ ] **Dependency Scanning** (Days 60-90)
  - Enable Dependabot or Snyk for code repositories
  - Configure automated security scanning in CI/CD
  - Establish vulnerability remediation SLAs
  - Document patching procedures

---

### Medium-Term Actions (6-12 Months) - Phase 2 Modernization

#### **7. Complete WordPress Migration**
- [ ] Migrate remaining WordPress sites to managed hosting
- [ ] Decommission SixT4 hosting (if appropriate)
- [ ] Implement automated backup validation testing
- [ ] Establish ongoing maintenance and update schedules

#### **8. Planner Modernization**
- [ ] Migrate Wardrobe planner to serverless architecture
- [ ] Migrate Signs planner to serverless architecture
- [ ] Rebuild or migrate Glass planner
- [ ] Migrate Lugna 3D planner to serverless (most complex)
- [ ] Establish planner monitoring and analytics
- [ ] Integrate with Acumatica for real-time pricing (aligned with IT strategy)

#### **9. Advanced Security Capabilities**
- [ ] Implement SIEM or security monitoring platform
- [ ] Establish penetration testing schedule (annual minimum)
- [ ] Deploy secrets management solution (AWS Secrets Manager, HashiCorp Vault)
- [ ] Implement infrastructure as code (Terraform/CloudFormation)
- [ ] Create disaster recovery playbooks and test quarterly

#### **10. Self-Service Operations**
- [ ] Document all infrastructure and access procedures
- [ ] Train internal team on cloud infrastructure management
- [ ] Establish runbooks for common operations
- [ ] Create self-service dashboard for deployment status
- [ ] Reduce external partner dependency for routine operations

---

## 💰 Budget Considerations

### Initial Investment (First Year)

| Category | Item | Est. Annual Cost | Priority |
|----------|------|------------------|----------|
| **Managed WordPress Hosting** | WP Engine for 3-5 critical sites | $1,800 - $6,000 | HIGH |
| **Managed WordPress Hosting** | Cloudways for 10-15 other sites | $1,200 - $6,000 | MEDIUM |
| **Cloud Infrastructure** | AWS accounts for planners (Dev/Staging/Prod) | $2,400 - $6,000 | HIGH |
| **Security Services** | Cloudflare Pro for WAF and DDoS | $1,200 | HIGH |
| **Monitoring** | UptimeRobot or Pingdom | $240 - $600 | HIGH |
| **Security Scanning** | Snyk or similar for dependency scanning | $600 - $2,400 | MEDIUM |
| **Development Tools** | CI/CD, code repositories (may be covered) | $0 - $1,200 | MEDIUM |
| **Migration Services** | External expertise if needed | $5,000 - $15,000 | MEDIUM |
| **Training** | Cloud and security training for team | $2,000 - $5,000 | MEDIUM |
| **Total Estimated** | | **$14,440 - $42,200** | |

### Ongoing Operational Costs (Annual)

| Category | Est. Annual Cost | Notes |
|----------|------------------|-------|
| **Managed WordPress Hosting** | $3,000 - $12,000 | Depends on number of sites and tier |
| **Cloud Infrastructure** | $3,000 - $10,000 | Varies with traffic and features used |
| **Security Services** | $1,800 - $4,000 | WAF, monitoring, scanning |
| **Backup Storage** | $600 - $1,200 | Additional backup retention |
| **Total Estimated** | **$8,400 - $27,200** | |

### Cost Comparison vs Current State

**Current State (Estimated):**
- SixT4 hosting for all sites: ~$X/month (need to confirm)
- Partner time for maintenance/support: ~$X/year
- Limited security and monitoring capabilities
- High risk of security incidents (indirect costs)

**Proposed State:**
- Higher upfront investment but significantly better:
  - Security posture and risk reduction
  - Self-service capabilities
  - Performance and reliability
  - Scalability and flexibility
  - Reduced partner dependency costs

**ROI Factors:**
- Reduced security incident risk (potential brand damage, customer loss)
- Reduced operational overhead (self-service vs partner tickets)
- Improved performance and uptime (revenue protection)
- Foundation for future digital initiatives
- Scalability without major infrastructure changes

---

## 📊 Success Metrics

### Security Metrics
- **Zero security incidents** resulting in site compromise or defacement
- **99.9% SSL certificate uptime** (no expired certificates)
- **100% of sites** behind WAF protection
- **Critical vulnerabilities** patched within 48-hour SLA
- **Zero production data** in non-production environments

### Operational Metrics
- **Backup success rate** >99.5%
- **Site uptime** >99.5% for customer-facing applications
- **Recovery Time Objective (RTO)** <4 hours for critical sites
- **Recovery Point Objective (RPO)** <24 hours (daily backups)
- **Self-service operations** >80% (reduced partner ticket volume)

### Performance Metrics
- **Page load time** <2 seconds for customer-facing sites
- **Time to deploy** new sites reduced by 50%
- **Time to clone/stage** environments <30 minutes (self-service)
- **Cost per site** maintained or reduced compared to current state

### Strategic Alignment Metrics
- **Environment separation compliance** 100% (all sites follow standards)
- **Infrastructure as Code coverage** >80% by end of Year 1
- **Team training completion** 100% of IT team certified in cloud basics
- **Documentation coverage** 100% of infrastructure documented

---

## 🤝 Roles & Responsibilities

### IT Strategy Governance Committee
- **Approval:** Overall strategy, budget, major technology decisions
- **Review:** Quarterly progress reviews and risk assessments
- **Escalation:** Security incidents, budget overruns, strategic pivots

### Group ICT Manager
- **Ownership:** Overall infrastructure security strategy execution
- **Responsibilities:** Partner selection, budget management, team capability building
- **Reporting:** Monthly progress to governance, incident escalation

### IT Operations Team
- **Responsibilities:** Day-to-day operations, monitoring, incident response
- **Training:** Cloud infrastructure, security best practices, new platforms
- **Empowerment:** Self-service operations, access to tools and dashboards

### External Partners
- **SixT4 (transitioning):** Support existing infrastructure during migration
- **Acumatica Partner:** ERP integration with planners (aligned with IT strategy)
- **Cloud/Security Consultants:** Architecture review, implementation support, training
- **Managed Hosting Providers:** Platform support, WordPress expertise

### Business Stakeholders
- **Marketing/Product:** Requirements for customer-facing sites and planners
- **Sales:** Feedback on planner effectiveness and customer experience
- **Finance:** Budget approval and ROI validation

---

## 🔄 Review & Update Cadence

### Monthly Review (IT Operational Governance)
- Migration progress and blockers
- Security incidents and response effectiveness
- Budget tracking and forecast
- Operational metrics review

### Quarterly Review (IT Strategy Governance Committee)
- Strategic alignment assessment
- Risk register review and mitigation effectiveness
- Budget vs actual analysis
- Technology evolution and recommendations

### Annual Review
- Complete strategy refresh
- Technology stack evaluation
- Partner performance assessment
- Budget planning for following year
- Training and capability assessment

---

## ✅ Decision Required from Leadership

### Immediate Approvals Needed (Next 30 Days)

1. **Approve Infrastructure Security Strategy**
   - Environment separation requirements
   - Migration to managed hosting approach
   - Serverless architecture for planners

2. **Budget Authorization for Phase 1**
   - Managed WordPress hosting migration: $3,000 - $12,000/year
   - AWS cloud infrastructure setup: $2,400 - $6,000/year  
   - Security services (WAF, monitoring): $2,000 - $5,000/year
   - Migration services if needed: $5,000 - $15,000 one-time

3. **Resource Allocation**
   - IT team time for migration execution
   - External partner engagement for complex migrations
   - Training budget for cloud and security skills

4. **Risk Acceptance**
   - Acknowledge current hosting approach is high risk
   - Approve investment in infrastructure modernization
   - Commit to ongoing operational costs for enhanced security

### Success Criteria for Phase 1 (90 Days)
- ✅ Lugna planner environments properly separated and secured
- ✅ 3-5 critical WordPress sites migrated to managed hosting
- ✅ Basic security controls (WAF, monitoring) operational
- ✅ Environment standards documented and enforced
- ✅ Self-service capabilities demonstrated for key operations
- ✅ Team trained on new platforms and procedures

---

## 📚 Appendices

### Appendix A: Incident Response Playbook
*(To be developed in Phase 1)*

### Appendix B: Environment Naming Standards
*(Included in tactical actions)*

### Appendix C: Security Checklist for New Web Properties
*(To be developed in Phase 1)*

### Appendix D: Technology Evaluation Criteria
*(Platform selection framework)*

### Appendix E: Migration Runbook Templates
*(To be developed during pilot migration)*

---

**Document Owner:** Group ICT Manager  
**Review Date:** February 1, 2026  
**Distribution:** IT Strategy Governance Committee, IT Operations Team  
**Classification:** Internal - Business Sensitive

