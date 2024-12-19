## **Cognitive Barriers**

In a certain way, a continuation of my former article on [biases that can derail a project](./seven-biases.md), and being fully aware I am probably out of my depth here, I explore this topic to learn a little bit on this idea of cognitive barriers and as well as something to be aware of, a sort of cognitive tool, if you like, that can be applied to project and product management work, especially when it comes to decision-making and problem solving, especially in more novel scenarios that include new variables and considerations. Cognitive barriers being basically mental obstacles that affect how one perceives, understands, and processes information apply and affect learning, decision-making, problem-solving and communication in general, which has broad relevance in any field, but especially those that are knowledge-intensive. 

It's probably due to the necessarily distorted view from my own experience, but cognitive factors as germane to Software Engineering, being one such knowledge-intensive, seem to have been well [researched](https://www.semanticscholar.org/paper/Cognition-in-Software-Engineering%3A-A-Taxonomy-and-a-Fagerholm-Felderer/37f32619cc4992078c1a45983eb3195f13b831e0) since the dawn of the field (but is far from mature and complete) and most people seem to be aware of basic facts about cognitive barriers or of factors that increase cognitive load and hamper desirable performance, including the formation of knowledge, perception, attention, context switching, memory, cognitive load, reasoning, cognitive biases, social cognition, cognitive control, and making mistakes or overlooking errors. 

Many of these biases actually overlap and / or present themselves in varying combinations. This is only an attempt to very simply enumerate and describe them with the goal of awareness, more than trying to quantifiable trying to understand these barriers or filters, since they often operate in autopilot without us being aware. I did not include as well other factors that do not fall into the specific conceptual category of the cognitive, such as the motivational or the emotional which, while having an impact on decision-making and problem solving, are distinct categories. Some barriers, though, while cognitive in nature are very much influenced by the cultural (as in organizational culture) environment.  

#### 1. **Perceptual Filters**
   - **Mental Filters**: Tendency to interpret information through pre-existing beliefs or frames, distorting weak signals or ignoring dissonant data (as in [cognitive dissonance](https://en.wikipedia.org/wiki/Cognitive_dissonance)). 
   - **Selective Attention**: Focusing on certain stimuli while ignoring others, often unconsciously filtering important but subtle cues. There are many reasons why this can happen.
   - **Expectation Bias**: Seeing what we expect to see, rather than what is objectively present. Also **Confirmation Bias** below.
   - **Echo Chambers**, or environmental reinforcement as I like to call it, which is another fancier way to say group thinking or herd mentality.
   - **Selective Amnesia**, which is self-explanatory. In the context of project / product management and decision-making, this bias appears in the tendency to overlook or forget specific information, events, or lessons (that weren't learned), especially those that are inconvenient, uncomfortable, or contradictory to the narrative or to our ideal desired view of how reality should be. Thus we brush aside past project pitfalls, critical feedback, fail to account for previous mistakes, all of which ultimately leads to repeated errors or overly optimistic plans.
   - **Peak-end rule**, perhaps an inversion of selective amnesia, more like selected memory perhaps, is a cognitive bias in which people judge an experience largely based on how they felt at its peak (the most intense moment) and at its end, rather than evaluating the experience as a whole ([more](https://en.wikipedia.org/wiki/Peak%E2%80%93end_rule)). This rule applies to both positive and negative experiences and can lead to distorted memories of the actual event (just like selective amnesia also ultimately does). The peak distorts and disproportionately influences the overall evaluation, and the total length of the experience often has less impact on its remembered quality, a bias known as **duration neglect**.

#### 2. **Biases and Errors in Judgment**
   - **Overconfidence Bias**: The tendency to overestimate one’s knowledge, abilities, or beliefs. The well-known [Dunning–Kruger effect](https://en.wikipedia.org/wiki/Dunning%E2%80%93Kruger_effect).  
   - **Confirmation Bias**: Seeking, interpreting, or remembering information in a way that supports pre-existing views while ignoring contrary evidence.  
   - **Anchoring Bias**: Relying too heavily on the first piece of information received (the "anchor") when making decisions. Can be motivated by a need to save face due to some quick decision too early on.  
   - **Availability Heuristic**: Judging the probability of events based on their ease of recall, which may lead to distorted conclusions.  
   - **Representativeness Heuristic**: Making assumptions based on stereotypes or similarities, ignoring base rates or statistical probabilities.  
   - **Hindsight Bias**: Believing, after an event, that we "knew it all along," which distorts our understanding of past decisions.
   - **Law of Small Numbers**, which is related to other biases such as availability and representativeness, and reflects the tendency to draw strong conclusions based on small sample sizes or small data sets whose correcteness is not even examined, which leads to overgeneralization and inaccurate judgments. It is also a case of **Oversimplification**. This law of small numbers ties directly to Nassim Taleb’s work on black swan events and fat tails, particularly in how human cognition often underestimates the impact of rare, high-impact events that occur in distributions with fat tails. If you are not familiar with his work, that is something I recommend you do sooner than later. This leads to **overconfidence in predictions** based on insufficient data and **ignoring variability and extreme outcomes** that small samples cannot reveal. This illustrates too why a [pre-mortem](./on-premortems.md) are an useful tool too.
   - **Dismissing fat tails**, where a fat-tailed distribution is one in which extreme values (outliers) occur much more frequently than predicted by a normal (Gaussian) distribution. These tend to be dismissed because it is more comfortable to default to normal distribution models due to other default cognitive modes that place less load on us: easier understanding, the comforts of (delusional) certainty, confirmation bias and the illusion of believing the the world behaves according to thin-tailed, predictable patterns, which contributes to flawed decision-making, risk dismissal, misguided investments and so on.
   - **Base Rate Neglect**: related to the biases we've seen already above, refers to how we ignore or undervalue statistical base rates (general probabilities) in favor of specific anecdotal or representative information, thus selecting data that confirms our views, limiting ourselves to oversimplified smaller datasets and ignoring ambiguity or probabilities we perceive as rare. 
   - **Illusion of Validity**: The unwarranted belief in the accuracy of one's judgments or predictions, even when the evidence is weak or contradictory.

#### 3. **Ambiguity and Complexity Aversion**
   - **Dislike for Ambiguity**: A strong preference for certainty and clear answers, even when ambiguity is unavoidable. The desire to simplify reality in order to be able to cope with too many complicated situations daily. The allure of dumbing down things to framework and 2x2 matrices with the illusion of being using sophisticated tools for enhanced decision-making. 
   - **Oversimplification**: Reducing complex issues to overly simplistic frameworks, like 2x2 matrices, to make them easier to digest.  
   - **Nuance Avoidance**: A reluctance to engage with gray areas, trade-offs, or contradictory evidence. Similar to **Dislike for Ambiguity**, in fact, in its need to simplify thing and reduce inherent complexity.

#### 4. **Social and Organizational Barriers**
   - **Groupthink**: The desire for consensus overrides critical analysis, leading individuals to align with majority views and suppress dissent.  
   - **Authority Bias**: Placing undue weight on the opinions or decisions of authority figures, even when flawed ([hippos](https://www.capterra.com/glossary/hippo-highest-paid-persons-opinion-highest-paid-person-in-the-office/) etc.)
   - **Conformity Bias**: Tendency to follow group norms or behavior, often driven by social acceptance rather than independent reasoning.  
   - **Pluralistic Ignorance**: When individuals privately disagree with a norm but go along with it because they assume others agree.
   - **Halo effect**: a single positive trait disproportionately influences overall perception, the perception of other unrelated traits or tends to dismiss risks or other negative traits. Can be related to [FOMO](https://en.wikipedia.org/wiki/Fear_of_missing_out) in technology adoption and decisions.

#### 5. **Mental Rigidity and Cognitive Shortcuts**
   - **Functional Fixedness**: Seeing objects or ideas only in their traditional uses or roles, hindering innovation.  
   - **Status Quo Bias**: Preferring the current state of affairs over change, even when alternatives may be better. Change is often messy, so this could be risk avoidance, insecurity or knowing deep inside that the initiative is doomed, or no incentives to change because rent-seeking opportunities are perceived to be reduced after the change.  
   - **Mental Set**: Relying on familiar solutions or ways of thinking, even when inappropriate for new contexts. Meme-copying, applying the same solution stencil we've applied in the past. Again this simplifies complexity and cognitive load while assuring us it will also work this time - when perhaps it really didn't before either (aka **Hindsight Bias** above)

#### 6. **Cognitive Overload**
   - **Information Overload**: Being overwhelmed by too much data, leading to paralysis or poor decision-making.  
   - **Decision Fatigue**: Deteriorating quality of decisions after making too many choices in a row.  

#### 7. **Emotional and Motivational Barriers**
   - **Loss Aversion**: Placing a greater emphasis on avoiding losses than on achieving equivalent gains.  
   - **Fear of Failure**: Allowing the potential for failure to prevent risk-taking or experimentation.  
   - **Optimism Bias**: Overestimating positive outcomes while underestimating risks or obstacles.
   - **Affect Heuristics": when decision-making is influenced by emotions or feelings associated with the options, often bypassing rational analysis. People rely on whether they like or dislike something to guide their judgments and choices.([more](https://thedecisionlab.com/biases/affect-heuristic)). It probably has other incentives and motivations underneath than just mere preference.
   - **Endowment effect**: when we assign too much undue value to things we already own, or decisions we already made and communicated. This leads to overpricing certain systems or overestimating a course of action because we already put our stakes on it. 

#### 8. **Temporal and Framing Barriers**
   - **Present Bias**: Valuing immediate rewards over long-term benefits, leading to short-sighted decisions.  
   - **Framing Effect**: refers to how decision-making is heavily influenced by how information is presented (e.g., as a gain vs. a loss), even when the underlying facts remain unchanged. Something which the skillful communicator can manage to its own advantage to sell something or to manage up.
   - **Sunk Cost Fallacy**: Continuing an action because of previously invested resources, despite its diminishing value. Somewhat related to a more emotional **endowment effect**.
   - **Planning Fallacy**: the very well-known tendency to underestimate the time, costs, and risks of future tasks while overestimating the benefits and likelihood of success. I guess we could also call it **best-case scenarios bias**. This fallacy is often helped by sales or pre-sales overpromising on the miracles of some technology as well as by our tendency to ignore historical precedence, complexity and ambiguity in systems and a bias towards brushing problems under the carpet for fear of being perceived as "negative" 

#### 9. **Knowledge and Skill Gaps**
   - **Illusion of Competence**: Overestimating one’s skills due to a lack of self-awareness or proper feedback.
   - **Illusion of Understanding**: we often believe we understand how things work more deeply than we really do. This is the old saying that goes something like "if you cannot explain it to a child, you have not really understood it". often appears together with the **Hindsight Bias** and is also similar to **Illusion of Validity**
   - **Dunning-Kruger Effect**: Incompetent individuals fail to recognize their lack of skill, while experts may underestimate their own abilities.  

---

## Papers and readings

- [Cognition in Software Engineering - A Taxonomy and Survey of a Half-Century of Research](https://www.semanticscholar.org/paper/Cognition-in-Software-Engineering%3A-A-Taxonomy-and-a-Fagerholm-Felderer/37f32619cc4992078c1a45983eb3195f13b831e0)
- [Bloom’s taxonomy of cognitive learning objectives](https://www.semanticscholar.org/paper/Bloom's-taxonomy-of-cognitive-learning-objectives.-Adams/8e2ca9fb5e8c0383966351650fa11771c6bf5873)

- Daniel Kahneman, 2011. "Thinking, Fast and Slow"
- Nassim Nicholas Taleb, 2001. "Fooled by Randomness: The Hidden Role of Chance in the Markets and in Life"