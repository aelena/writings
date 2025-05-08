# Theory of Constraints
The Theory of Constraints (ToC) is a management philosophy introduced by Dr. Eliyahu M. Goldratt in his 1984 book "The Goal". Disclaimer: I have not really gotten to read the book yet, but this was a term I was not familiar with, so my interest was immediately piqued and had to research this a little bit. Heck, there is even an [Theory of Constraints Institute]([https://www.tocinstitute.org/](https://www.tocinstitute.org/)).

As a manner of TL;WR (won't read), ToC is a theory based on the principle or core tenet that any manageable system is limited in achieving its goals by a generally small number of constraints, and that there is always at least one constraint actively limiting the system at any given time, or we would be in a perfect universe otherwise, which we have ample proof is not the case. It could be then said that the idea of TOC is predicated on detecting a critical bottleneck and attempting to remove the bottleneck in a constant iterative effort to upgrade the system to a new stable level of performance. A constraint can be anything, a team, a process, a way of operating or that isolate server no one will update for fear it will not come back up and nobody knows where the code is.

The origins of ToC can be traced back to Goldratt's work in developing software for production scheduling in the late 1970s. He observed that traditional manufacturing approaches often led to inefficiencies and bottlenecks. This led him to develop a new approach focused on identifying and managing constraints to improve overall system performance. While ToC was initially developed for manufacturing, its principles have since been applied across a wide range of industries and domains outside of software development, such as supply chain management. finance and accounting or project management.

## The process

Since the central concept of ToC is that every system has a weakest link or bottleneck that limits its overall performance, then it should follow that by focusing efforts on improving this constraint, the entire system's performance can be enhanced. Therefore, ToC proposes a five step process for continuous improvement:

1.  __Identify the system's constraint(s)__ -  Locate the weakest link in the development process. This could be a specific team, individual, or process that's limiting throughput.
2.  __Find out how to exploit the constraint(s)__ - Maximize the efficiency of the identified bottleneck without adding more resources. This might involve reducing work-in-progress (WIP) or redirecting team members to assist with the bottleneck. Once the constraining process is operating at its maximum capacity, the speeds of other processes are functions of the speed or capacity of the constraint.
3.  __Subordinate everything else to the above decision__ - Align all other processes to support and work around the constraint. This ensures the bottleneck is never starved of work. This is also called the __focus principle__.
4.  __Elevate the system's constraint(s)__ - If necessary, allocate additional resources or implement changes to alleviate the bottleneck. This could include investing in automation, implementing test-driven development, or adopting pair programming to spread knowledge or more expensive stuff like capital investment or reorganizations (somewhat surprisingly, some organizations tend to go for this directly).
5.  __Repeat__ - Once a constraint is resolved, return to step one to identify the next bottleneck, fostering continuous improvement and watching out for not creating new constraints in the process, or succumbing to inertia.

Do not confuse inertia as in physics, related to an object's mass and referring to the resistance of any physical object to changes in its velocity unless acted upon by an external force, and [social inertia](https://en.wikipedia.org/wiki/Social_inertia) as in the tendency of organizations and social systems to resist change and maintain the status quo, even when there are compelling reasons to adapt, manifesting through resistance to adopting new technologies, processes, or ways of working (this applies as well as to how countries are run in spite of abundance contrarian evidence), resistance or difficulty in changing established routines, structures, and cultural norms and often the sunk costs fallacy too, or the reluctance to abandon existing investments in favor of new approaches.

One of the key strengths of TOC is its emphasis on continuous improvement, or focusing on whatever it is that reduces the speed of product or value delivery through the system, where a system is canonically defined as series of inter-dependent processes where the performance of the entire chain depends on the strength of the weakest link. 

The iterative process of ToC is not meant to be a one-time fix, but rather an ongoing cycle of identifying and addressing constraints as they shift within the system. This aligns well with modern management philosophies that emphasize adaptability and continuous learning. ToC also introduces several important concepts that have gained traction in management thinking:

- POOGI (**Process of On-Going Improvement**) and [The Five Focusing Steps](https://www.tocinstitute.org/five-focusing-steps.html), which provide a systematic approach to improvement.
-  The [Drum-Buffer-Rope (DBR)](https://www.6sigma.us/six-sigma-in-focus/drum-buffer-rope-dbr/) scheduling method, which synchronizes production to the pace of the constraint, thus reducing Work In Progress to avoid clogging the system. The “drum” represents the constraint that sets the pace, the “buffer” ensures the drum never starves, and the “rope” controls the release of work
- The Thinking Processes, a set of tools for analyzing and solving complex problems.

## The Axioms 
ToC is based on three fundamental axioms:

1.  __Convergence__ (also called "Inherent Simplicity")  
    This axiom states that the more complex a system is to describe, the simpler it is to manage, somewhat counterintuitively at first sight. It suggests that in highly interconnected systems, there are fewer points that need to be managed to impact the entire system. A key implication is that every organization has at least one active constraint at any given time.
2.  __Consistency__ (also called "There are No Conflicts in Nature")  
    This axiom posits that if two interpretations of a natural phenomenon conflict, at least one must be wrong. In an organizational context, this means that when two parts of an organization with a common goal are in conflict, the reasoning that led to the conflict must contain *at least* one flawed assumption.
3.  __Respect__ (also called "People are Not Stupid")  
    This axiom asserts that even when people do things that seem irrational, they have a reason for that behavior. It emphasizes that people are not inherently irrational and their actions, even if seemingly counterproductive, stem from some underlying logic or motivation, organizational factors, misaligned incentives or what have you.
    
## Implementing ToC
Any methodology, however lax, will benefit from identifying and addressing high-level bottlenecks. It's likely that in many case, those will be organizational, social, procedural or policy-related, more than merely technical. Things like long and rigid approval processes, overly complex branching strategies, outsourcing contracts and activities like 
- knowledge transfers or any type of handoffs between teams
- inefficient communication channels, things like CAB's
- manual deployments / releases
- separate manual testing team, or testing bottlenecks in general 
- lack of clear requirements, or frequently changing requirements and priorities
- Limited developer resources or skills
- Technical debt, of course
- Complicated [TOM](https://www.luxoft.com/blog/luxoft-target-operating-model-your-transformation-on-the-right-path)'s for the development organization with stages, approvals etc which add a lot of overhead

A thing worth noting here is that in order to identify bottlenecks we need to know what is our purpose and we need to be able to measure the distinct parts of the process. Sounds obvious, but it is not always the case that measurements can be had, backed up with actual data. Based on the criteria we choose, our purpose and our ability to measure, a constraint can be here or there. This is important too because we need to be sure it is not the rest of the system that is actually slowing the perceived bottleneck down, instead of the bottleneck itself being at fault. The volume of work in queue next of a process operation is a primary indicator. Another instance is where goods are processed in batches.

A testing bottleneck will affect releases and deployments, which will increase the likelihood, in turn, of changing requirements or priorities, and cause *mura* / *muda* in the process (see below). Therefore, to address this problem, and following the steps we saw earlier, we then need to

- __Exploit the constraint__, should be maximized without major changes. For the testing bottleneck example, this will likely involve:
  -   Prioritizing test cases to focus on the most critical functionality, increasing stability and reducing regression errors
  -   Automating those repetitive tests to reduce waste
  -   Providing testers with better tools and environments to reduce repetitive slow and error-prone manual testing 
- __Subordinate the rest of the process__, that is, align other activities to the overarching goal of solving this bottleneck. For now, we do not change anything or add more resources, which tends to be the knee-jerk reaction
  - Let developers write more unit test, heck, demand that this is a non-negotiable development activity that is not to be scheduled or somehow accounted for as a separate activity
  - Consider adjusting sprint planning to provide a steady flow of work to testers
  - Address quality issues (address technical debt) to avoid that testers have to "send back" too many features
  - Consider how testing capability could be part of the teams, not a separate later stage
  - Perhaps, implement feature flags
- __Elevate the constraint__, if the constraint still limits throughput after the previous stage and you're sure you did that right and not half-heartedly, then perhaps more resources may need to be invested, such as hiring more tester, procuring better tools or training testers so they can also do automation work, which is probably a good idea regardless.

As constraints are addressed, new bottlenecks will emerge. The process should be repeated to continually improve the software development workflow.


## ToC in Software development

Benefits of Applying TOC to Software Development
-   Faster delivery of working software
-   Improved quality and reliability, which probably improves the previous
-   More efficient use of resources
-   Continuous learning and improvement
-   Better alignment with business goals

All of these are self-reinforcing. However, there can be challenges:

- Knowledge work is sometimes necessarily a discovery journey and some constraints will not be apparent
- Organizational aspects not amenable to identifying and addressing bottlenecks "in public"
- Resistance to change from traditional development / managerial practices 
- Conditions imposed by outsourcing contracts
- Cross-functional collaboration is often impossible to remove
- Conway's Law will be at work in some way or another in the implicit design and architecture of your organization, even if that emerged by default with no conscious design behind
- Rapidly changing requirements and priorities

### ToC in Agile methodologies
-   **Lean Software Development**: define and then inspect the value stream mapping to identify waste and constraints. This is really nothing new but something we often impose on ourselves because of processes or the difficulty to enable certain practices. Both ToC and Lean Software Development aim to enhance productivity and efficiency in software development processes.
-   **Extreme Programming (XP)**: Look for bottlenecks in practices like continuous integration or pair programming.
-   **Scrum**: Examine sprint planning, daily stand-ups, and retrospectives for potential constraints. Look for inefficient prioritization and especially rework, either due to poor user stories or for lack of testing and delays. 
-   **Feature Driven Development (FDD)**: Analyze the feature lifecycle for bottlenecks, from feedback loops to rapid prototyping. 

A related tool that can be useful here are [Current Reality Trees](https://en.wikipedia.org/wiki/Current_reality_tree_(theory_of_constraints)). I will not delve now into this in detail. A CRT is a visual, cause-and-effect diagram tool from ToC that tries to systematically identify the root causes behind multiple problems or undesirable effects within a system. The idea is to create clarity of thought in how these are interconnected with the ultimate goal of getting at one or a few core problems - that is, the constraint.

## The Criticisms
- TOC assumes only one constraint acting at a time, which may not reflect reality in complex systems. I guess it could also be read as identifying the top constraint hindering the system. Unblocking that could have (hopefully positive) cascade effects. 
- Short-term focus on removing the immediate constraint can cause unforeseen and potentially serious problems down the road in any complex system whose dynamics are hardly understood well.
- Implementation challenges and difficulty to see the ROI. Implementation challenges are probably an issue with any tool or framework that requires a degree of formalism, discipline, data and thought, instead of meme-copying, hand-waving complexity away and gut-intuition or rather uninspected assumptions.
- Friction and resistance. Also inherent. Like the previous issues, not really a criticism of ToC.
- [Tesler's law](https://en.wikipedia.org/wiki/Law_of_conservation_of_complexity) perhaps?

## Tools
There is a whole rabbit hole of related visual thinking tools in ToC. Let's have a cursory look at some of them.

- [Current Reality Trees](https://en.wikipedia.org/wiki/Current_reality_tree_(theory_of_constraints)) - A cause-and-effect diagram that maps undesirable effects (UDEs) to their root causes, identifying the core constraint limiting system performance
- [Evaporating Cloud (EC)](https://en.wikipedia.org/wiki/Evaporating_cloud) - an interesting name for a tool that tries to resolve conflicts by surfacing underlying assumptions, enabling win-win solutions without compromise. Goldratt himself said that *_conflicts arise because we create them by believing at least one __erroneous assumption__._* This is something you probably can relate to. 
- [The Five Focusing Steps](https://www.tocinstitute.org/five-focusing-steps.html) for managing and dealing with constraints. 
- [Future Reality Tree (FRT)](https://online.visual-paradigm.com/knowledge/problem-solving/what-is-future-reality-tree/), which is similar to CRT but you work it backwards, to see what you should do and remove now to get to the desired target state later, and ideally, also anticipating and avoiding unintended consequences. 
- [Prerequisite Tree (PRT)  /  Strategy & Tactics Tree](https://www.tocinstitute.org/prerequisite-tree.html) - Identifies obstacles to goals and outlines steps to overcome them. The Strategy & Tactics Tree replaces PRT in some contexts, aligning tactics with strategy 
- [Transition Tree](https://hohmannchris.wordpress.com/2015/07/13/thinking-processes-transition-tree/) - nothing that new really, breaks down the path from current to future state, specifying sequential actions to ensure alignment with strategic goals.
- [Drum-Buffer-Rope (DBR)](https://www.velocityschedulingsystem.com/blog/drum-buffer-rope/) - another intriguing name. The Drum is the constraint and all marches to its beat. The constraint sets the pace. This is akin to the weakest link, the slowest walker, conditioning the whole system. The Buffer is there to protect the constraint from variability. It represents the amount of work expressed in time (effort) and the rope controls the amount of work. In the end what this means, is to have enough work in front of the constraint so that it does not run out of work. The buffer in its turn, absorbs the variability.
- [Critical Chain Project Management (CCPM)](https://en.wikipedia.org/wiki/Critical_chain_project_management) - Focuses on resource-dependent tasks, using buffers to protect project timelines from delays.
- [Negative Branch Reservations](https://www.dbrmfg.co.nz/Thinking%20Process%20NBR.htm) - Anticipates and addresses potential negative outcomes of proposed solutions during FRT analysis. Those outcomes could be obvious or unanticipated, which makes them more difficult to effectively identify them, which is why using this tool helps in uncovering the logic and make a negative outcome become apparent, within what's possible. Using a tool forces at least to think consequences through, instead of rushing into implementation carelessly. 
 
## Related concepts
Maybe something like [*Kaizen*](https://en.wikipedia.org/wiki/Kaizen) 改善 came to your mind reading this. Certainly, it can be said that Japanese concepts like *Kaizen* and [*muda*](https://en.wikipedia.org/wiki/Muda_(Japanese_term)) (無駄, waste) are closely related in their focus on continuous improvement and waste reduction in organizations. However, ToC emphasizes identifying and managing the top constraints to improve overall system performance while *Kaizen* promotes ongoing, incremental improvements across all areas of an organization or process. *Muda* aligns with ToC's goal of eliminating non-value-adding activities, but, again, ToC uses a more focused approach by targeting the most critical bottlenecks, while *kaizen* and removing *muda* are typically applied more broadly throughout an organization, team or process. 

Additionally there is also [*Mura*](https://en.wikipedia.org/wiki/Mura_(Japanese_term)) 斑, meaning "unevenness" or "irregularity" in Japanese, refers to inconsistencies and fluctuations in production processes, again another type of "waste" in a process. It describes situations where there are alternating periods of high activity and low activity, creating an uneven workflow, which is in itself, another form of inefficiency or waste. It's relevant to ToC as it negatively impacts overall system performance. Both Constraints and *Mura* disrupt the smooth flow of work. A constraint in TOC acts as a chokepoint, while *mura* creates alternating periods of overburden and underutilization, something which is not unusual to see in development teams, or especially when several teams need to collaborate together and there is tasks handoffs.

# References

- [Theory of Constraints Institute](https://www.tocinstitute.org/theory-of-constraints.html)
- [An essay on the Theory of constraints](https://nzbef.org.nz/wp-content/uploads/2019/05/Paper-An-Essay-on-the-Theory-of-Constraints.pdf)

