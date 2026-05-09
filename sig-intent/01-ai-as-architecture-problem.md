# AI is an architecture problem, not just a model problem

The cheapest part of any AI feature is the model. The expensive parts are the ones people often dismiss and forgets to put in the slides or wavehands away in the discussion.

I have watched this pattern play out in three different use cases in the past eighteen months. A team picks a model, runs a POC in a week, and produces a demo that makes the room nod in vague agreement. Then the demo starts moving toward production and something quietly happens. A few  months later there is no product yet, no "value realization". At best, there are unresolved tickets about data quality, retry semantics, evaluation pipelines, cost overruns, latency budgets, vendor lock-in, and a governance committee nobody invited. Most often, there is just silence.

The failure is actually on the system around the model.

Effectively shipping AI is a distributed-systems problem with ML as one component, and the gap between a working POC and a production product is almost never the model. It is the architecture and everything that has to be there to support the model.

## What the POC does not show you

When you run a POC, you get to assume the nice parts. The inputs are clean, the world is reduced in its messiness and complexity, there is no [network fallacies](https://www.geeksforgeeks.org/system-design/fallacies-of-distributed-systems/), no [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem), no latency, no bad data and no integrations or deployments. The call is synchronous. There is one user — you — and there are no failure modes to handle because the one call you made worked, so ship it because "it worked on my machine."

Production is the very opposite of this set of assumptions.

Production has bad inputs, because real data is always worse in unpredictable ways. Production has concurrency, because you now have more than one user and some of them click twice. Production has latency budgets, because the user will abandon a feature that takes longer than their expectation of what it should cost. Production has a wide array of possible failures, because every call to a model is a network-mediated request to a stateful, throttled, regionally rate-limited third party that can and will degrade at the worst possible time. Production has a bill, because someone now adds up what each call costs and realizes the token budget and margin assumptions were wrong - or the compute, for that matter. And production has users who do adversarial things — intentionally or accidentally — because that is what users do with any interface that accepts free text.

None of those problems are model problems. All of them sit in the realm of distributed-systems problems. Every single one of them is well-known has been studied and solved in the context of service architecture for the past two decades, if not way more. The literature exists. Most AI teams are not using it because they think they are doing ML, and the ML literature does not cover it. Its focus is somewhere else. 

## The actual components of a working AI feature

Strip away the model for a moment and look at what is actually required to run one in production. You need, at minimum:

- A **data pipeline** that reliably delivers the inputs your model needs, with consistency guarantees that match the freshness needs of the feature. If you are doing retrieval-augmented generation, you need an index. If you are personalizing, you need user state. Both of those are real subsystems with their own failure modes. A data pipeline can easily be the hardest part to build, test, validate and maintain. And we know the quality of data in most organizations: not [FAIR](https://www.go-fair.org/fair-principles/), siloed, uncategorized, no MDM and so on.

- A **request pipeline** that handles concurrency, rate limits, retries with backoff, and graceful degradation when the model is slow or unavailable, or puts limits on users' actions. Every production LLM call should have a fallback — cached, cheaper, slower, or explicitly null. No fallback is a promise you cannot keep.

- An **evaluation harness** that runs against a held-out set on every deployment and tells you whether your change made things worse. Drift hits from three directions: data drift as the inputs you retrieve and prompt with shift, model drift as your provider updates the endpoint underneath you, infra drift as the runtime around both moves with every deploy. Without this, you have no ability to iterate, you will be blissfully unaware shipping regressions you cannot diagnose.

- **Observability** that lets you answer "_what exactly did the model see, and what did it do?_" for any individual request a user complains about. You are logging the prompt, the context, the response, the latency, the cost, the user, and the outcome? Without this, how can you possibly triage and solve bugs?

- **Cost control** that tells you when a single user has consumed more of the month's budget than you intended, and cuts them off or charges them. Without this, their consumption and the bill is your problem until addressed.

- In many non-trivial environments, a **governance layer** that tracks what data went into the model, who authorized the integration, and what the model is allowed to do is a must-have. Skip this and your first regulatory question ends the product.

That is the whole system, and I am probably forgetting things. The model itself is but one box in it. If you cannot draw the system, you are not shipping AI; you are hosting a demo (in `localhost:3000` most likely).

## Why teams skip this

Because it is boring and because it is expensive, and unsexy. Decision makers often dismiss or underplay this complexity. A working production AI feature has maybe fifteen percent of its effort in the model and eighty-five percent in the surrounding system. The remaining 20% is 80% of the effort, as per the classic Pareto adage. Yes you might ship the demo faster, which lets you claim faster, which lets the team feel good in the short term. The dopamine hit. 

Debt catches up with you in one of three ways.

- First, __cost__: the bill arrives and someone realizes the unit economics do not work.
- Second, __incidents__: the model has an off day, you have no fallback, the feature fails, and you cannot debug it because you logged nothing.
- Third, __compliance__:legal asks a question you cannot answer, and the feature is frozen until you can.

All three of these are predictable, manageable and avoidable. 
None of them are solved by picking a better model.

## The reframe

The thing to put on the wall when an AI project starts is not a model selection matrix. It is a system diagram. Every component above, every data flow, every failure mode, every cost lever. Do this *before* you pick a model, not after — because the model is the easiest thing to change and the hardest thing to get wrong in a way that kills the feature. Design for model swap-out from day one — ports and adapters, dependency injection, the strategy pattern. These predate the LLM era by twenty years and they remain the right tools for it.

What you will find, consistently, is that the model choice does not matter that much, or in some case, even barely matters. GPT-4, Claude, Llama, a hosted endpoint, a smaller fine-tuned model — all of them will work for 80%, if not more, of business use cases. What makes the difference between a stuck POC and a live feature is whether you have built a system that can operate one.

The companies that are shipping AI at scale right now are not the ones with the best models. They are the ones with the best architectures around the models. The model is a commodity. The system is the product.

## One more thing

If you are a CTO and your team is eight or whatever months into an AI initiative that is still at the POC stage, the question to ask is not *"are we using the right model?"*. The question is *"show me the system diagram that would need to exist for this feature to run in production tomorrow."* If the team cannot draw one on a whiteboard in fifteen minutes, or it is no there on the project's wiki, the problem is not the model and it never was.

AI is an architecture problem. Treat it like one and you ship. Treat it like an ML problem and you will still be in POC next Christmas.
