> **Origen de estas notas.** La página del curso (Skilljar, curso 7 de 8, ~30 min) se descargó el 2026-11-09, pero **las lecciones requieren registro/login**: solo están públicos la descripción ("About this course") y los 3 objetivos de aprendizaje, que se citan literalmente abajo. El resto está **reconstruido a partir de fuentes oficiales públicas de Anthropic**: la guía oficial del examen CCAO-F (PDF v1.0, julio 2026), docs de prompt engineering (platform.claude.com), artículos de support.claude.com (límites de uso/longitud, errores, respuestas incorrectas, Projects, Skills, memoria, personalización) y tutoriales/cursos de academy.claude.com (AI Fluency, elegir modelo, contexto, Skills). Lo marcado **[INFERIDO]** es síntesis propia, no texto oficial.
> **Fecha de investigación:** 2026-11-09.
> **Aviso:** tamaños de ventana de contexto, nombres de modelos, planes y nombres de menús cambian con frecuencia. Verifícalos en la fuente antes del examen.

# Troubleshooting & Optimization (Domain 7 – 10%)

## 1. What the course officially says (public page)

> "When an output disappoints, most people do one of two things: give up and conclude 'Claude can't do this,' or start changing random things until something works. This module replaces both by teaching you how to identify common failure patterns and promote a one-time fix into a permanent one."

**Learning objectives (literal):**
1. "Diagnose why a prompt or output is underperforming and trace it to its root cause: **under-specification, context overload, the wrong feature or model, or stale configuration**"
2. "Adjust your approach based on the output you get, **turning recurring corrections into fixes that persist** instead of repeating the same manual work"
3. "Optimize a workflow for efficiency by **promoting shared context, format, and verification steps into Projects, Skills, and standing instructions**"

**Exam blueprint – Domain 7 objectives (exam guide):**
- Identify, diagnose, and resolve issues with underperforming prompts or poor outputs
- Adjust approach based on feedback and results
- Optimize workflows for efficiency and effectiveness

Course outline: not public (lessons gated). The four root-cause families above are the course's own taxonomy — memorize them.

Sources:
- https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations/troubleshooting-optimization
- https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations
- CCAO-F Exam Guide v1.0 (local PDF in `APUNTES-CURSOS/`)

---

## 2. The diagnostic method

**Anti-patterns the course names:** (a) giving up ("Claude can't do this"), (b) changing random things until it works.

**Method [INFERIDO – structure; each step is backed by the sources cited]:**
1. **Name the symptom precisely.** What is wrong: facts, completeness, format, tone, length, it "forgot" something, it claims an action it didn't do?
2. **Define what "good" looks like.** Anthropic's docs assume, before prompt engineering, "a clear definition of the success criteria", "some ways to empirically test against those criteria" and "a first draft prompt you want to improve". Good criteria are specific and measurable (e.g. not "good performance" but "accurate sentiment classification").
3. **Locate the root cause** – check the four families in order: under-specification → context overload → wrong feature/model → stale configuration (table in §3).
4. **Change one thing at a time** and re-run on the **same test inputs**, comparing old vs new version against your criteria. [INFERIDO from "empirically test against criteria"; the Skills tutorial does the same: test in a new conversation and compare to your example.]
5. **Promote the fix** if the correction recurs: move it into project instructions, project knowledge, a Skill, or profile instructions so you stop fixing it by hand.
6. **Know when it is not a prompt problem.** Docs: "Not every success criterion or failing eval is best solved by prompt engineering. For example, you can sometimes improve latency and cost more easily by choosing a different model."

Key quote for root cause: "When an LLM produces incorrect information, it's usually a side-effect of missing, incorrect, or low-quality context." (Academy, context tutorial)

Sources:
- https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/overview
- https://platform.claude.com/docs/en/test-and-evaluate/develop-tests
- https://academy.claude.com/tutorials/parametric-memory-and-context

---

## 3. Symptom → root cause → fix

| Symptom | Likely root cause (course family) | Fix (official technique) |
|---|---|---|
| Generic, bland, "not what I meant" | **Under-specification**: missing context, audience, purpose | Be clear and direct; "Think of Claude as a brilliant but new employee who lacks context on your norms and workflows." Add the *why*: "Providing context or motivation behind your instructions… can give Claude more information about your goals." |
| Right content, wrong format/tone/length | **Under-specification** of the output | "Be specific about the output format and constraints you want." Give 3–5 relevant, diverse examples. "Tell Claude what to do instead of what not to do." Match your prompt style to the desired output style. |
| Steps skipped / incomplete on a multi-part task | **Under-specification / task too big** | Give "sequential steps using numbered lists" when order/completeness matters; decompose into smaller tasks; chain (draft → review against criteria → refine). |
| Instructions, data and examples get mixed up | **Under-specification (structure)** | Wrap content types in XML-style tags (`<instructions>`, `<context>`, `<example>`). |
| Invented facts, fake citations, confident errors | Missing/low-quality context; normal hallucination risk | Allow "I don't know"; ask for direct quotes first on long docs; ask it to cite and retract unsupported claims; restrict to provided documents; verify against the original source. |
| Claims it "sent an email" / broken links | **Wrong feature** (no tool connected) | Claude "can sometimes hallucinate its capabilities"; it can only use tools explicitly connected. Check connectors; do the final step yourself; test links. |
| Quality drifts late in a long chat, early details "forgotten", length-limit error | **Context overload** | Start a new chat with a short summary of the key decisions; split content; ask Claude to first identify the relevant portions; put stable material in project knowledge. Auto-summarization "can still occasionally result in lost details." |
| Long document answers miss the point | **Context overload / structure** | Put long documents at the top and the question at the end ("up to 30 percent" better in tests); ask for relevant quotes first. |
| Shallow reasoning on a hard problem | **Wrong model** (too light) or effort too low | Move up: Opus for "Problems where you've tested with Sonnet and it struggled". Raise effort for the hardest problems. |
| Slow / burns usage on simple tasks | **Wrong model** (too heavy) | "Using Opus on a task Haiku could handle costs you tokens for no gain and slows you down." Lower effort; Haiku for quick summaries/extraction. |
| Answers use outdated facts from project files | **Stale configuration** (old knowledge) | Update/replace the files in project knowledge; "Regularly clean up files you're no longer actively using in your projects." |
| Same correction needed every chat | **Stale/missing configuration** | Promote into project instructions or a Skill ("that's your cue to package them into a skill"). |
| Odd tone/behavior in every chat, or conflicting guidance | **Stale or conflicting configuration** across layers (profile instructions, project instructions, Skills, memory, the chat) | Audit each layer; keep project instructions short and general; put task-specific instructions in the chat; edit/delete stale memory topics. [Precedence between layers is NOT documented – INFERIDO: remove the conflict rather than rely on an order.] |
| A Skill "doesn't work" | Skill not triggered | If "Reading [skill name]" doesn't appear, the request "didn't match your skill's name or description": fix the name/description or mention the skill by name. |
| Project chat doesn't know what another chat decided | Wrong expectation of the feature | "Context is not shared across chats within a project unless the information is added into the project knowledge base." |

Sources:
- https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices
- https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations
- https://support.claude.com/en/articles/8525154-claude-is-providing-incorrect-or-misleading-responses-what-s-going-on
- https://support.claude.com/en/articles/8241188-claude-is-producing-links-that-don-t-work-and-falsely-claiming-that-it-has-sent-emails-or-produced-external-documents-what-s-going-on
- https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work
- https://support.claude.com/en/articles/12466728-troubleshoot-claude-error-messages
- https://academy.claude.com/tutorials/choosing-the-right-claude-model
- https://support.claude.com/en/articles/9519177-how-can-i-create-and-manage-projects
- https://academy.claude.com/tutorials/teach-claude-your-way-of-working-using-skills

---

## 4. Context management: restart vs continue

Official facts:
- Length limits "relate to Claude's context window—the amount of information Claude can work with in a single chat." You can't increase the window for your plan.
- Paid plans (with code execution): "When your conversation approaches the context window limit, Claude summarizes earlier messages"; full history is preserved for reference. But these longer conversations "consume more of your usage limit", and a summary "can still occasionally result in lost details."
- "Context is re-sent every turn" → "a short question late in a long conversation may cost more than the same question in a fresh one"; "starting a new chat can be the cheapest and fastest way to get an answer."
- Length-limit error fix: attach fewer/smaller files, split content, summarize key sections, ask Claude to identify the most relevant portions first, or start a new chat.
- Usage tip: "Try starting a new conversation if you're approaching your usage limit in a longer chat."
- Memory: chats in a project use that project's memory ("Each project has its own memory"); you can view/edit memory in Settings and ask Claude to forget something. Incognito chats aren't saved to memory.

**Decision rules [INFERIDO from the facts above]:**
- **Continue** when the task is the same and the recent context is still relevant.
- **Restart** when the topic changes, the chat is long and quality/cost degrades, or wrong assumptions have built up in the thread.
- **Summarize to carry over:** before restarting, ask Claude for a short summary (goal, decisions, constraints, open items), check it, paste it into the new chat.
- **Persist** (project knowledge / instructions / memory) anything you will need in many future chats — don't keep it alive in one endless thread.

Sources: https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work · https://academy.claude.com/tutorials/parametric-memory-and-context · https://support.claude.com/en/articles/11817273-use-claude-s-chat-search-and-memory-to-build-on-previous-context · https://support.claude.com/en/articles/12466728-troubleshoot-claude-error-messages

---

## 5. Feedback loops and turning fixes into permanent ones

- **Description–Discernment loop (AI Fluency):** Describe → Discern → Refine → Integrate. Refine = "Provide feedback on what worked and what didn't", "Clarify or adjust your description as needed", "Request iterations until you're satisfied with the result."
- **Self-correction pattern (docs):** "generate a draft → have Claude review it against criteria → have Claude refine based on the review."
- **Best-of-N:** run the same prompt several times and compare; "Inconsistencies across outputs could indicate hallucinations."
- **Thumbs-down feedback** in the app reports unhelpful responses to Anthropic. It does not fix your workflow. [INFERIDO]

**Where to put a recurring fix (promotion ladder):**

| Fix type | Put it in | Official basis |
|---|---|---|
| One-off task | A good prompt in the chat | "When you need Claude to do something once, just prompt well." |
| Shared background docs for a body of work | **Project knowledge** | "Anything you upload to this space will be used across all of your chats within that project." |
| Role, tone, key rules for one body of work | **Project instructions** (short) | "Keep your project instructions concise and focused on essential information… Reserve task-specific instructions for the chat itself." |
| A procedure/format/verification checklist you repeat anywhere | **Skill** | Create one "when you've figured out how you want a task done and want Claude to follow that approach consistently"; "Skills work everywhere." Requires code execution. |
| Preferences for all your chats | **Profile instructions** (Settings) | "Instructions are account-wide settings." |

Testing a promoted fix: "Open a new conversation and ask for the task the way you normally would"; "Anything you'd still fix by hand is a line worth sharpening in the skill itself."

Sources: https://academy.claude.com/courses/ai-fluency-framework-foundations/the-description-discernment-loop · https://academy.claude.com/tutorials/teach-claude-your-way-of-working-using-skills · https://support.claude.com/en/articles/12512176-what-are-skills · https://support.claude.com/en/articles/10185728-understanding-claude-s-personalization-features · https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work

---

## 6. Optimizing for efficiency and effectiveness

- **Right-size the model:** Haiku = quick answers, summaries, simple extraction; Sonnet = "your versatile default"; Opus = deep research/complex reasoning ("reserve it for tasks that really need it"); Fable = largest, most critical long tasks. Default effort "is the right balance for most work." (Model names/lineup are volatile.)
- **Save usage:** remove unused project files; lower effort when you don't need deep reasoning; "Tools and connectors are token-intensive", so turn on only what the task needs.
- **Templates/reusable prompts [INFERIDO]:** keep a tested prompt that has worked; if you reuse it often, turn it into a Skill or project instructions.
- **Measure it [INFERIDO]:** compare time per task and the number of manual corrections before vs after a change, using the same inputs and your success criteria. Note: the lighter model is enough if it "covers everything you would have flagged yourself."

Sources: https://academy.claude.com/tutorials/choosing-the-right-claude-model · https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work

---

## 7. When to escalate

Exam guide: Associates are expected to recognize "limitations and escalat[e] more complex or technical work to Claude Architects and Developers." Out of scope for Associates: building "against APIs", designing "agentic systems", "enterprise-scale AI architectures or integrations".

**Escalate [INFERIDO]** when the fix needs: API integration or automation beyond built-in features, custom connectors or system integrations, high-volume pipelines, or changes to org-wide admin/governance settings. Escalate to compliance/legal (Domain 6) when the problem is about policy or data.

Source: CCAO-F Exam Guide v1.0, §1 and §3.

---

## 8. Common mistakes

- Concluding "Claude can't do this" after one bad output, or changing many things at once (both named by the course).
- Re-typing the same correction in every chat instead of promoting it (objective 2).
- Telling Claude only what *not* to do instead of what to do.
- Treating confident output as correct, or asking Claude to rate its own confidence. The exam guide says self-reported confidence "is not a reliable accuracy signal."
- Believing Claude sent an email or created an external file without checking.
- Keeping one endless chat for unrelated topics; expecting project chats to share context with each other.
- Leaving outdated files in project knowledge; making project instructions long and task-specific.
- Defaulting to the most powerful model for everything (wastes cost and latency), or staying on a light model when it keeps failing.
- Trying to fix with prompting what needs a different model, feature, or an escalation.

---

## 9. Self-check quiz (8)

1. **A weekly report prompt gives generic output. The colleague test shows a newcomer wouldn't know the audience or purpose. Root-cause family?**
   → Under-specification. Fix: add context and motivation (audience, purpose, format), plus examples.
2. **You fixed the format, tone, and length all at once and the output improved. What is the problem with this approach?**
   → You can't tell which change helped. Change one variable at a time and compare on the same test inputs.
3. **In every chat in a Project you have to remind Claude "use our 5-section template." Best fix?**
   → Promote it: a short line in project instructions, or a Skill if the template is a procedure you use in many places. Don't keep correcting it by hand.
4. **Claude cites last year's price list although you uploaded the new one weeks ago. Likely cause?**
   → Stale configuration: the old file is still in project knowledge. Remove or replace it, then retest in a new chat.
5. **A 3-hour chat now ignores constraints agreed at the start. What should you do?**
   → Context overload. Ask for a summary of the goal, decisions, and constraints, check it, and start a new chat with it. Persist stable info in project knowledge or instructions.
6. **Claude says "I've emailed the client." What do you do?**
   → Don't assume it happened. Claude can only use connected tools and "can sometimes hallucinate its capabilities". Check your sent mail or the connector, or send it yourself.
7. **Sonnet keeps failing a complex multi-document analysis even with a well-specified prompt. Next step?**
   → Wrong model or effort for the task. Try Opus or a higher effort level (move up when a lighter model has struggled). Not everything is solved by prompt engineering.
8. **Which is NOT a reliable way to validate a factual claim? (a) Ask Claude for supporting quotes (b) Check the original source (c) Ask Claude to rate its confidence (d) Compare several runs**
   → (c). Self-reported confidence is not a reliable accuracy signal (exam guide, sample 1).
