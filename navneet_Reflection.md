# Reflection.md
**Navneet Kaur | BDA400 | markdown-buddy-navneet**

---

**AI Assistance Declaration:** I used Claude (Anthropic) to generate a starting framework for these reflection responses. Prompt: "What should a student reflect on after completing an AI-assisted documentation project?" I used the AI's output as a list of questions to answer in my own voice, not as text to quote or paraphrase. Everything below is written independently. I am responsible for the accuracy and originality of this work.

---

### Reflection One: What did AI do well in this assignment?

Let me start with something specific rather than general: the AI was exceptionally good at producing *formatted* documentation on first attempt. Headers used consistent levels, tables rendered immediately, code fences had proper syntax highlighting. Markdown has enough quirks — escaped characters, table alignment rows, nested blockquotes — that a first draft without syntax errors is genuinely valuable.

Beyond formatting, there was a subtler benefit. Because I was asking AI to help me describe the project to a generalist reader, I was forced to think of my project *as* a generalist reader would encounter it. The AI's draft assumed nothing about my scripts — it described the project from zero context. Reading that draft helped me identify every place where I had assumed readers would share context they don't have.

Concretely: the AI's version of my README didn't mention `renv`. I use it so routinely that I forgot to document it. A user who cloned my repository without `renv` knowledge would have no idea why `renv::restore()` appeared in the setup instructions. Adding the "Reproducing on a New Machine" section was a direct result of noticing that gap.

---

### Reflection Two: Where did the process break down?

There's a specific failure mode I want to name: the AI optimised for *completeness* rather than *relevance*. Given any project description, it would add sections until the README looked impressively comprehensive. A changelog. A citation guide for academic use. A community code of conduct. A roadmap.

None of those were appropriate for a course project. But they weren't obviously wrong either — they would all be appropriate in a different context. The AI had no mechanism for asking "does this project actually need a roadmap?" It just added one because professional open-source READMEs often have them.

This matters beyond the immediate assignment. If I had accepted the AI's output without review, my README would have contained documentation of features that don't exist ("future releases will include sentiment analysis") and processes that aren't relevant ("submit issues via GitHub Issues"). That would have been misleading, not just unnecessary.

The verification step — reading the README against the actual repository structure — eliminated all of it. But it required me to have enough context about the project to recognise what didn't belong.

---

### Reflection Three: Has this changed anything about how you'll approach data science work?

Documentation has always felt like a tax on the real work. You build something, it functions correctly, and then you spend additional time explaining what you built to people who weren't there. This assignment changed that framing slightly.

Writing `segment_analysis.Rmd` while thinking about what a reader would need to know forced me to document two edge cases I had noticed while testing but hadn't explicitly decided how to handle: the empty-category problem and the paid-post mixing in hourly averages. Both were sitting in my notes as "to-do" items. The act of writing "this could cause display issues if the category is expected to always appear" made it obvious that I needed to handle it, not just note it.

This is the argument for documentation as a thinking tool rather than an afterthought — an argument the assignment made implicitly, and that working through it made explicit. AI accelerates the formatting and structure of documentation. The thinking part — what to document, what it means, what the limitations are — remains unchanged. If anything, AI makes that part more visible by handling the other part so quickly.

---

*markdown-buddy-navneet | BDA400 Data Science Tools and Techniques*
