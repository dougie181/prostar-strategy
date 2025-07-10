# 📄 IT Strategy Document

## 🟢 Executive Summary

### 💬 Clarifying Questions
- What is the overall business vision and top strategic objectives for the next 3-5 years?
- What is the role you want IT to play in enabling this vision?
- Who is the primary audience for this strategy document (Board, Executive team, IT department, all of them)?

### ✍️ Your Answers
**Business Vision & Strategic Objectives:**
Our organization provides aluminum and cabinet-related products to Bunnings, with 80% of products manufactured and sourced from China, shipped via 3PLs, and delivered to Bunnings stores across Australia and NZ. We also manufacture custom aluminum and cabinetry for bespoke customer requirements. Our core business challenges are optimizing systems to ensure on-time delivery of quality products while scaling to meet customer demands and growth.

**Key Business Strategic Objectives (3-5 years):**
1. Develop a cost-effective software delivery process for both customer and internal client tools
2. Continue supporting Acumatica investment across Sales, Manufacturing, Inventory, Warehouse Management, and Finance, with best-of-breed integrations
3. Provide first-class IT Support with comprehensive incident, problem, and change management tools
4. Develop robust Business Analysis and project management skills and capabilities for effective business outcomes
5. Provide mechanisms for better reporting, target setting, and trend management (operational and tactical)

**IT's Strategic Role:**
IT will function as both a strategic enabler and business partner (not a cost center), investing in technology that provides competitive advantages while actively driving measurable business outcomes. This hybrid positioning supports our need to scale operations, optimize delivery performance, and handle complex manufacturing/supply chain operations.

**Primary Audience:**
Executive leadership team who will approve and fund this strategic plan.

### 💡 Draft Content
---

## 🎯 Business Drivers & Objectives

### 💬 Clarifying Questions
- What are the main business drivers (growth, efficiency, compliance, customer experience)?
- What specific business objectives should IT directly support?
- Are there new markets, products, or operational changes expected?

### ✍️ Your Answers
**Main Business Drivers:**
- **Customer Experience:** Maintaining and improving delivery performance to Bunnings (on-time, quality products)
- **Operational Efficiency:** Optimizing complex international supply chain (China sourcing → 3PL → Bunnings stores)
- **Growth & Scalability:** Building systems capable of scaling to meet increasing customer demands
- **Operational Excellence:** Streamlining manufacturing processes for both standard products and custom orders

**Specific Business Objectives IT Must Support:**
- **Supply Chain Visibility:** Complete tracking from China-sourced products through 3PL delivery to final Bunnings stores
- **Manufacturing Optimization:** Better visibility and control of manufacturing performance metrics and processes
- **Custom Order Management:** Seamless handling of bespoke items (raked aluminum panels, sliding doors, glass panels)
- **Inventory Intelligence:** Effective management of Ready-to-Assemble parent/child relationships for accurate picking and delivery
- **Purchasing Efficiency:** Streamlined purchasing processes eliminating manual workarounds across multiple systems
- **Data-Driven Decision Making:** Real-time dashboards and trend analysis for operational and tactical management

**Operational Changes Expected:**
- Continued growth in Bunnings business requiring scalable systems
- Increasing complexity in custom manufacturing requirements
- Need for more automated and integrated business processes
- Enhanced reporting and analytics capabilities for performance management

### 💡 Draft Content
---

## 🏗️ Current State ("As-Is")

### 💬 Clarifying Questions
- What are the key current IT capabilities, systems, and limitations?
- What strengths and weaknesses have been identified?
- What major risks, technical debts, or skill gaps exist?

### ✍️ Your Answers
**Current IT Capabilities & Systems:**
- **ERP Foundation:** Acumatica implemented 2 years ago covering Sales, Manufacturing, Inventory, Warehouse Management, and Finance
- **Team Structure:** Group ICT Manager + 2 Operational Support people for ERP + Strategic IT Support Partner managing O365, PC Setup, Network, and Security (includes onsite person at HQ + 1 day/week at remote office)
- **Support Systems:** FreshService for Acumatica support and problem management
- **Integration:** The Order Exchange (TOE) EDI for Bunnings orders, 3PL shipments, and invoicing
- **Additional Systems:** Netstock (purchasing - finished products only), Excel spreadsheets (purchasing), Velixio (data extraction), ELMO (HR/payroll), HUMAND (workplace communication), Telstra Calling for Office (telephony), DocuSign, Adobe Creative Suite

**Current Strengths:**
- Solid operational IT support through partner arrangement
- Established ERP foundation with Acumatica
- Automated EDI connection with key customer (Bunnings)
- Good coverage of core business functions (Finance, HR, Communication)

**Current Weaknesses & Limitations:**
- **Acumatica Issues:** Configuration problems, poor reporting for manufacturing metrics, disjointed processes
- **Order Tracking Gaps:** Custom Special Orders and Ready-to-Assemble parent/child relationships not properly tracked
- **Purchasing Inefficiencies:** Manual processes across 3 systems (Netstock limitations for manufacturing materials)
- **EDI Reliability:** TOE has regular outages and subpar support
- **Missing Capabilities:** No software development capability, no dedicated BA/PM resources, no production scheduling system

**Major Risks, Technical Debts & Skill Gaps:**
- **Business Risk:** Acumatica performance issues affecting core business operations after 2-year investment
- **Single Points of Failure:** Heavy dependence on TOE EDI with reliability issues
- **Capability Gaps:** No internal development capability, limited BA/PM skills, no formal IT governance framework
- **Technical Debt:** Acumatica configuration issues requiring significant rework
- **Process Risk:** Manual workarounds creating potential for errors and inefficiencies

### 💡 Draft Content
---

## 🚀 Future State Vision ("To-Be")

### 💬 Clarifying Questions
- What is your ideal future state for IT in 3-5 years?
- Are there specific technologies or capabilities to adopt (cloud-first, AI analytics, etc.)?
- How do you envision IT's operating model evolving (centralized, federated, hybrid)?

### ✍️ Your Answers
**Ideal Future State (3-5 years):**
- **Optimized ERP Foundation:** Acumatica fully configured and performing effectively with proper governance for prioritization and change management
- **Strategic IT Capabilities:** In-house software development capability with external partnerships for specialized needs
- **Advanced Analytics:** Data warehouse with time series data enabling real-time dashboards on TV screens and simplified management reporting with trend analysis and business ratios
- **Integrated Operations:** Seamless integration between Acumatica and best-of-breed solutions for production scheduling, manufacturing materials purchasing, and other specialized functions
- **Reliable EDI:** Either improved TOE solution or alternative EDI platform ensuring reliable Bunnings connectivity
- **Professional IT Delivery:** Dedicated BA/PM capabilities ensuring effective project outcomes and business value delivery

**Key Technologies & Capabilities to Adopt:**
- **Data Warehouse & Analytics:** Centralized data repository with time series capabilities for operational dashboards and management reporting
- **Production Scheduling Solution:** Best-of-breed scheduling system integrated with Acumatica
- **Manufacturing Materials Purchasing:** System to handle manufacturing materials (complementing Netstock's finished goods focus)
- **Development Platform:** Internal capability for custom integrations and business applications
- **Business Intelligence:** Advanced reporting and analytics beyond standard Acumatica capabilities

**IT Operating Model Evolution:**
- **Core Team:** Maintain lean internal team for Level 1 support and strategic oversight
- **Hybrid Partnerships:** Level 2 support and customizations through Acumatica partners, development projects through strategic technology partners
- **Governance-Driven:** Monthly governance group meetings to confirm priorities and manage change
- **Business-Partnered:** IT actively participating in business planning and driving measurable outcomes

### 💡 Draft Content
---

## ⚡ Strategic Priorities

### 💬 Clarifying Questions
- What are the top priorities in the short (1 year), medium (2-3 years), and long term (3-5 years)?
- Are there mandatory or compliance-driven projects?
- Which priorities deliver the most business value?

### ✍️ Your Answers
**Short Term Priorities (Next 12 months) - Foundation Setting:**
1. **Acumatica Optimization** *(Highest Priority)*
   - Fix Custom Special Order tracking issues
   - Resolve Ready-to-Assemble parent/child relationship problems
   - Improve manufacturing performance metrics and reporting
   - Address purchasing workflow inefficiencies
   - Implement proper change governance processes

2. **IT Governance Framework Implementation**
   - Establish monthly governance group for priority setting and change management
   - Implement structured decision-making processes
   - Create IT service catalog and SLA framework

3. **BA/Project Management Capability Building**
   - Hire dedicated BA/PM resource OR train existing ERP support person with backfill
   - Establish project delivery methodology and standards

**Medium-Term Priorities (Years 2-3) - Capability Building:**
1. **Software Development Capability** *(Nearly Equal Priority)*
   - Build internal development team
   - Establish development partnerships for specialized needs
   - Create custom integration and application development capability

2. **Data Warehouse & Analytics Platform** *(Nearly Equal Priority)*
   - Implement centralized data repository with time series capabilities
   - Deploy real-time operational dashboards
   - Create advanced management reporting with trend analysis

3. **Best-of-Breed Integrations**
   - Production scheduling solution selection and implementation
   - Manufacturing materials purchasing system (to complement Netstock)
   - Integration platform for seamless data flow

**Long-Term Priorities (Years 3-5) - Optimization & Innovation:**
1. **EDI Platform Evolution**
   - Evaluate TOE replacement options vs. improvements
   - Implement alternative EDI solution if required
   - Enhance Bunnings integration reliability

2. **Advanced Automation**
   - Automated business process workflows
   - Enhanced integration capabilities
   - Predictive analytics and business intelligence

**Business Value Delivery Focus:**
- Primary value driver: Acumatica optimization (enables all other initiatives)
- Equal secondary drivers: Development capability + Data analytics (multiplier effect)
- All priorities focused on scalability, operational efficiency, and customer satisfaction

### 💡 Draft Content
---

## 🗺️ Initiatives & Roadmap

### 💬 Clarifying Questions
- What major initiatives are required to close the gap from as-is to to-be?
- What is the expected timeline and budget constraints?
- Are there dependencies or key milestones?

### ✍️ Your Answers
**Major Initiatives to Close Gap:**

**Initiative 1: Acumatica Foundation Stabilization (Months 1-12)**
- Establish Acumatica governance committee and priority framework
- Engage Acumatica partner for Level 2 support and configuration optimization
- Fix critical order tracking issues (Custom Orders, Ready-to-Assemble products)
- Improve manufacturing reporting and performance metrics
- Streamline purchasing workflows and reduce manual processes
- Dependencies: Governance framework, partner selection, business process documentation

**Initiative 2: IT Capability Development (Months 6-18)**
- Recruit or train dedicated BA/PM resource
- Establish project delivery methodology and standards
- Begin building internal software development capability
- Create IT service catalog and SLA framework
- Dependencies: Budget approval, resource availability, governance processes

**Initiative 3: Data & Analytics Platform (Months 12-30)**
- Design and implement data warehouse architecture
- Develop real-time operational dashboards
- Create management reporting with trend analysis capabilities
- Integrate multiple data sources (Acumatica, TOE, Netstock, etc.)
- Dependencies: Acumatica stabilization, development capability, data strategy definition

**Initiative 4: Best-of-Breed Integration Program (Months 18-36)**
- Production scheduling solution selection and implementation
- Manufacturing materials purchasing system evaluation and deployment
- Integration platform implementation for seamless data flow
- Process automation and workflow optimization
- Dependencies: Development capability, data platform, business requirements definition

**Initiative 5: EDI Platform Enhancement (Months 30-48)**
- Evaluate TOE alternatives vs. improvement options
- Implement enhanced or replacement EDI solution
- Improve Bunnings integration reliability and performance
- Dependencies: Business case analysis, integration platform, development capability

**Timeline & Budget Approach:**
- Budget driven by positive ROI cases presented to executive leadership
- Phased approach allowing for learning and adaptation
- Resource allocation focused on building internal capability with strategic external partnerships
- Regular milestone reviews and priority adjustments through governance framework

**Key Dependencies & Milestones:**
- Month 3: Governance framework operational
- Month 6: BA/PM capability in place
- Month 12: Acumatica core issues resolved
- Month 18: Development capability operational
- Month 24: Data warehouse foundation complete
- Month 30: First best-of-breed integrations live
- Month 36: Advanced analytics and reporting operational

### 💡 Draft Content
---

## 🛡️ Risk Management

### 💬 Clarifying Questions
- What are the most critical risks to delivering this strategy?
- What mitigation actions are planned?
- What is the risk appetite defined by leadership?

### ✍️ Your Answers
**Most Critical Risks to Strategy Delivery:**

**Risk 1: Acumatica Investment Protection (HIGH)**
- *Risk:* Failure to optimize Acumatica could result in sunk costs and business disruption after 2-year investment
- *Impact:* Loss of ERP foundation, significant re-implementation costs, operational disruption
- *Mitigation:* 
  - Establish clear governance and priority framework for Acumatica improvements
  - Engage specialized Acumatica partner for Level 2 support and configuration optimization
  - Phase improvements with quick wins to build confidence and momentum
  - Regular milestone reviews with clear success criteria

**Risk 2: Capability Building Execution (MEDIUM-HIGH)**
- *Risk:* Inability to attract or develop required BA/PM and development capabilities internally
- *Impact:* Delayed project delivery, continued dependence on external resources, limited strategic flexibility
- *Mitigation:*
  - Dual strategy: recruitment AND training of existing staff with backfill plans
  - Establish strategic partnerships as backup for capability gaps
  - Phased capability building with external support during transition
  - Competitive compensation and development opportunities for retention

**Risk 3: TOE EDI Dependency (MEDIUM)**
- *Risk:* Continued outages and poor support from TOE disrupting Bunnings operations
- *Impact:* Customer relationship damage, operational disruption, manual workaround costs
- *Mitigation:*
  - Develop contingency plans for TOE outages
  - Evaluate alternative EDI solutions as part of long-term strategy
  - Strengthen relationships with key TOE personnel
  - Create backup communication channels with Bunnings and 3PLs

**Risk 4: Scope Creep and Priority Dilution (MEDIUM)**
- *Risk:* Attempting too many initiatives simultaneously without proper governance
- *Impact:* Resource spread thin, delayed delivery, incomplete implementations
- *Mitigation:*
  - Strong governance framework with monthly priority reviews
  - Clear success criteria and milestone-based approvals
  - Focus on Acumatica optimization before expanding scope
  - Regular ROI validation for new initiatives

**Risk 5: Integration Complexity (MEDIUM)**
- *Risk:* Underestimating complexity of integrating multiple systems and data sources
- *Impact:* Cost overruns, delayed implementations, system instability
- *Mitigation:*
  - Start with simple integrations and build complexity gradually
  - Invest in proper integration platform and architecture
  - Use experienced integration partners for complex implementations
  - Thorough testing and rollback procedures

**Risk Appetite:**
- **Conservative approach** to protecting existing Acumatica investment
- **Moderate appetite** for new technology investments with clear ROI
- **Low tolerance** for business disruption during implementations
- **High confidence requirement** in vendor/partner capabilities before engagement

### 💡 Draft Content
---

## 📊 Governance & KPIs

### 💬 Clarifying Questions
- What governance structures will oversee the strategy?
- How will progress be measured?
- What is the cadence for reporting and review?

### ✍️ Your Answers
**Governance Structures:**

**IT Strategy Governance Committee**
- **Composition:** Executive leadership (CEO/CFO/Operations Director), Group ICT Manager, key business stakeholders
- **Responsibility:** Strategic direction, budget approval, priority setting, major decision making
- **Frequency:** Quarterly reviews with monthly updates during critical phases

**IT Operational Governance Group**
- **Composition:** Group ICT Manager, Department heads, key end-users, selected external partners
- **Responsibility:** Tactical priority setting, change management, operational issue resolution
- **Frequency:** Monthly meetings with bi-weekly reviews during active project phases

**Project Governance**
- **Structure:** Dedicated BA/PM resource leading project delivery with clear escalation paths
- **Methodology:** Structured project approach with defined phases, milestones, and success criteria
- **Reporting:** Regular status updates to both governance committees

**Progress Measurement KPIs:**

**Strategic Success Metrics:**
- **Acumatica Optimization:** Custom Order tracking accuracy (target: >98%), Ready-to-Assemble processing time reduction (target: 50%), Manufacturing metrics availability (target: 100%)
- **Capability Building:** BA/PM resource in place and productive (target: Month 6), Development capability operational (target: Month 18)
- **Data & Analytics:** Real-time dashboard deployment (target: Month 24), Management reporting automation (target: 75% reduction in manual reporting)

**Operational Excellence KPIs:**
- **System Reliability:** ERP uptime (target: >99.5%), EDI transaction success rate (target: >99%)
- **Process Efficiency:** Purchasing workflow time reduction (target: 40%), Manual workaround elimination (target: 80% reduction)
- **Customer Impact:** On-time delivery performance to Bunnings (maintain >95%), Customer complaint reduction related to order issues (target: 50% reduction)

**Financial Performance Indicators:**
- **ROI Achievement:** Positive ROI on each major initiative within 18 months of implementation
- **Cost Management:** IT operational costs as percentage of revenue (target: maintain or reduce current levels)
- **Investment Tracking:** Actual vs. budgeted costs for each initiative (target: <10% variance)

**Reporting & Review Cadence:**
- **Monthly:** Operational governance group meetings with KPI dashboard reviews
- **Quarterly:** Strategic governance committee with comprehensive progress reports and budget reviews
- **Ad-hoc:** Issue escalation and critical decision points
- **Annual:** Complete strategy review and adjustment for following year

**Decision-Making Framework:**
- **ROI-based approval process** for all significant investments
- **Clear escalation paths** for issues and decisions
- **Regular priority reassessment** based on business needs and performance
- **Structured change management** for scope or timeline adjustments

### 💡 Draft Content
---

## ✅ Assumptions & Next Steps

### ✍️ Assumptions Made During Strategy Development

**Business Assumptions:**
- Continued growth and partnership with Bunnings as primary customer
- Existing Acumatica investment will be protected rather than replaced
- Business appetite for ROI-driven IT investments with clear business cases
- 150-person organization size and complexity levels remain relatively stable
- China sourcing and 3PL distribution model continues as primary operational approach

**Technology Assumptions:**
- Acumatica configuration issues are resolvable with proper expertise and governance
- Hybrid in-house/external partner model is financially and operationally viable
- Data warehouse and analytics technology is mature enough for reliable implementation
- Integration complexity can be managed through phased approach and proper architecture
- TOE EDI issues can be mitigated through alternatives or improvements

**Resource Assumptions:**
- Executive leadership commitment to IT as strategic enabler and business partner
- Budget availability for positive ROI initiatives as presented
- Ability to recruit or develop required BA/PM and development capabilities
- Current IT support partner relationship remains stable and effective
- Dedicated governance time commitment from business stakeholders

**Timeline Assumptions:**
- 12-month timeframe for Acumatica stabilization is achievable with proper focus
- 18-month timeline for building internal development capability is realistic
- Business processes can accommodate phased implementations without major disruption
- External partner availability and capability as required

### 🚀 Immediate Next Steps (Next 30-90 Days)

**Immediate Actions (Next 30 Days):**
1. **Executive Approval:** Present IT strategy to executive leadership for approval and budget commitment
2. **Governance Establishment:** Form IT Strategy Governance Committee and schedule first meeting
3. **Partner Engagement:** Begin evaluation and selection of specialized Acumatica partner for Level 2 support
4. **Priority Documentation:** Document and validate Acumatica issue priorities with business stakeholders

**Short-Term Actions (Next 60-90 Days):**
1. **BA/PM Resource:** Begin recruitment process or training program for BA/PM capability
2. **Acumatica Partner Selection:** Complete partner evaluation and establish support engagement
3. **Governance Framework:** Implement monthly operational governance meetings and processes
4. **Quick Wins:** Identify and implement immediate Acumatica improvements to build momentum

**Foundation Setting (Next 90 Days):**
1. **Project Methodology:** Establish project delivery standards and procedures
2. **KPI Baseline:** Document current performance metrics for future comparison
3. **Vendor Relationships:** Begin preliminary discussions with potential development and analytics partners
4. **Strategy Communication:** Share approved strategy with broader organization and stakeholders

This strategy document should be reviewed quarterly and updated annually to ensure continued alignment with business objectives and technology evolution.