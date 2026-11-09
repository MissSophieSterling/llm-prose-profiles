# LLM Prose Profiles & Anti-Slop Guardrails

A reusable voice kit (one author's writing voice for any LLM), plus modular style profiles that replace choppy, staccato "AI blog voice" (parataxis, asyndeton, standalone punches) with smooth, flowing prose. Flow comes from subordination, not from longer words.

Updated 2026-11-08.

## Voice Kit

`voice/` is a complete voice kit for one author: a profile, real writing samples and a matching cleanup pass. Use it for anything written as that author or rewritten into their voice: posts, extracts, emails, docs. Replace the profile and samples with your own to adapt it. It keeps the author's hyphen dash and ellipses, bans staccato, and runs its own removal-only cleanup pass afterwards. Setup for each kind of tool is in `voice/README.md`.

## Generic Style Profiles

Run these in two passes: draft with a **Style Profile** first, then apply the **Anti-AI Slop Guardrail** as a separate removal pass over the finished draft. Keeping the banned-word list out of the drafting context stops it from priming the model toward the very words it bans.

```bash
# Pass 1: rewrite the draft in the Unhurried Narrative style
cat styles/01-hypotactic-narrative.md draft.txt | llm "Rewrite the draft following the provided style specification." > pass1.txt

# Pass 2: remove synthetic patterns without changing facts or style
cat guardrails/anti-ai-slop.md pass1.txt | llm "Edit the text to remove every pattern the guardrail bans. Change nothing else." > final.txt
```

With `01a`, add "Leave the glued hyphen dashes and the ellipses as they are." to the pass 2 instruction so the edit doesn't convert them.

Every style profile ends its output with a `Dropped:` line naming any source detail it could not keep. Read it, restore what matters, then delete the line before pass 2.

## Included Files

* **`voice/`**: Voice profile, writing samples and cleanup pass for one author, with write and edit modes.
* **`guardrails/anti-ai-slop.md`**: Strips out RLHF clichés ("It's not X, it's Y", "delve", rule-of-three lists, moralizing conclusions).
* **`styles/01-hypotactic-narrative.md`**: Blends long-form magazine warmth with technical reference authority. Unhurried pacing, 100% detail retention, no added claims, plain words, one short factual sentence per paragraph allowed.
* **`styles/01a-hypotactic-narrative-hyphens-and-ellipses.md`**: Profile 01 with the conversational hyphen dash ("like this- and on") and ellipses of two to five dots kept.
* **`styles/02-hypotactic-compressed.md`**: High-density version of Profile 01. Achieves brevity, measured in characters, through syntactic synthesis and the shorter plain word rather than choppy sentence clipping.
* **`styles/03-dry-architectural.md`**: Impersonal, objective engineering prose modeled after classic UNIX textbooks and RFCs.

## Revisions
* 2026-11-08: Generalized the voice kit for public sharing: the author is now referred to as "the author" throughout.
* 2026-11-04: Removed the multi-syllabic vocabulary rule from `01`, `01a` and `02` and replaced it with a plain-words register. Preservation rule in every profile now bans added claims, keeps quotations verbatim with their named source, keeps standard names for symbols and tools, and ends with a `Dropped:` line. One short factual sentence per paragraph is allowed and sentence-initial connectives are capped at one per paragraph. Guardrail adds "less X, more Y", connective openers in series, uniform sentence length and a lexical-inflation list. `03` keeps everyday words that are themselves the technical term. `01` and `01a` carry a reference sample.
* 2026-10-29: `voice/` became the voice kit master; `01a` added.
* 2026-10-28: Initial profiles and guardrail.
