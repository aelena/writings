# MD, JSON, HTML or XML - Pick the format for the next reader

It seems people are now starting to move to HTML for AI, instead of Markdown. Yes, certainly the informational density and the visual communication and design possibilities of HTML are far superior to what can be achieved with Markdown, and its mermaid or ascii diagrams, and code fences. 

The argument — credited most cleanly to [Thariq's recent essay](https://x.com/trq212/status/2052809885763747935) (as of this writing) on Claude Code's output formats on Twitter — runs roughly like this: HTML beats Markdown for AI-generated artifacts because HTML is both a data format and a rendering target. The same artifact serves machine parsing and human comprehension at once. Density compounds. The argument is correct. And I would add that it significantly raises the odds of people reading you, if you use HTML and not Markdown

However, I think the debate and the framing is also incomplete in a way that matters. It is not HTML vs MarkDown, rather, the question is: **who is the next reader?** Once you ask that, the format choice is not a debate, and becomes a matter of architecturally thinking downstream and making the best choice, something most teams never ponder. 

This is a specific instance of not framing a decision at the right altitude. The format question is smaller than the __decision-craft__ question beyond.

## What the format debate is actually about

Lets walk through the four formats in active use right now to find the right framing.

- **Markdown.** The conversational format. Optimized for humans-and-LLMs reading prose with light structure: headings, lists, emphasis, code blocks. Cheap to produce, cheap to read, cheap for a model to attend to, portable. But it carries no metadata, no validation, no rendering richness — and that is the point. It is the format of the chat window, and perfect for that.

**HTML.** The battle-tested presentation classic format. Optimized for humans browsing a rendered artifact. Carries layout, navigation, tables, SVG, code, links, embedded interactivity and much more it accrued over the years. Density compounds because a single document serves both the parser and the eye. This is the format Thariq's argument identifies and the reason Claude-generated dashboards and reports are increasingly delivered as HTML.

**XML.** Another veteran, the solid rugged contract format. Optimized for parsers, validators, schema-checkers, and language models trained to attend to tag boundaries. Its underrated feature is *mixed content* — the ability to put prose inside structure inside prose without escape-trapping it in a JSON string. Anthropic's own prompting guidance leans on `<context>`, `<example>`, `<instructions>` for the same reason: the boundaries are explicit and the model treats them as load-bearing. Older, slower, yet a force to still be reckoned with. 

**JSON.** The control-plane format. Optimized for compact machine-to-machine traffic where payloads are small, fields are typed, and verbosity is overhead. Tool calls, API responses, configuration, agent control messages — JSON wins because nothing about the message is for a human, and brevity is a feature.

Each format has a primary downstream reader/consumer. 

## The reframe

> Downstream thinking - Pick the format for the next reader.

The consequence: most format arguments are not considering *who or what reads the artifact next*. Two engineers arguing whether agent output should be Markdown or XML are usually arguing whether the next reader is a human, another agent, a legacy system, or a downstream parser — and the disagreement is about that, not about syntax or verbosity. Resolve the consumer question and the format question becomes clear and takes about just a few minutes at most.

The corollary, which is where most teams actually go wrong: when an artifact has more than one next reader, *no single format is correct*. The honest answer is a layered one.

## The hybrid stack

The pattern that pays off in practice, and which few think and build, is to choose the formats by the next reader-role rather than picking one one-size-fits-all standard or convention.

A specific example. An agentic system surfaces a finding from an incident-triage pipeline:

```xml
<finding confidence="0.7" source="trace-7421">
  <h3>P99 latency regression on /search</h3>
  <p>Tail latency rose 40% after the 2026-04-12 deploy. Correlates with cache hit ratio falling below 85% on two of three regions.</p>
  <evidence>
    <table>...</table>
  </evidence>
</finding>
```

Three layers, one complete artifact with precise layered meanings, three readers:

- The XML envelope (`<finding>`, `<evidence>`, attributes) is the *contract*. A downstream parser keys off it, a schema validates it, a confidence threshold filters on it before a human ever sees it.
- The HTML payload (`<h3>`, `<p>`, `<table>`) is the *interface* and the vehicle for visual communication. A reviewer renders it and reads it without translation.
- The attributes (`confidence`, `source`) is the metadata, structural and contextual.

Generalize the pattern across a typical agentic system and the stack looks clear:

- **JSON**, or even yaml, for the control plane: tool calls, agent-to-agent commands, configuration, anything compact and typed.
- **XML** for document envelopes and formal specs: schema-validated message structures, prompt blocks with explicit boundaries, intermediate representations between pipeline stages, payloads that need to round-trip between machines and humans without losing structure.
- **HTML** for the visual and inspection layer: dashboards, audit logs, review screens, anything a human reads after the fact. Old technologies can be agently leveraged to transform the XML, not produced natively or generatively. That keeps the strictness as information moves.
- **Markdown** for the conversation: model-to-human and human-to-model exchange, where light structure is enough and ceremony costs more than it pays. And now, also for human to agent communication, one order of magnitude richer.

Thus:
- XML for contracts
- HTML for visual interface and human communication
- Markdown for the conversation
- JSON is for the wire


## The cost trap

There is a discipline this pattern requires, and it is the part teams skip.

**Formalism only earns its keep when something downstream enforces it.** XML tags, attributes, and schemas are not free. They impose verbosity, parsing cost, and a non-trivial cognitive load on whoever is writing prompts or reading raw output. The return is reduced ambiguity for parsers and models. If no parser, validator, or extraction step ever runs against the structure, the verbosity is dead weight.

The failure mode is predictable. A team adopts XML envelopes because Anthropic's docs use them, or they believe in the value of [XML Structured Prompting](https://aelena74.gumroad.com/l/xsp) in specific scenarios. They wrap every output in `<response>` and `<reasoning>` tags, but there is nothing downstream that parses the tags. The tags are thus just decoration, an illusion. They have paid the formalism cost without collecting the benefit, and the next engineer who joins assumes the structure is load-bearing and writes code around it that brittles fast from breaking changes upstream.

Pay for formalism only where it is enforced. Otherwise the simpler format is the correct call, and reaching for XML is over-engineering with extra steps.

## What this is really about

The format debate is interesting because it is a clean instance of a much larger habit: arguing the answer before rushing to agree on the question. Most technology decisions get hastily resolved like that. Build vs. buy. Microservices vs. monolith. Synchronous vs. event-driven. SQL vs. NoSQL. The arguments stay heated because they are conducted at the wrong altitude — a layer below the reframe that would dissolve them.

The better move, in formats and in everything else, is one level of altitude up. Not the default choice or "which format do we use here?" but "who has to read this next, and how many of them are there?". Not "build or buy?" but "is this differentiation surface or substrate?". Not "monolith or microservices?" but "what is the unit of independent deployment our team can actually operate?".

Get the altitude right and most arguments turn into routine engineering. Get it wrong and every meeting feels like litigation, because it is.

Rmember: XML is for the contract. HTML is for the interface. Markdown is for the conversation. JSON is for the wire. Pick the format for the next reader, not the current writer.
