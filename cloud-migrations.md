
# Main Cloud Migration Strategies


Cloud migration options are commonly referred to as the "6 Rs" of cloud migration, 

1. Rehost
2. Re-platform
3. Refactor / Re-architecture
4. Repurchase (move to a SaaS, generally)
5. Retire
6. Retain

but arguably we could also consider two more possible strategies

7. Rebuild
8. Replace

The levels of effort, risk and cost involved in each are obviously different, which is why a practice of continuous portfolio management matters. 
 
An effective IT application portfolio management practice is essential for enterprises with large ecosystems to maintain operational efficiency, reduce costs, and support strategic decision-making. A portfolio should provide visibility into application usage, business value, and costs, in order to understand when the latter start to grow compared with the former, identify redundancies, know when to modernize legacy systems, and allocate always scarce resources strategically. Continuous portfolio management methodologies, such as [Gartner’s TIME](https://www.leanix.net/en/wiki/apm/gartner-time-model) (Tolerate, Invest, Migrate, Eliminate) model, offer structured and objective approaches to assess and categorize applications  along dimensions such as technical health, technology lifecycles, business value, strategic alignment etc. These frameworks allow enterprises to streamline their IT landscape by determining which systems to retain as-is, enhance, migrate to newer platforms, or phase out entirely. TIME is just one such tool, there are other similar tools out there, like [PACE](https://www.orbussoftware.com/docs/default-source/blogs/an-introduction-to-the-gartner-paced-layer-application-strategy-2021.pdf) (yes, also Gartner), a Horizons-based model (core, growth-oriented, emerging), the [BCG matrix](https://safetyculture.com/topics/bcg-matrix/), a heavy methodology that you can adapt, such as [TOGAF](https://www.opengroup.org/togaf), or any custom application scoring framework tailored to your own organizational goals and strategy, normally measuring things like business impact and value, user satisfaction, TCO, risk, stack obsolescence, cost effectiveness and so on. Ideally, data-driven from actual application usage and not stakeholder gut-feeling or opinions. There are vendor agnostic approaches too, such as [MoSCoW](https://community.atlassian.com/t5/App-Central-articles/Understanding-the-MoSCoW-prioritization-How-to-implement-it-into/ba-p/2463999) that can be applied to IT portfolio management. Simpler, more generalistic tools like [Impact-Effort Matrix](https://monday.com/blog/project-management/impact-effort-matrix/) or the [Kano Model](https://en.wikipedia.org/wiki/Kano_model) are also useful tools. There are endless [others](https://roadmunk.com/guides/product-prioritization-techniques-product-managers/).

I am not selling or advocating for any specific tools from the ones cited. Vendor methodologies come and go all the time, rehashed, reheated and served again to willing customers. But as a tool, they can provide useful guidance by indicating dimensions you should pay attention too, so can help guide your thinking. At the same time, many of those frameworks - especially those are not complicated to use like TOGAF - tend to the oversimplification of the world to 2x2 matrices. Use judiciously. There are entire books on the topic of IT portfolio management, so there are more details than can be captured in a simplistic matrix. 

What matters here is that you employ an objective and comprehensive methodologies for articulating and communicating decisions. Or, you adopt a Portfolio Management tool. Ultimately the idea is to have a clear objective view and understanding of the IT Portfolio, so you can decide different migration roadmaps with clear exit criteria defined. Your EA principles should direct those, in line with business strategy and goals, establishing solid governance goalposts. The roadmaps will be showing how to implement phased migration approaches, that will probably be different for different applications. 
Anyway, this article is not about this topic.

__Note__: I realize this is hardly a new thing, so I will try to explore as well the organizational ramifications for each strategy that I think should be taken into account, and not merely explain the strategies. 

## Exploring the strategies

### __Rehost (Lift and Shift)__ 
This approach involves moving applications to the cloud with minimal modifications. It's the quickest and least complicated (which does not necessarily mean simple or not time consuming) migration method, essentially transferring existing servers and applications to cloud infrastructure without changing the code. Normally this means just shifting the workload to a replica of the on-premises environment to vanilla VM-based IaaS. You could containerize those workloads, but ultimately they remain the same under the hood. This approach can be suitable for organizations with time-sensitive migration needs, limited cloud expertise, a large portfolio that precludes a comprehensive cloud journey to PaaS, or applications that don't need or require immediate optimizations. Pros include a faster migration, minimal disruption, and lower immediate transformation costs and risks. Cons include missed opportunities for cloud-native optimization, potentially higher long-term operational costs (that many VMs) due to the large IaaS footprint, and limited scalability. 

It's probably something not done massively anymore in 2024, unless you are still closing datacenters , or perhaps incorporating new pieces after an M&A deal, and it is the less mature option in a cloud journey. It can also be a trap from which it is difficult to move out later. Once you are "in the cloud", business stakeholders might be already expecting the miracles of technology to manifest, and there can be less appetite for continuing the journey towards cloud-native modernizations.

Tools like AWS Server Migration Service (SMS) or Azure Migrate can help here.

To sum up:
- Minimal immediate skill transformation needed, especially if a vendor is handholding you
- Quickest migration path, ideal if you need to meet tight deadlines to tell your stakeholders, investors etc that "you are in the cloud"
- Limited initial disruption to existing processes, which has less friction and requires less discussion and stakeholder management, but can be probably a bad thing since inefficient processes remain unchanged
- Potential for future optimization, which alternatively means limited immediate cloud-native benefits are obtained
- May introduce some sort of complacency or reluctance to move forward in the cloud journey for those applications that merit it - applications that are thus migrated tend to remain and linger in that state for too long if they seem to "just work", especially in large portfolios
- Constraints include higher long-term operational costs
- Limited immediate cloud-native benefits, which can mean missing strategic value
- Be sure to assess the long-term costs of running a large IaaS footprint.

### Re-platform (Lift, Tinker, and Shift)
A middle-ground strategy where applications are migrated with some cloud optimization but without complete redesign, think for example moving only some parts of the systems that are clear-cut and not tangled in a web of dependencies (admittedly rare, but could be the case), ancillary services, or new requirements that could be implemented as a separate piece instead of adding to the monolith you already have. This might also involve modernizing a tier to leverage some cloud capabilities, such as migrating to a managed database offering or implementing basic auto-scaling, with minor modification to your codebase, such as removing or relocating persistent user state or sessions. Or, alternative, moving only some part of the application, some clear-cut service, component or integration that is easier to carve out. A tool like [Independent Service Heuristics](https://github.com/TeamTopologies/Independent-Service-Heuristics) can be helpful here to identify candidates, as well as specific domain knowledge. 

This migration option is suitable for key parts of the portfolio where reaping cloud benefits in an incremental while removing the risk (or the impossibility) of a full re-architecture, where such a thing is not warranted. As with most of the other options, a technical feasibility assessment should be done to find out if this is the right option and how far to go with the modernization. Pros of this option include performance improvements, albeit probably moderate, some cost or operational optimization, and reduced migration complexity avoiding riskier choices. Cons include incomplete cloud-native transformation and potential ongoing performance limitations.

Presents more moderate organizational risks:
- Enables faster wins for operational improvements while postponing full transformation
- Partial skill transformation requirements, depending on how far it goes
- Potential performance inconsistencies
- Could require the ability to develop different parts of the system with lifecycles that move at different paces (IT Speeds etc), which could lead to problems later on
- Requires more diversity of skills in teams, but that will generally be a good thing
- Incremental changes may not deliver expected benefits, or present too many issues and technical problems down the road
- Risk of creating hybrid environments that are harder to manage (operations, skills, as mentioned)
- Incomplete leverage of cloud capabilities
- As with the previous approach, this one too risks perpetuating legacy issues in partially modernized systems that never fully modernize
- Inherent increased complexity of distributed systems

### Refactor/Re-architecture
A comprehensive transformation where applications are significantly redesigned to fully leverage cloud-native architectures, typically involving microservices, containerization, and serverless technologies. Best for mission-critical applications where performance, scalability, and innovation are paramount. Pros include maximum cloud efficiency, enhanced performance, improved scalability, and future-proofing. Cons include high complexity, substantial time investment, significant expertise requirements, and potentially high transformation costs and risks.

A close second in risk profile, with critical organizational challenges:
- Requires extensive retraining of existing development teams, including building more sophisticated skills like domain-driven design (DDD) for effective decomposition of legacy applications (or you need to resort to specialized consulting)
- Substantial cultural resistance to fundamental architectural changes
- High likelihood of introducing new technical debt while attempting to eliminate old debt - seen this happening a few times in spites of continuous assurances and promises (incidentally this is not specific to the cloud per se)
- Complexity of managing parallel systems during migration
- Risk of Reengineering 
- Potential outages or performance degradation during transition
- Significant investment in new tooling and development practices
- Two sides of the same coin: better possibilities of incorporating newer technologies at the risk of over-engineering solutions
- Requires robust governance to prevent scope/feature creep and ensure alignment with business goals (the "since you are already working on this application" syndrome)
- Can lead to just containerizing big applications that suffer no modification to their architecture and thus you end running huge pods that are just VM's in disguise

### Repurchase (Replace with SaaS)
Replacing existing on-premises or custom applications with COTS or commercial Software-as-a-Service (SaaS) solutions. Ideal for non-core, non-differentiating standardized business functions like Field Services, CRM, HR, Marketing & Communications where specialized cloud solutions exist. Pros include immediate cloud benefits, reduced maintenance overhead, automatic updates, and typically lower total cost of ownership. Cons include potential loss of customization, vendor lock-in, and possible data migration challenges when moving out of your silos and proprietary custom solutions. Political issues might arise with stakeholders clinging to their beloved applications (and the budget that goes with them), so perhaps the main risks with this strategy fall in the organizational category:

- Vendor lock-in challenges, often for the long term, but that's life
- Data migration and integration complexities - there will have to be integration projects depending on this migration, which requires a full [api-first mindset](https://swagger.io/resources/articles/adopting-an-api-first-approach/) first
- Potential misalignment between SaaS capabilities and specific business processes (you are guaranteed to have many complains here as people protect their turfs, aka job security and org chart relevance)
- User adoption and change management difficulties
- Hidden costs of customization and integration - which often happens with the siren song the implementing vendor will no doubt offer
- Loss of unique competitive advantages embedded in custom solutions - albeit in theory you can have a strategy and build an ecosystem of enhanced services or competitive advantages on top of a COTS product, and this is only a maybe, since you could be repurchasing some system that is not really a core differentiator and more of a standard function everyone already has 
- Evaluate your SaaS adoption with longer term business strategies and consider vendor-related risks

### Retire 
Decommissioning applications that are no longer necessary or valuable to the business. This strategy involves identifying and eliminating redundant, obsolete, or inefficient applications during the migration process. Beneficial for organizations looking to streamline their IT portfolio, reduce maintenance costs, and simplify their infrastructure. It is probably the lowest effort option, but some things still need to be attended to, such as migrating or phasing-out customers or users, what to do with data and identify any hidden or forgotten dependency. So, basically, an impact assessment. 
Pros include reduced complexity, lower operational costs, and improved security by eliminating unnecessary systems. Cons might include potential disruption to business processes and the need for careful impact assessment.

Lowest organizational risk:
- Simplifies IT portfolio and frees up IT resources
- Reduces maintenance overhead
- Potential cost savings
- Risks include potential loss of legacy functionality, especially if there are dark corners of undocumented functionality that no one knows anymore about and that could impact workflows in legacy systems with low utilization. Apply the "pull the plug and listen for the shouting and swearing" principle (aka perform impact assessment)
- Again, there might be some people clinging to those systems for justification

### Retain
Keeping certain applications in their current environment, either due to compliance requirements, recent upgrades, or technical constraints. This might involve postponing migration or maintaining a hybrid infrastructure. Perhaps it is not worthy, not feasible or sunset is expected to happen soon (although I've seen systems that have survived their roadmapped decommissions for years). Appropriate for highly specialized applications, those with complex dependencies (think Team Topologies' [complicated subsystems](https://teamtopologies.com/key-concepts) and beyond), systems with recent significant investments, or situation where risk, cost and timelines are too high (let the next C*O eat that one). Technology availability could eventually become a killer, though. Pros include minimal immediate disruption and preservation of recent technology investments - or even further amortization. Cons include missed cloud benefits, potential increased complexity in managing hybrid environments, and potential long-term inefficiencies.

Low organizational risk, with some caveats:
- Preserves existing infrastructure and knowledge
- Minimal immediate disruption, but inefficiencies are kept as-is
- Allows for strategic planning - but also for kicking the ball forward and postponing decisions
- Potential constraints include mounting technical debt
- Increasing maintenance costs
- Reduced competitive agility
- Put in place ongoing monitoring to evaluate when retained applications might become migration candidates
- Keep an eye on possible growing operational costs
- Requires management of threatened stakeholders and their turfs, evaluate that and have a communication strategy ready and a clean way forward, or out, for those stakeholders
- Some sort of eventual way out must be in place ... eventually

### Rebuild
A comprehensive strategy involving complete application reconstruction using cloud-native technologies and modern development approaches. Most suitable for legacy applications that are fundamentally incompatible with cloud environments or require complete modernization. Pros include maximum technological flexibility, opportunity to incorporate latest architectural patterns, and potential for significant performance improvements. Cons include extremely high transformation costs, extended development timelines, and substantial organizational disruption. 
This strategy carries the highest organizational risk due to its comprehensive nature. This strategy carries the highest organizational risk due to its ambitious and comprehensive nature, so [beware](https://www.linkedin.com/pulse/why-do-organizations-continue-fall-big-bang-rewrite-antonio-elena-0dnff).

- Massive skill gap between existing "legacy IT teams" and cloud-native technologies team, which can potentially introduce serious issues between the lifers and those hip trendy new hires
- Underestimation of complexity in complete application reconstruction, which will invariably happen and I will explore in a future article
- Significant budget overruns, often 2-3x initial estimates - and missed deadlines - as per the previous point 
- Prolonged development cycles leading to business functionality gaps, or forces a classic two-pronged approach where the legacy systems still acquires new functionality downstream from the new one, or even bidirectionally between old and new (features, fixes). What could go wrong?
- The previous point tend to happen as timelines that are inevitably extended will reduce stakeholder patience and support (or their ability or appetite for forking out some more budget) for the project
- Potential loss of institutional knowledge during complete rewrite - poor team management could mean you lose key knowledge mid-air
- High probability of scope creep and endless refinement cycles
- Risk of creating more complex systems than the original application was, because of creep, new bugs created on top of the ones who were ported to the new system from the original, because there will be pressure to cut corners, "reuse" code and not change the processes too much
- Nice opportunity to score some ESG points with your audience & investors and introduce green computing practices and a more sustainable or leaner architecture and cloud offerings
- Requires focus on change management, communication and phased development to maintain organizational confidence and drive
- Inherent increased complexity of distributed systems

### Replace
Involves substituting existing applications with entirely new solutions that better meet business requirements. This might mean changing vendors or developing new custom applications (not the same as rebuild) that are more aligned with current business needs. Ideal for scenarios where existing applications are severely limited or where business processes have significantly evolved. Pros include opportunity for radical improvement, potential cost savings, alignment with current business strategies and breaking up with ballast from the past when justified. Cons include potential high initial investment, risk of business disruption, and challenges in data migration and user adaptation. Data migration, user training, and change management are things you will also need to consider here, as in the other strategies too. 

- Opportunity for a strategic pivot to adopt modern best practices, technically and even organizationally
- High likelihood of disruptions in entrenched processes & constituencies
- Needs leadership alignment and transparent communication to manage resistance and smooth transition

## How to implement an encompassing cloud migration strategy
To successfully navigate these migration approaches, organizations should:

1. Develop a robust cloud & architecture competency centers
2. Invest heavily in continuous skills training
3. Create detailed migration roadmaps with clear exit criteria and milestones
4. Implement phased migration approaches
5. Establish strong governance and (possibly) architectural review boards, although I have mixed feelings about those for their obvious limitations in knowledge and reach. I guess it depends on the type of organization and its maturity levels. 
6. Develop comprehensive change management programs
7. Create fallback and rollback mechanisms
8. Maintain open communication channels across IT and business units
9. Have KPIs and metrics in order to build data-driven decision making as opposed to opinions, intuition and hand-waving 

In all cases, a viewpoint beyond the immediate and the tactical is needed in order to:

__Consider Emerging Complexity Factors__
- Increasing regulatory compliance requirements, something which is clear in the EU with its love for bureaucracy and intervention, as well as with sustainability and other similar trends
- Multi-cloud and hybrid cloud environments
- Where technological evolution is heading
- Increasing complexity of distributed systems (operations, monitoring and observability, reliability etc)

__Build Key Organizational Capabilities for Successful Migration__:
- Strategic technological vision
- Cloud architecture expertise
- API-first and product vs project mindset
- Continuous learning culture
- Financial flexibility
- Strong change management practices
- Cross-functional collaboration
- Risk management maturity

Recommendation: Most organizations should start with Rehost or Re-Platform strategies to build cloud migration experience, then progressively move to more complex strategies like Refactor or Rebuild as organizational cloud maturity increases.


## A note on Cloud Repatriation:
We've discussed moving to the cloud, but sometimes the reverse trip could be necessary. So-called [Cloud Repatriation](https://www.puppet.com/blog/cloud-repatriation) / Edge retention has gained some recent attention due to [some famous articles](https://basecamp.com/cloud-exit). This approach involves either deliberately choosing to maintain on-premises infrastructure or [moving workloads back](https://www.eetimes.eu/cloud-repatriation-on-the-rise-83-of-cios-plan-workload-shifts-in-2024/) from public cloud environments to private data centers or edge computing infrastructure. It's a strategic counterpoint to the widespread cloud migration narrative, acknowledging that cloud isn't always the optimal solution for every technological context.

__Organizational Scenarios of Applicability__
Ideal candidates for this strategy include organizations with specific regulatory constraints, high-performance computing requirements, predictable and stable workloads, sensitive data processing needs, or those experiencing unexpectedly high public cloud operational costs. Industries like financial services, healthcare, government, scientific research, and certain manufacturing sectors often find compelling reasons to retain or repatriate infrastructure.


__Pros__:
- Complete control over infrastructure and data sovereignty - there are many ways to build mixed / hybrid architectures where some relevant data resides on-premises while you still run other workloads in the cloud and use on-prem gateways to connect the two worlds. This model applies as well to the Re-platform model where some parts or data can remain on-prem while other parts of the system move to the cloud, complexity notwithstanding.
- Predictable, potentially lower long-term operational costs - at least you are reducing your exposure to unilateral prices / licenses increases in exchange for not offloading that much responsibility to the vendor
- Elimination of cloud vendor dependencies
- Precise performance tuning capabilities
- No recurring cloud service expenses
- Compliance with strict regulatory environments
- Reduced network latency for specific compute-intensive applications
- Full customization of hardware and network configurations, but slower provisioning of new infrastructure for which lifecycle now you have to be responsible
- Open to debate whether the security for sensitive workloads stands in a repatriation effort

__Cons__:
- Significant upfront capital expenditure
- Requires sophisticated internal IT infrastructure expertise
- Ongoing maintenance and refresh responsibilities
- Limited scalability compared to cloud elasticity
- Higher costs for disaster recovery and redundancy
- Increased complexity in managing hardware lifecycle
- Reduced access to cutting-edge cloud-native services
- Manual scaling and capacity planning
- Higher energy and cooling infrastructure investments


### Organizational Constraints and Challenges for Repatriation

__Skill Set Requirements__
- Demands specialized infrastructure engineering talent
- Requires continuous training, but just like mostly everything else today (think AI for non-IT employees)
- Needs comprehensive understanding of capacity planning
- Demands advanced networking and security expertise
- Forgotten skills like Hardware in general

__Financial Considerations__
- You will face initial and ongoing capital and staff expenditures
- Complex total cost of ownership calculations - Read the "Pricing Granularity" section in the [Wardley Maps](https://learnwardleymapping.com/book/) book for a good exploration of this topic
- Need for precise workload forecasting, for cost reasons too
- Investment in redundancy and disaster recovery infrastructure

__Technological Constraints__
- Limited access to rapid technological innovation - only mature and tech-savvy engineering organizations will be able keep up the pace
- Management of hardware refresh cycles
- Reduced flexibility in scaling computational resources
- Higher complexity in distributed computing scenarios

__Operational Challenges__
- 24/7 infrastructure management responsibilities, SLAs, SLOs, Observability etc
- Complex compliance and security maintenance, no offloading responsibilities
- Higher overhead for monitoring and maintenance
- Limited global distribution capabilities, or at least more difficult

__Performance and Scalability Limitations__
- Fixed computational capacity, although admittedly this is a problem with the cloud, not because of the cloud itself, but because of the applications we move to the cloud and the state they're in, where scalability was hardly a design consideration back then and the only way to scale was up. It can be a different story if you build cloud-native but repatriated from scratch.
- Manual resource allocation unless you are able to build a good level of managed automated scalability
- Potential underutilization during low-demand periods
- Increased complexity in dynamic workload management

__Risk Mitigation Strategies for Repatriation__
- Implement hybrid infrastructure approaches where possible, or how you will approach redundancy depending on criticality (perhaps if it isn't critical you don't need to consider repatriation)
- Create flexible, modular infrastructure designs so you can replace pieces or move selected parts to the cloud later on if context changes (or your mind does)
- You still need to invest in advanced monitoring and optimization tools
- Maintain continuous skills development programs - but that is the same with the cloud, basically
- Develop robust disaster recovery and business continuity plans, including effective management of things like backups and their storage


### Decision Criteria for Repatriation

Consider the below if you are thinking Repatriation. Examine what other companies have done, how (full, degrees of hybrid) and especially why and what was their context. Yours will be different. And theirs may have changed since. 

- Consistent, predictable workload characteristics
- Regulatory compliance requirements
- High-performance computing needs
- Sensitive data processing
- Cost-effectiveness analysis
- Strategic technological independence
- Foresee customization requirements
- Calculate long-term total cost of ownership and associated costs


Cloud repatriation represents a mature technological strategy that recognizes no single infrastructure approach fits all scenarios. It's a nuanced response to the simplified one-size-fits-all cloud migration narrative based on data and contextual technological decision-making. The most sophisticated organizations view infrastructure as a strategic portfolio, dynamically balancing cloud, on-premises, and edge computing based on specific workload characteristics and organizational objectives.
