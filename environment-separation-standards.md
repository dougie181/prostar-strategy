# Environment Separation Standards

**Document Purpose:** Define mandatory standards for Dev/UAT/Production environment separation  
**Effective Date:** November 2, 2025  
**Status:** APPROVED (pending IT Governance Committee review)  
**Applies To:** All web applications, planners, calculators, and customer-facing digital properties  
**Review Frequency:** Quarterly  

---

## 🎯 Purpose & Scope

### Why Environment Separation Matters

Following the Lugna UAT security incident, this document establishes mandatory standards to:

1. **Prevent security incidents** in non-production environments from affecting production
2. **Protect production data** from exposure in testing environments
3. **Enable safe testing** without risk to customer-facing systems
4. **Support rapid development** with appropriate guardrails
5. **Meet compliance requirements** for data protection and security

### Scope

These standards apply to:
- ✅ Customer-facing planners and calculators
- ✅ WordPress marketing and corporate websites
- ✅ Internal web applications
- ✅ Web APIs and integration endpoints
- ✅ Any web property accessible via browser

These standards do NOT apply to:
- ❌ Local development on developer workstations (separate guidelines)
- ❌ Internal-only tools with no customer data (but recommended)
- ❌ One-off prototypes or proof-of-concepts (but recommended)

---

## 📋 Mandatory Standards

### 1. Domain Separation

#### **REQUIRED: Different Domains for Each Environment**

| Environment | Domain Pattern | Example | Purpose |
|-------------|----------------|---------|---------|
| **Production** | `{service}.{brand}.{tld}` | `planner.lugna.online` | Customer-facing |
| **UAT** | `uat-{service}.{brand}-staging.{tld}` | `uat-planner.lugna-staging.com` | Pre-production testing |
| **Development** | `dev-{service}.{brand}-dev.{tld}` | `dev-planner.lugna-dev.com` | Active development |
| **Local** | `localhost:{port}` or `127.0.0.1:{port}` | `localhost:3000` | Developer machines |

#### **Rationale:**
- Different domains prevent cookie/session leakage between environments
- Clear identification of environment in browser
- Prevents accidental production use of non-production URLs
- Enables different security policies per environment

#### **Anti-Patterns (DO NOT USE):**
- ❌ `planner.lugna.online/uat/` (subdirectory)
- ❌ `planner-uat.lugna.online` (same domain, different subdomain)
- ❌ `planner.lugna.online:8080` (same domain, different port)

### 2. Infrastructure Isolation

#### **REQUIRED: Separate Infrastructure Per Environment**

| Requirement | Production | UAT | Development |
|-------------|-----------|-----|-------------|
| **Cloud Account** | Separate AWS/Azure account | Separate account | Separate account OR isolated VPC |
| **Database Server** | Dedicated instance | Dedicated instance | Shared with dev (separate DBs) |
| **Application Server** | Dedicated | Dedicated | Can be shared with isolation |
| **Network** | Production VPC/VNET | Non-prod VPC/VNET | Non-prod VPC/VNET |
| **Authentication** | Production identity | Separate identity | Separate identity |

#### **Minimum Requirements:**
- Production MUST be on completely separate infrastructure
- UAT SHOULD be on separate infrastructure from production
- Dev MAY share infrastructure with UAT if properly isolated
- Local development on developer workstations

#### **Cloud Architecture Pattern:**

```
AWS Organization / Azure Tenant
├── Production Account
│   ├── VPC (10.0.0.0/16)
│   ├── Web Application (production workloads)
│   ├── Database (production data)
│   └── Monitoring (production metrics)
├── Staging Account  
│   ├── UAT VPC (10.1.0.0/16)
│   ├── UAT Application
│   └── UAT Database (sanitized data)
└── Development Account
    ├── Dev VPC (10.2.0.0/16)
    ├── Dev Application
    └── Dev Database (test data)
```

### 3. Access Control

#### **REQUIRED: Different Access Controls Per Environment**

| Control Type | Production | UAT | Development |
|-------------|-----------|-----|-------------|
| **Public Access** | YES (customers) | NO - Auth required | NO - Auth required |
| **Authentication** | Customer auth if needed | Basic Auth OR IP whitelist | Basic Auth OR IP whitelist |
| **Admin Access** | 2FA/MFA required | 2FA/MFA required | Password minimum |
| **IP Restrictions** | None (public) | Office + VPN IPs | Office + VPN IPs |
| **Search Engine** | Indexed | BLOCKED (robots.txt, noindex) | BLOCKED |

#### **UAT/Development Access Methods:**

**Option A: Basic Authentication (Recommended for simplicity)**
```
Username: [company]-uat
Password: [Strong password in password manager]
```

**Option B: IP Whitelist (Recommended for security)**
```
Allowed IPs:
- Office IP: [IP address]
- VPN Range: [IP range]
- Partner IPs: [Specific IPs as needed]
```

**Option C: SSO/OAuth (Recommended for larger teams)**
- Integrate with Microsoft 365 / Google Workspace
- Grant access via security groups
- Automatic provisioning/deprovisioning

### 4. Visual Indicators

#### **REQUIRED: Clear Environment Identification**

All non-production environments MUST have prominent visual indicators:

**Banner Requirements:**
- Appears on EVERY page
- Cannot be dismissed or hidden
- Different color per environment
- Includes environment name and warning

**Example Banners:**

**UAT Environment:**
```html
<!-- Sticky banner at top of page -->
<div style="background: #ff9800; color: #000; padding: 10px; 
            text-align: center; font-weight: bold; position: sticky; 
            top: 0; z-index: 9999;">
  ⚠️ UAT ENVIRONMENT - NOT FOR PRODUCTION USE - DATA MAY BE RESET
</div>
```

**Development Environment:**
```html
<div style="background: #f44336; color: #fff; padding: 10px; 
            text-align: center; font-weight: bold; position: sticky; 
            top: 0; z-index: 9999;">
  🔧 DEVELOPMENT ENVIRONMENT - TEST DATA ONLY - FREQUENT CHANGES EXPECTED
</div>
```

**Color Coding:**
- 🟢 **Production:** No banner (normal site)
- 🟠 **UAT:** Orange banner
- 🔴 **Development:** Red banner
- 🔵 **Local:** Blue banner (optional)

### 5. Data Management

#### **REQUIRED: Different Data Per Environment**

| Data Type | Production | UAT | Development | Local |
|-----------|-----------|-----|-------------|-------|
| **Customer PII** | Real data | NEVER - sanitized only | NEVER - test data | NEVER - mock data |
| **Products** | Real products | Real products (copy) | Subset of products | Mock products |
| **Pricing** | Real pricing | Real pricing (copy) | Test pricing | Mock pricing |
| **Orders** | Real orders | Test orders | Test orders | Mock orders |
| **User Accounts** | Real users | Test users only | Test users only | Mock users |
| **Payment Data** | Real (if applicable) | NEVER - test mode | NEVER - test mode | Mock data |

#### **Data Sanitization Requirements:**

When copying production data to UAT:
- [ ] Remove or hash all email addresses
- [ ] Remove or hash all phone numbers
- [ ] Replace customer names with fake names
- [ ] Remove payment information completely
- [ ] Remove authentication credentials (force password reset)
- [ ] Clear audit logs containing PII
- [ ] Document sanitization process

**Recommendation:** Use dedicated data sanitization tools or scripts, never manual processes.

### 6. Security Configuration

#### **REQUIRED: Environment-Specific Security Settings**

| Security Control | Production | UAT | Development |
|-----------------|-----------|-----|-------------|
| **SSL/TLS** | Required (HTTPS only) | Required | Required (can be self-signed) |
| **Security Headers** | Full set (see below) | Full set | Basic set |
| **WAF** | Required | Recommended | Optional |
| **DDoS Protection** | Required | Recommended | Optional |
| **Rate Limiting** | Strict | Moderate | Lenient |
| **Error Disclosure** | Generic messages | Generic messages | Detailed (for debugging) |
| **Debug Mode** | DISABLED | DISABLED | ENABLED (but not verbose) |
| **Source Maps** | NO | NO | YES |

#### **Required Security Headers (Production & UAT):**

```
Content-Security-Policy: default-src 'self'; script-src 'self' 'unsafe-inline' 'unsafe-eval'; style-src 'self' 'unsafe-inline';
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
Strict-Transport-Security: max-age=31536000; includeSubDomains
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: geolocation=(), microphone=(), camera=()
```

### 7. Deployment & Change Management

#### **REQUIRED: Promotion Path**

All changes MUST follow this promotion path:

```
Local Development → Development → UAT → Production
                    ↓              ↓      ↓
                    Testing     Acceptance Review & Approve
```

**Rules:**
- ✅ Code flows in one direction only (left to right)
- ❌ NEVER deploy directly to production
- ✅ ALL changes must be tested in UAT before production
- ✅ Production deployments require approval
- ✅ Rollback plan required for all production deployments

#### **Deployment Checklist:**

**UAT Deployment:**
- [ ] Code reviewed and approved
- [ ] Tests passing in development
- [ ] Database migrations tested
- [ ] Deployment runbook prepared
- [ ] Stakeholders notified

**Production Deployment:**
- [ ] UAT testing completed and signed off
- [ ] Deployment approved by authorized person
- [ ] Backup completed and verified
- [ ] Rollback plan documented and tested
- [ ] Stakeholders notified with timing
- [ ] Monitoring alerts configured
- [ ] On-call support arranged

---

## 🏗️ Architecture Patterns by Application Type

### Pattern A: Serverless Web Application (Recommended for Planners)

**Production:**
```
Route53/DNS → CloudFront CDN → S3 Static Site
                              → Lambda Functions → RDS Database
                              → API Gateway
```

**UAT:**
```
Route53/DNS → CloudFront CDN → S3 Static Site (separate bucket)
                              → Lambda Functions (separate) → RDS (separate instance)
                              → API Gateway (separate)
```

**Benefits:**
- Complete isolation
- No shared infrastructure
- Easy to tear down/rebuild
- Cost-effective (pay per use)

### Pattern B: WordPress Site (Managed Hosting)

**Production:**
```
Managed Host (WP Engine/Kinsta) Production Environment
  → WordPress Application
  → MySQL Database
  → CDN
```

**UAT:**
```
Managed Host Staging Environment (included with most platforms)
  → WordPress Application (clone of production)
  → MySQL Database (sanitized copy)
  → CDN
```

**Benefits:**
- Platform handles separation
- Built-in staging/cloning
- Self-service operations

### Pattern C: PaaS Web Application

**Production:**
```
Azure App Service Production Slot / Elastic Beanstalk Production Environment
  → Application Code
  → Azure SQL / RDS Database (production)
```

**UAT:**
```
Azure App Service Staging Slot / Elastic Beanstalk Staging Environment
  → Application Code (same version as prod candidate)
  → Azure SQL / RDS Database (separate, sanitized data)
```

**Benefits:**
- Blue/green deployment support
- Slot swapping for zero-downtime
- Environment parity

---

## ✅ Compliance Checklist

Use this checklist when creating new web properties or validating existing ones:

### Domain & DNS
- [ ] Production uses primary brand domain
- [ ] UAT uses separate staging domain
- [ ] Development uses separate dev domain
- [ ] UAT/Dev domains not indexed by search engines

### Infrastructure
- [ ] Production on dedicated infrastructure
- [ ] UAT separated from production (network/account)
- [ ] Development separated from production
- [ ] No shared databases between environments

### Access Control
- [ ] Production publicly accessible (if customer-facing)
- [ ] UAT requires authentication OR IP whitelist
- [ ] Development requires authentication OR IP whitelist
- [ ] Admin access uses 2FA/MFA

### Visual Indicators
- [ ] UAT has prominent orange banner
- [ ] Development has prominent red banner
- [ ] Banners cannot be dismissed
- [ ] Environment clearly labeled

### Data Management
- [ ] Production has real data only
- [ ] UAT has sanitized or test data (no real PII)
- [ ] Development has test data (no real PII)
- [ ] Data sanitization documented

### Security
- [ ] SSL/TLS enabled on all environments
- [ ] Security headers configured
- [ ] WAF enabled on production (and UAT if possible)
- [ ] Monitoring and alerting configured
- [ ] Debug mode disabled in production and UAT

### Deployment
- [ ] Changes promoted through Dev → UAT → Production
- [ ] Production deployments require approval
- [ ] Rollback procedures documented
- [ ] Backup before production deployment

---

## 🚫 Common Violations & Remediation

### Violation 1: UAT on Production Domain
**Example:** `planner.lugna.online/uat/`

**Risk:** High - Security incident in UAT affects production domain reputation  
**Remediation:** 
1. Create new UAT domain: `uat-planner.lugna-staging.com`
2. Deploy UAT to new domain
3. Update all references
4. Decommission old UAT path

### Violation 2: Shared Database Between Environments
**Example:** Production and UAT using same database with different table prefixes

**Risk:** Critical - Data corruption, performance impact, security breach  
**Remediation:**
1. Create new database instance for UAT
2. Copy and sanitize production data
3. Update UAT connection strings
4. Test thoroughly before decommissioning shared database

### Violation 3: No Authentication on UAT
**Example:** UAT site publicly accessible without any access control

**Risk:** High - Testing data visible to public, confusion with production  
**Remediation:**
1. Implement basic authentication immediately (htpasswd)
2. Add noindex meta tags and robots.txt
3. Plan for IP whitelist or SSO in future

### Violation 4: No Visual Indicators
**Example:** UAT looks identical to production

**Risk:** Medium - Users confused, potential use of wrong environment  
**Remediation:**
1. Add prominent banner to all UAT pages
2. Add banner to all development pages
3. Use different color schemes if possible

---

## 📚 Reference Examples

### Example 1: Lugna Planner (Target State)

| Environment | URL | Infrastructure | Access | Data |
|-------------|-----|----------------|--------|------|
| **Production** | `planner.lugna.online` | AWS Prod Account, us-east-1 | Public | Real products/pricing |
| **UAT** | `uat-planner.lugna-staging.com` | AWS Staging Account, ap-southeast-2 | Basic Auth | Sanitized data |
| **Development** | `dev-planner.lugna-dev.com` | AWS Dev Account, ap-southeast-2 | Basic Auth | Test data |
| **Local** | `localhost:3000` | Developer laptop | None | Mock data |

### Example 2: Protector Aluminium Website (Target State)

| Environment | URL | Infrastructure | Access | Data |
|-------------|-----|----------------|--------|------|
| **Production** | `protectoraluminium.com.au` | WP Engine Production | Public | Live content |
| **Staging** | `protectoraluminium.wpengine.com` | WP Engine Staging | Password | Copy of live |
| **Development** | Local WordPress install | Developer laptop | None | Test content |

---

## 🔄 Review & Exceptions

### Standards Review
- **Frequency:** Quarterly
- **Owner:** Group ICT Manager
- **Approval:** IT Strategy Governance Committee

### Exception Process

If you need an exception to these standards:

1. **Document the exception request:**
   - Which standard(s) require exception
   - Business justification
   - Risk assessment and mitigation plan
   - Duration of exception (temporary or permanent)

2. **Submit for approval:**
   - Exceptions < 90 days: Group ICT Manager approval
   - Exceptions > 90 days or permanent: IT Governance Committee approval
   - High risk exceptions: Executive approval required

3. **Monitor and review:**
   - Document exception in central register
   - Review monthly until resolved
   - Plan remediation for temporary exceptions

### Emergency Exceptions

In emergency situations (security incident, business-critical issue):
- Group ICT Manager can grant temporary 7-day exception
- Must be documented within 24 hours
- Must be reviewed by governance within 7 days
- Remediation plan required

---

## 📞 Questions & Support

**Questions about these standards:**
- Contact: Group ICT Manager
- Email: [Email]
- Slack: #it-governance

**Report a violation:**
- Email: [Security email]
- Slack: #security-incidents
- Phone: [Emergency number] (critical only)

**Request exception:**
- Submit via: [IT Service Desk / Governance portal]
- Template: environment-exception-request-template.doc

---

**Document Owner:** Group ICT Manager  
**Approved By:** IT Strategy Governance Committee (pending)  
**Effective Date:** November 2, 2025  
**Next Review:** February 1, 2026  
**Version:** 1.0

