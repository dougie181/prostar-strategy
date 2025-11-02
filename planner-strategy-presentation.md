# Customer-Facing Planners Strategy Presentation

## Slide 1: Title Slide
**Customer-Facing Planners & Calculators Strategy**
*Driving Sales and Improving Customer Experience*

Meeting Date: [Insert Date]
Attendees: [Insert Names]

---

## Slide 2: Meeting Purpose & Agenda
### Purpose
Discuss and align on our strategy for customer-facing planners and calculators to help drive sales and improve the customer experience.

### Key Questions to Answer
- What is our short-medium term strategy for planners?
- Can we define a repeatable "recipe" for consistent delivery?
- Should we focus on building new planners or fixing existing ones?

---

## Slide 3: Current Planner Portfolio Assessment
### Our Current Planners

| Planner | Market | Status | 
|---------|--------|--------|
| **Lugna 3D Planner** | AU | Functioning - although has errors or missing functionality
| **Glass Planner** | AU & NZ | Not functioning and disabled
| **Pool & Garden Fence Calculator** | AU | Functioning- although missing products & inaccurate pricing
| **Sign Planner** | AU | Functioning with limited font options
| **Wardrobe Planner** | AU | In review - addressing feedback from Bunnings

### Key Issues
- Inconsistent user experience across tools
- Different technologies and architecture (from Wordpress plugins to standalone web applications)
- Not all planners integrate with Acumatica ERP - innacurate pricing or missing products
- Analytics and conversion tracking - not really able to do this properly due to lack of integration with Bunnings
- Support and maintenance - different teams / people over time
- **🚨 SECURITY INCIDENT:** Lugna UAT site defaced, flagged by Google Safe Browsing
- **Infrastructure gaps:** No separation between Dev/UAT/Production environments
---

## Slide 4: Recommended Strategic Approach
### "Fix Before Expand" Strategy

**Phase 1: Foundation**
- Fix Glass planner (disabled → functional)
- Complete Wardrobe planner review and deployment
- Establish technical standards and governance
- Implement basic analytics across all planners

**Phase 2: Optimization (Months 12-24)**
- Build repeatable development process
- Integrate with Acumatica for real-time pricing
- Enhance user experience consistency
- Selective expansion based on ROI

**Rationale:** Align with IT strategy's "foundation first" approach

---

## Slide 6: Repeatable Development Framework
### Standardized "Recipe" for Success

#### 🎯 **Business Case Requirements**
- Target market analysis & conversion potential
- ROI projections and success metrics
- Bunnings integration implications
- Resource requirements assessment

#### 🔧 **Technical Standards**
- Consistent technology stack
- Security & compliance baseline
- Mobile-responsive design
- Analytics implementation

#### ⚙️ **Operational Framework**
- Acumatica integration for pricing/products
- Automated update processes
- Maintenance & support procedures
- Performance monitoring

#### 🛡️ **Security & Infrastructure Standards**
- Environment separation (Dev/UAT/Production isolated)
- Modern cloud-native/serverless architecture
- WAF and DDoS protection
- Automated security monitoring
- Self-service deployment capabilities

---

## Slide 6.5: Security & Infrastructure Strategy
### Lessons from Lugna UAT Incident

#### **What Happened**
- Lugna 3D planner UAT site defaced
- Google Safe Browsing flagged URL
- Customer-facing impact and brand risk

#### **Root Causes Identified**
1. **No environment separation** - Dev/UAT/Production shared domains
2. **Infrastructure co-location** - Non-prod on same servers as production
3. **Partner dependency** - Limited self-service for security response
4. **Traditional architecture** - Server-based hosting increases attack surface

#### **Strategic Response** (See Web Infrastructure & Security Strategy document)
- **Environment Isolation:** Separate domains and infrastructure
- **Serverless Migration:** Modern cloud-native architecture for planners
- **Managed Hosting:** WordPress sites to WP Engine/Kinsta
- **Self-Service Operations:** Reduced dependency on external partners

#### **Impact on Planner Strategy**
- All new planners must follow security standards
- Existing planners prioritized for infrastructure migration
- Phase 1 includes security hardening alongside functionality fixes

---

## Slide 7: Priority Assessment Matrix
### Immediate Actions Required

#### **CRITICAL Priority (Immediate)**
1. **Lugna Planner Security Incident Response**
   - Remediate compromised UAT environment
   - Separate Dev/UAT/Production environments
   - Implement security hardening measures
   - Google Safe Browsing delisting

#### **HIGH Priority (Next 90 Days)**
2. **Glass Planner** - Fix or retire decision
   - Impact: AU & NZ markets affected
   - Decision needed: Repair cost vs. rebuild vs. retire

3. **Wardrobe Planner** - Complete review process
   - Status: Under Bunnings review
   - Action: Finalize feedback incorporation and launch

#### **MEDIUM Priority (Next 6 months)**
3. **Lugna & Sign Planners** - Standardize and optimize
4. **Analytics Implementation** - Basic conversion tracking

#### **LOW Priority**
5. **Pool & Garden Calculator** - Maintain current state

---

## Slide 8: Key Considerations Analysis
### Addressing Critical Success Factors

| Consideration | Current State | Target State | Action Required |
|---------------|---------------|---------------|-----------------|
| **Functionality & UX** | Inconsistent | Standardized | UX audit & guidelines |
| **Maintenance** | Manual/Ad-hoc | Automated | Development capability |
| **Pricing Updates** | Manual | Real-time | Acumatica integration |
| **Analytics** | Limited | Comprehensive | Tracking implementation |
| **ERP Integration** | None | Seamless | Phase 1 of IT strategy |
| **Bunnings Integration** | Future goal | CSO & tracking | Year 2-3 capability |
| **Security & Infrastructure** | High risk | Cloud-native | Environment separation + serverless migration |

---

## Slide 9: Resource Strategy & Dependencies
### Alignment with IT Strategy Timeline

#### **Immediate Resources (Next 3 months)**
- **BA/PM Resource** (planned in IT strategy) for requirements analysis
- **External UX Partner** for user experience audit
- **Acumatica Partner** (already planned) for integration design
- **Cloud Infrastructure** (AWS/Azure) for secure environment separation
- **Security Services** (WAF, monitoring) for protection and incident detection

#### **Medium-term Resources (6-18 months)**
- **Internal Development Capability** (IT strategy Year 2)
- **Data Analytics Platform** (IT strategy Year 2-3)

#### **Dependencies**
✅ Acumatica optimization project (in progress)
🔄 BA/PM resource hiring (IT strategy priority)
📅 Development capability building (18-month timeline)

---

## Slide 10: Success Metrics & ROI
### How We'll Measure Success

#### **Customer Impact Metrics**
- Planner usage rates and user engagement
- Conversion from planner use to purchase
- Customer satisfaction scores
- Bunnings partnership feedback

#### **Operational Metrics**
- Time to deploy new planners
- Maintenance cost reduction
- Pricing update automation
- System reliability (uptime)

#### **Financial Metrics**
- Revenue attributable to planner-generated leads
- Cost per planner maintenance
- ROI per planner investment
- Development efficiency improvements

---

## Slide 11: Risk Assessment & Mitigation
### Key Risks & Management Strategies

#### **HIGH Risks**
- **Glass Planner Repair Costs** → *Mitigation: Cost-benefit analysis, consider rebuild*
- **Resource Allocation Conflicts** → *Mitigation: Align with IT governance priorities*

#### **MEDIUM Risks**
- **Integration Complexity** → *Mitigation: Phased approach, experienced partners*
- **Bunnings Requirements Changes** → *Mitigation: Regular stakeholder communication*

#### **LOW Risks**
- **Technology Stack Obsolescence** → *Mitigation: Modern, supported technologies*
- **User Adoption Issues** → *Mitigation: UX focus, user testing*

---

## Slide 12: Recommended Decisions
### What We Need to Decide Today

#### **Immediate Decisions (Next 30 days)**
1. ✅ **Approve "Fix Before Expand" strategy**
2. 🔧 **Glass Planner: Fix, rebuild, or retire?**
3. 📋 **Establish planner governance within IT governance framework**
4. 👥 **Assign BA/PM resource to lead planner requirements analysis**

#### **Resource Commitments**
- Budget allocation for Glass planner resolution
- Timeline for Wardrobe planner completion
- Integration with Acumatica optimization project

---

## Slide 13: Implementation Timeline
### 90-Day Action Plan

#### **Days 1-30: Assessment & Planning**
- Glass planner technical assessment and cost analysis
- Wardrobe planner feedback review and finalization
- Establish planner governance and standards
- Begin BA/PM resource requirements analysis

#### **Days 31-60: Foundation Building**
- Complete Glass planner decision (fix/rebuild/retire)
- Deploy Wardrobe planner (if approved by Bunnings)
- Implement basic analytics across functioning planners
- Define integration requirements with Acumatica team

#### **Days 61-90: Optimization & Standards**
- Begin standardization of functioning planners
- Establish technical architecture for future planners
- Create maintenance and update procedures
- Plan Phase 2 roadmap based on learnings

---

## Slide 14: Success Scenarios
### What Good Looks Like (12 months from now)

#### **Customer Experience**
- 5 fully functional, consistent planners across AU/NZ
- Seamless user experience with modern, mobile-friendly design
- Real-time pricing and product availability
- Clear conversion path to purchase

#### **Business Operations**
- Automated pricing updates from Acumatica
- Conversion tracking and ROI measurement
- Streamlined maintenance and update processes
- Foundation for Bunnings CSO integration

#### **Strategic Capability**
- Proven internal development process
- Repeatable framework for new planner development
- Data-driven decision making for planner investments
- Platform for future digital customer tools

---

## Slide 15: Next Steps & Ownership
### Actions & Accountability

#### **Immediate Actions (Next 7 days)**
| Action | Owner | Due Date |
|--------|-------|----------|
| Glass planner technical assessment | IT Team | [Date] |
| Wardrobe planner Bunnings follow-up | Sales/Product | [Date] |
| Governance framework establishment | IT Manager | [Date] |
| Resource allocation approval | Executive | [Date] |

#### **30-Day Milestones**
- Glass planner decision finalized
- Planner standards document created
- Integration roadmap with Acumatica defined
- Phase 2 planning initiated

#### **Next Review**
📅 **Follow-up meeting in 30 days** to review progress and make Phase 2 decisions

---

## Slide 16: Questions & Discussion
### Open Discussion

**Key Questions for Group Decision:**
1. Do we agree on the "Fix Before Expand" strategic approach?
2. What's our tolerance for Glass planner investment vs. retirement?
3. How should planner priorities integrate with broader IT roadmap?
4. What success metrics matter most to leadership?

**Next Steps:**
- Assign action item owners
- Confirm resource commitments
- Schedule follow-up reviews
- Align with IT governance calendar 