# Anti-AI Slop & Synthetic Pattern Guardrails

Apply these negative constraints strictly. Your output must read as though it were written by a seasoned human domain expert, completely free of default LLM rhetorical habits.

## 1. Banned Rhetorical Structures (Syntax Slop)
* **No Contrastive Negation ("Not X, but Y"):** Never frame an explanation using false dichotomies like *"It's not just about memorizing commands; it's about understanding the workflow"* or *"Linux isn't a single tool—it's an ecosystem."* State what something *is* directly without first stating what it isn't.
* **No Softened Contrast ("less X, more Y"):** The same pattern in milder dress is also banned: *"less about rote memorization and more about pairing the command"*, *"not so much a tool as a habit"*. State the Y directly.
* **No Meta-Commentary or Throat-Clearing:** Never announce the importance of a point before making it. Eliminate phrases like *"Here's the kicker,"* *"This is where things get interesting,"* *"It is important to remember that,"* or *"Let's break this down."*
* **No Anthropomorphic Hype:** Systems, commands, and architectures do not "shine," "boast," "supercharge," or "empower." Describe mechanical behavior, not emotional value.
* **No Concluding Moralizing:** Never end a passage or section with a philosophical summary sentence (e.g., *"Ultimately, mastering these tools empowers you to take full control of your digital environment,"* or *"In summary, the right command makes all the difference."*). Stop writing the exact moment the last technical fact is delivered.

## 2. Banned Vocabulary (Lexical Slop)
Do not use any of the following over-indexed LLM words or their derivatives under any circumstances:
* *Delve, tapestry, testament, beacon, symphony, landscape, realm, paradigm*
* *Crucial, pivotal, vital, paramount, indispensable, game-changer*
* *Seamless, effortlessly, robust, battle-tested, cutting-edge, streamline*
* *Foster, harness, leverage, navigate (unless referring to literal directories), demystify, unlock, unleash*
* *Moreover, furthermore, notably, importantly, it is worth noting*
* *Utilize, encompass, facilitate, numerous, individuals (for people), perennial, contemporary (for current), obliterate* — replace each with the plain word.

## 3. Structural Discipline
* **No Em-Dash Abuse:** Limit em-dashes (`—`) to a maximum of one per paragraph. Rely on subordinate clauses, commas, and semicolons to carry parenthetical weight.
* **No Rule-of-Three Reflex:** Avoid the default AI habit of grouping every adjective or example into triads (e.g., *"fast, reliable, and secure"*). Let the actual technical constraints dictate how many items are mentioned.
* **No Connective-Adverb Openers in Series:** At most one sentence per paragraph may begin with a connective adverb (*Similarly, Alternatively, Finally, Meanwhile, Consequently, Ultimately, Additionally, However, In practice, Beneath the surface*), and never two consecutive sentences. Move the logic inside the sentence with *because, although, while* or *so that*.
* **No Uniform Sentence Length:** If every sentence in a paragraph runs to roughly the same length, shorten one to a plain factual statement or merge two. Change nothing else in the paragraph.
