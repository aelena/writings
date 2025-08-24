Had you heard of Dickerson’s Hierarchy of Reliability? This hashtag#SRE framework structures reliability practices into layers — from foundational resilient architecture to product-level reliability — providing both a map and a diagnostic tools building reliable systems and the organizational capabilities necessary to support them. I have no magic recipes to offer, but if this is new to you, I hope you find it as thought-provoking as I did.

[On LinkedIn](https://www.linkedin.com/pulse/dickersons-hierarchy-reliability-antonio-elena-rxk7f/?trackingId=CQa1kR8pBrUl5mCs9GfyEw%3D%3D)

# Dickerson's Hierarchy of Reliability

Brushing up on the topic of Site Reliability Engineering, I soon came across [Dickerson's hierarchy of reliability](https://sre.google/sre-book/part-III-practices/), inspired in format and approach by the well-known [Maslow's hierarchy of needs](https://en.wikipedia.org/wiki/Maslow%27s_hierarchy_of_needs), so this piqued my interest and I thought it would be interesting to explore this topic a little bit and use it as a kind of repository of guidance and practices to include in your SRE workstream, or when you are trying to build it up in the first place. A team or organization can use this to aim at gradually and systematically building up their system reliability capability and evaluate how their current practices fare in each level.

In the book [The Art of Site Reliability Engineering with Azure](https://www.goodreads.com/book/show/63839646-the-art-of-site-reliability-engineering-sre-with-azure), the authors - exercising good judgement - add an extra layer at the bottom of said pyramid, which is the foundational practice of designing resilient architectures. This is foundational precisely because it is an activity that you can execute from day 1 in the solution's life cycle, that is, planning and design, and then forward from there. So we will consider this layer 0 below.

The Dickerson Hierarchy of Reliability was created by Mikey Dickerson, a former Google SRE, who was inspired by Maslow's Hierarchy of Needs. The hierarchy was first introduced in 2013, when Dickerson was working on the [HealthCare.gov](http://healthcare.gov/) project, and has since been widely adopted in the SRE community. The hierarchy, like any pyramid diagram, is based on the idea that each level builds upon the previous one, and that teams should focus on the lower levels before moving on to the higher levels. Although that project seems to have started off on the wrong foot.

It applies to both greenfield and brownfield scenarios, cloud, on-premises or hybrid and seems to be widely used in the SRE community as it provides a framework for prioritizing work on improving systems' reliability. 

## Exploring the levels

- 0) __Resilient Architecture Design__: the practice of designing and architecting systems and applications that minimize failure, can recover from failure (fault-tolerant) and try to ensure continuous operation and minimal disruption. This approach involves several key practices such as anticipating and modeling failures and threats, planning redundancy and failover, as well as how will the system scale and face load spikes. In the specific case of Azure, the famous [Well Architected framework](https://learn.microsoft.com/en-us/azure/well-architected/what-is-well-architected-framework) offers some guidelines based on [4 key principles](https://learn.microsoft.com/en-us/azure/well-architected/reliability/principles), but we will not go into those here.

- 1) __Monitoring__: The foundation of the hierarchy, monitoring involves collecting metrics and logs to gain operational awareness. Effective monitoring helps detect issues early and provides data for optimization. It's complicated that you can effectively manage what you do not monitor end to end in the first place. Without good observability and actionable alerts you cannot trigger incident creation, especially in complex distributed system, and therefore, the next layer, would be quite hampered.

- 2) __Incident Response__: Efficient handling of incidents minimizes their impact. This layer focuses on quick resolution and mitigation of problems as they arise, because they will. There are several incident response frameworks out there, most notably, [NIST](https://csrc.nist.gov/projects/incident-response), [ISO](https://www.iso27001security.com/html/27035.html), [SANS](https://www.sans.org/media/score/504-incident-response-cycle.pdf). They are pretty similar in spirit, and I will not go into comparing them here, but probably any organization would do well in building its own structured approach and guidance to live site incident management, including a clear chain of command, clear roles and responsibilities, documentation and communication, remediation and learning.

- 3) __Postmortem Analysis__: Learning from failures is crucial, not only in SRE but generally in life. Postmortem analysis involves reviewing incidents to understand their causes and equally important, prevent recurrence. This will require proper understanding of all the factors that contributed in the incident, which you cannot have without the first layer. A culture of [blameless](https://postmortems.pagerduty.com/culture/blameless/) [postmortems](https://sre.google/sre-book/postmortem-culture/) is critical here. Depending on where your organization sits in [Westrum’s Organizational Model](https://itrevolution.com/articles/westrums-organizational-model-in-tech-orgs/) this could be an issue to work on for improvement. Another good reason to have proper observability in place is that you want to avoid having to depend on the esoteric knowledge of "old hands" that have a second nature knowledge of the system, but will not be around for ever.

- 4) __Testing__: Ensuring system resilience before deployment through rigorous testing helps identify potential weaknesses. The learning that hopefully happened in the previous layer is leveraged here, improving current practices in how you test and release new features. Perhaps you need to reduce the implicit blast radius of new releases that are too big. Leveraging automation here is key too. Examine your overall current testing practices, starting with unit testing. There is [another pyramid](https://www.headspin.io/blog/the-testing-pyramid-simplified-for-one-and-all) to help you here.

- 5) __Capacity Planning__: This layer ensures that the infrastructure can meet future demands without performance degradation or outages. This builds on the previous layers with practices such as analysis of resource utilization, forecasting demand (probably best done with your business counterparts to understand seasonal spikes, launches or product cycles), identify and harden point of failures (for example, protecting yourself from third party dependencies you do not control, or that legacy system you still need to use), scalability and load and performance testing. Capacity planning is a cross-team activity and regular reviews of an application and the evolution of its architecture to prevent the inevitable creep of inertia and entropy are key to stay on top of scalability. Observability is again important here, you want to make sure that spike in consumption is real and not actually a bug. Capacity planning is not always about up, up, we need to know when we can safely scale back for cost and sustainability.

- 6) __Development__: Are you building the right thing, and are you building the thing right? Incorporating solid software engineering practices and reliability principles into the design and coding phases ensures that reliability is built into the system from the start. How have people fixed similar situations or problems elsewhere? Avoid reinventing the wheel or rolling out your own (probably subpar) "solution". Build vs buy is an importan decision in this layer.

- 7) __Product Reliability__: Achieved when all previous layers are functioning correctly, this final layer ensures that the product meets reliability standards and user expectations. This is what users and customers see. In many organization it is still common that engineers have zero visibility or understanding on the experience on the other side of the chasm. It is vital to understand the application in the context of the user and feed that into successive iterations of the development cycle. Regular reviews, updates, and improvements based on user feedback and performance data are essential (data-driven). This iterative approach helps in adapting to changing user needs and technological advancements. Deficient implementations or gaps in the practices of the previous levels will be acutely noticed here. As we iterate, a continued clear articulation of KPIs and nonfunctional requirements are essential in order to guide the backlog, the implementation and the investment.

## Caveats

A note when using tools or frameworks like this, is not to fall back into absolute modes of thinking. By that I mean to keep in mind what constitutes _acceptable resilience_ for any given workload and invest accordingly. Aiming for 100% everywhere makes little sense. Not all outages have the same economic or reputational impact, obviously.

- where are the workloads running?
- what are current, requested or acceptable levels of availability for each subsystem?
- what is your current level of monitoring? SRE requires more than old style monitoring of basic metrics. It requires SLIs, user-facing metrics, and context-rich observability.
- how does your team or organization currently develop, test, release and manage systems and applications?
- how much of that is automated and what is lacking? (_a key tenet of SRE is to automate as much as possible with the overarching goal of [reducing toil](https://itrevolution.com/articles/westrums-organizational-model-in-tech-orgs/)
- how is your monitoring today and what would you like it to be?
- how is your current incident response management practices? Without playbooks, escalation paths, and a blameless culture, as mentioned, incident response will most likely tend to be reactive and stressful (war rooms, etc)
-  beware the "infinite scalability" myth of cloud marketing


# References

- [Google SRE Book](https://sre.google/sre-book/table-of-contents/)

- [The Art of Site Reliability Engineering with Azure](https://www.goodreads.com/book/show/63839646-the-art-of-site-reliability-engineering-sre-with-azure)

- [How to Engineer for Real Reliability Using Dickerson’s Hierarchy](https://www.contino.io/insights/how-to-engineer-for-real-reliability-using-dickerson-s-hierarchy)

> Written with [StackEdit](https://stackedit.io/).

