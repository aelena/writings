### My notes on Werner Vogel's AWS Reinvent Keynote
Werner's keynote is one of the events of the year for me. These are key points and ideas that I took from [this year's keynote](https://www.youtube.com/watch?v=aim5x73crbM). As usual, there is no shortage of interesting ideas, which some could seem obvious in retrospect. I allow myself the temerity to add some commentary on some of the ideas.

## Key Idea: Simplexity
__Simplicity requires discipline__
*(intentional focused work and principles)*

## 21st Century Architectures should be

__Controllable__
-   Decomposed intro small, loosely coupled, stateless building blocks - *(statelessness is one of my key principles as state is generally a liability - if you really need state, you need to work a way to control the impact and the constraints this liability imposes)*
-   Automate applications and processes
-   Let business levers control the system
-   Architect with cost in mind (thefrugalarchitect.com)

__Resilient__
-   Protecting your customer is your first priority
-   Integrate security into your application from the ground up
-   In production, deploy to at least two availability zones
-   Build, test, integrate and deploy continuously
-   Don't think in single failures
-   Don’t treat failure as an exception

__Data-driven__
-   Instrument everything, all the time
-   Inspect the whole distribution
-   Put everything in logs

__Adaptive__
-   Assume nothing
-   Use late binding


## Tesler's Law
I was not aware of this law
> "Complexity can neither be created nor destroyed, only moved somewhere else"

More on that here https://lawsofux.com/teslers-law/. Obviously, applies not only to UX, but also to systems' design and engineering.

## Complexity warning signs
-   Declining feature velocity
-   Frequent Escalations 
-   Time-consuming debugging *(how frequent "blind debugging" happens and the results of those efforts are something you should carefully examine)*
-   Excessive Codebase growth
-   Inconsistent patterns
-   Dependencies everywhere - *(this is certainly a concern for systems design and integration but can also be an issue with some specific technologies)*
-   Undifferentiated work - *(examine how much time you are needing to spend on that?)*


## Lehman's Laws of Software Evolution

__Law 1 - Continuing Change__ - systems must be continually adapted else they become progressively less satisfactory  - *(surprising how this fact, which should be pretty obvious in itself, needs to be hammered again and again with some constituencies)*

__Law 2 - Continuing Growth__ - the functional content of a system must be continually increased to maintain user satisfaction with the system over its lifetime - *(but also beware feature creep and useless cruft)*

__Law 3 - Increasing Complexity__ - as a system evolves, its complexity increases, unless work is done to maintain or reduce it

__Law 4 - Declining Quality__ - a system will be perceived to be declining in quality unless it is rigorously maintained and adapted to its changing operational environment

## Lessons
**Lesson 1 - Make evolvability a requirement**
- Evolvability is a precondition for managing complexity
- Easily accommodate future changes.
- System disaggregation
- Low coupling & high cohesion
- Well-defined APIs
- Principles for evolvable systems, see below

__Lesson 2 - Break complexity into pieces__
- Disaggregate into building blocks with high cohesion and well-defined APIs

__Lesson 3 - Align organization to architecture__
- Build small teams, challenge the status quo, and encourage ownership
- Focus on Ownership
- Build a sense of agency in the team (make sure they feel they have the support they need in order to deliver)
- Agency + Urgency - *(moving fast as a leader - but there is the obvious caveat of not building urgency as the "natural" effect of poor management decisions, deficient project management and poorly thought-out processes)*

**Lesson 4 - Organize into Cells**
- In a complex system, it is essential to reduce the scope of impact (control the blast radius for decisions and failures alike)
- Organize your services into isolated, manageable units.
More on cell-based architecture [here](https://docs.aws.amazon.com/wellarchitected/latest/reducing-scope-of-impact-with-cell-based-architecture/reducing-scope-of-impact-with-cell-based-architecture.html)

*The same question we had with microservices surfaces with how big should a cell be? Think enough to benefit from economies of scale. Another act of balance here too.*

**Lesson 5 - Design Predictable Systems**
Simplicity is the key to build predictable systems. *(Complexity tends to rapidly escape our capabilities for control and management - this reminded me of the well-known [principle of least astonishment](https://en.wikipedia.org/wiki/Principle_of_least_astonishment))*
- Reduce the impact of uncertainty in your systems.
- Allow your smaller systems to call upon larger systems.
- Implement the ["constant work" pattern](https://aws.amazon.com/builders-library/reliability-and-constant-work/).


**Lesson 6 - Automate Complexity**
- Automate everything that does not require high judgment. 
- We often ask, "What should we automate?"
- Instead, consider, "What don't we automate?" - only when humans need to be in the loop

## Principles for Evolvable Systems

Evolvable systems have better chances of successfully managing and taming complexity

-   Modeled on business concepts (in my humble opinion, complexity has to be managed on that side too)
-   Hidden internal details
-   Fine-grained interfaces (again a balance between coarse-grained and chatty interfaces)
-   Smart endpoints
-   Decentralized (not the same as distributed)
-   Independently deployable
-   Automated
-   Cloud-native design patterns
-   Isolate failure
-   Highly observable
-   Multiple paradigms

This additional principle is actually not explicitly stated but alluded to during the keynote, which is

-   Keep the complexity hidden from the users, do not allow the internals and the accrued architectural choices you've made leak to the user experience. That too requires additional intentional work.

## Other ideas
Other tidbits that resonated during the keynote

- Think how your systems have (and articulate in) different tiers of complexity and reliability, criticality - *this is important in order to also be cost-conscious and invest/focus where it matters the most*
- Learn to distinguish between intended and unintended complexity
- Complexity != number of components - Entia non sunt multiplicanda praeter necessitatem. *(Flexibility has to be factored in - a balance is to be stricken there)*
- Pay attention to __Complexity Warning Signs__ as they appear
- Heraclitus on Systems: our systems are in constant flow - *(seems pretty obvious but somehow we manage to forget that)*
- Build on primitives - *(getting to understand the shape of those primitives and building them right is neither trivial nor a one-time effort)*
- Share your lessons
- [Monoliths are not dinosaurs](https://www.allthingsdistributed.com/2023/05/monoliths-are-not-dinosaurs.html)
