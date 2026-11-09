# Voice Kit

Lets any AI write in one person's voice (here, the author of a hobbyist tech blog), or rewrite existing text in that voice, then strip the AI habits back out. Swap in your own profile and samples to use it for someone else.

## What these are called
- **Voice profile** (also called a style guide or writing persona): the description of how the author writes. File 1.
- **Custom instructions** or **system prompt**: the box for standing directions an AI follows for the whole chat. The voice profile goes there.
- **Writing samples** (AI people call them "few-shot examples"): real pieces of the author's writing for it to match. File 2.
- **Prompt**: the one-off ask typed each time.
- **Editing pass**: a second prompt that edits the draft. Here that's the cleanup pass, File 3.

## Set Up Once
Put `1-voice-profile.md` in the instructions box and attach `2-writing-samples.md` as a file.
- ChatGPT: make a Project or a custom GPT. Profile into Instructions, samples into its files.
- Claude: make a Project. Profile into the project instructions, samples into project knowledge.
- Gemini: make a Gem. Profile into its instructions, samples as a file.
- Anything else (another chat app, a local model, an API): paste both at the very top, as the system prompt or the start of the first message.

## Write New Text
```
Write a blog post in the author's voice about: ___
Sources and notes: ___  (links, notes, numbers, quotes)
My own bit (optional): ___  (something real you own, did or saw)
Format: Blogger HTML / plain text
```

## Edit Existing Text
```
Rewrite the text below in the author's voice. Keep every fact, number, name, quote, code and link exactly as it is. Plain text, no titles or labels.

___
```

## Clean It
In a new chat, paste `3-cleanup-pass.md`, then the draft. Use the cleaned version.

Use this cleanup pass for the author's voice, not `guardrails/anti-ai-slop.md`. It protects the ellipses, the glued hyphen dash and the asides, which the generic guardrail doesn't know about.

## From the Command Line
```bash
cat voice/1-voice-profile.md voice/2-writing-samples.md notes.txt | llm "Write a blog post in the author's voice from these notes. Format: plain text." > draft.txt
cat voice/3-cleanup-pass.md draft.txt | llm > final.txt
```

## Why Two Passes
Handing an AI a list of "don't sound like AI" rules while it writes makes it sound more like AI, because it writes around the list. So it writes with the voice and the samples only, and the don't-list runs afterwards as an edit.

## Check Before Using
- Numbers, names, quotes and links match the sources.
- No "I" claims the author didn't give it: gear, prices, tests.
- No staccato: no run of short clipped sentences or fragments.
- A blog post ends on a question to readers and then the links, not a neat moral.
