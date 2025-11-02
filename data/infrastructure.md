# List of infrastructure used

## On-Premises / Physical Infrastructure
1. Synology NAS - local backup and file storage

## Web Hosting & Cloud Infrastructure

### Current State (As of November 2025)
1. **SixT4 Partner Hosting** - WordPress sites and web applications
   - Status: Under review for migration
   - Issues: Limited self-service, unclear separation, possible single server
   - Sites: Multiple WordPress sites, possibly some planners

2. **Web Planners** - Various hosting (details TBC)
   - Lugna 3D Planner - planner.lugna.online (UAT compromised - security incident)
   - Wardrobe Planner - wardrobes.apps.lugna.online
   - Signs Planner - signs.apps.protectoraluminium.com.au
   - Glass Planner - DISABLED
   - Pool & Garden Calculator

### Target State (Migration in Progress)

1. **Managed WordPress Hosting**
   - Platform: WP Engine (premium sites) or Cloudways (standard sites)
   - Benefits: Self-service, automated backups, security monitoring
   - Timeline: Phase 1 migration in next 90 days

2. **Cloud Infrastructure - AWS** (Profile: default, Region: ap-southeast-2)
   - Production Account - customer-facing production workloads
   - Staging Account - UAT environments
   - Development Account - development environments
   - Use case: Serverless planners and calculators
   - Timeline: Architecture design in progress

3. **Security Services**
   - WAF: Cloudflare or AWS WAF
   - Monitoring: UptimeRobot + AWS CloudWatch
   - SSL: Let's Encrypt / AWS Certificate Manager

### Migration Status
- ⚠️ CRITICAL: Lugna planner security incident response in progress
- 📋 Planning: WordPress sites migration to managed hosting
- 🏗️ Design: Serverless architecture for planners
- 📅 Timeline: See web-infrastructure-security-strategy.md

## Network & Office Infrastructure
3. Office Network - managed by IT Support Partner
4. VPN - for remote access (details TBC)

## Security Infrastructure
5. Microsoft 365 - email, collaboration, identity
6. IT Support Partner - manages security, O365, PC setup

## Notes
- Comprehensive infrastructure modernization strategy documented in web-infrastructure-security-strategy.md
- Environment separation standards documented in environment-separation-standards.md
- Immediate actions documented in immediate-security-actions.md
