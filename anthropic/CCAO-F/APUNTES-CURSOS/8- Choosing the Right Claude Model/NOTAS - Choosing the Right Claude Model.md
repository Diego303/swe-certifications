> **Origen de estas notas**
> - **Página del curso consultada:** sí. El tutorial de Anthropic Academy *"Choosing the right Claude model: Haiku, Sonnet, Opus, or Fable"* (https://academy.claude.com/tutorials/choosing-the-right-claude-model) es **público** (no requiere login) y es un tutorial de ~5 minutos sin lista formal de objetivos. Las secciones de abajo siguen su estructura real (6 secciones).
> - La versión en español (`/es/`) existe pero no devolvió contenido legible, así que se usó la versión en inglés.
> - **Fuentes oficiales complementarias** (para ampliar, marcadas como tales en cada sección): Claude Help Center (support.claude.com) — artículos de *extended thinking/effort* y de *cambio de modelo con Fable 5*; Claude Platform Docs (platform.claude.com) — *Models overview* y *Choosing the right model*.
> - **Fecha de la investigación:** 2026-11-09.
> - ⚠️ **Datos volátiles:** precios, ventanas de contexto, números de versión de modelos (5.5, 5.2…), niveles de effort por defecto y qué modelo incluye cada plan cambian con frecuencia. **Compruébalos antes del examen** en las URLs indicadas.
> - Lo que no está escrito literalmente en una fuente oficial se marca como **[INFERIDO]**.

# Choosing the Right Claude Model: Haiku, Sonnet, Opus, or Fable

**Course framing (quote):** a 5-minute tutorial on when to use each of the four Claude models "to get better results while staying within your rate limit."

**Course outline (6 sections):**
1. Meet the four models
2. Understanding rate limits
3. When to use each model
4. What this looks like in practice
5. Try the same task on two models
6. Choosing models over time

Source: https://academy.claude.com/tutorials/choosing-the-right-claude-model

---

## 1. Meet the four models

| Model | How the course describes it (quotes) | Rate-limit "weight" |
|---|---|---|
| **Haiku** | "our fastest model and our most capable Haiku yet, built for everyday requests" | Lightest |
| **Sonnet** | The "daily driver" — "If you're not sure which model to pick, start here." | Moderate |
| **Opus** | "built for problems that genuinely need deep thinking over time" | Heavy |
| **Fable** | For "Your largest, most critical projects" | Heaviest ("uses the most of your limit") |

Key ideas:
- The four models form a **ladder**: lighter/faster → heavier/deeper. The heavier the model, the more of your rate limit it consumes.
- **Default rule of thumb for a business user in the Claude app: start with Sonnet when unsure.**
- **Fable** is the newest top tier. The course describes it as the model that "plans the steps, checks its own work, and keeps working on long tasks with fewer mid-task check-ins"; responses take longer and it uses the most rate limit.

**Plan availability (as stated in the course — volatile):**
- "Free includes Haiku and Sonnet."
- "Opus is available on Pro plans and above."
- "Fable is available on paid plans."
- Pro, Max and Ultra add Opus, Fable and more headroom.

**What Fable is, from the official docs (complement):**
- Claude Platform Docs: Claude Fable 5.2 is "Anthropic's most capable model open to all customers. It's built for demanding reasoning and long-horizon agentic work."
- A sibling model, **Claude Mythos**, offers the same capabilities "only to organizations verified through Anthropic's verification programs" (e.g. the Cyber Verification Program). For a business user this is background only.

Sources: https://academy.claude.com/tutorials/choosing-the-right-claude-model · https://platform.claude.com/docs/en/about-claude/models/choosing-a-model

---

## 2. Understanding rate limits

Core quotes from the course:
- "Your rate limit caps how many tokens you can use in a given time window."
- "Models like Opus and Fable use more tokens because they do more reasoning."
- "if you use Opus or Fable on a task that Sonnet or Haiku could handle, you may be using more of your limit unnecessarily."

**Effort setting (in the course):**
- "The Effort setting in the model picker adjusts this directly."
- "the default level is the right balance for most work."
- Lower effort → faster, lighter answers. Save the highest setting for the hardest problems.

> The course does **not** say what happens when you hit the limit or when it resets — don't assume specifics for the exam.

**Complement — Help Center "Using extended thinking" (model menu, effort, thinking):**
- The model menu next to the send button controls three settings: **model, effort level, and thinking**. Changes apply "starting with Claude's next response."
- Effort "controls how much thinking Claude applies to a response." Higher effort gives more thorough answers, but "they take longer and use more tokens, so you'll reach your usage limits faster."
- Levels: **Low** and **Medium** for routine tasks · **High** = best overall balance · **Extra high (xhigh)** for long-running coding/agentic tasks · **Max** for the deepest reasoning. Each model marks one level as "Default".
- **Thinking and effort are separate settings.** On some current models thinking is always on and can't be turned off in Claude; there you **lower effort** to make Claude think less.
- When thinking is on, an expandable "Thinking" section shows a **summary** of Claude's approach — useful to verify reasoning.
- For everyday tasks the defaults work well, and lower effort "stretches your usage further." For complex work (proofs, project planning, detailed document analysis, multi-step technical problems) raise effort, turn on thinking, or both. For the most correctness-critical work choose Max and "expect longer response times."

Sources: https://academy.claude.com/tutorials/choosing-the-right-claude-model · https://support.claude.com/en/articles/10574485-using-extended-thinking

---

## 3. When to use each model

The course's guiding principle: "it's best to consider what kind of output you're looking for from Claude and choose your model accordingly."

| Model | Use it for (course quotes) |
|---|---|
| **Haiku** | "Anything you want done instantly without complex reasoning" — quick answers, summaries, simple extraction, lookups |
| **Sonnet** | "Most 'general purpose' work where you're not sure which model to use" — everyday coding, writing, analysis, multi-step work |
| **Opus** | "Problems where you've tested with Sonnet and it struggled" — deep research, complex reasoning |
| **Fable** | "Work where you'd rather describe the outcome and let Claude plan the steps" — large, long-horizon projects |

**Decision rules to memorize:**
1. **Unsure → Sonnet.**
2. **Simple / instant / no complex reasoning → Haiku** (saves rate limit).
3. **Move up to Opus only after Sonnet struggled** ("tested with Sonnet and it struggled") — escalate based on evidence, not by default.
4. **Fable when you want to hand over an outcome**, not steps, on large/critical/long projects — accepting slower responses and heaviest limit use.
5. **Before switching model, consider the Effort setting** (default is right for most work; lower for speed; highest only for the hardest problems).

**Model switching on sensitive topics (course):** on some biology and security topics, "Claude may switch to a different model than the one you picked," and "it tells you when it does."

**Complement — Help Center "Why Claude switched models… with Fable 5":**
- Fable models run safety classifiers on every request. Requests on **offensive cybersecurity**, many **dual-use biology** topics, and a narrow set of **frontier LLM development** tasks may be redirected to a less capable model (an Opus model).
- In Claude apps automatic switching is **on by default**; you see a notice that the model switched and the response is labeled with the model that answered.
- Classifiers also review content Claude reads (files, connector content, web results, memory), so a switch can be triggered by material you didn't type.
- You can switch back from the model picker (editing the earlier message often helps), or turn off "Switch models when a message is flagged" in Settings > Capabilities (the conversation then pauses on a blocked request instead).

Sources: https://academy.claude.com/tutorials/choosing-the-right-claude-model · https://support.claude.com/en/articles/15363606-why-claude-switched-models-in-your-conversation-with-fable-5

---

## 4. What this looks like in practice

Course table (literal):

| Task | Model | Why |
|---|---|---|
| Summarizing articles | **Haiku** | "Straightforward content extraction without complex reasoning" |
| Debugging code | **Sonnet** | "Exceptional coding capabilities, fast feedback, and clear bug identification" |
| Analyzing complex research papers | **Opus** | "Deep analysis across long specialized documents, including methodology critique and forward-looking insights" |
| Building a working project from a rough idea | **Fable** | "Plans the steps, checks its own work, and keeps working on long tasks with fewer mid-task check-ins" |

Extra business-user examples **[INFERIDO]** (by analogy with the table, not from the course): reformatting a list / quick email reply → Haiku; drafting a report or analyzing a spreadsheet → Sonnet; critiquing a long contract or multi-source strategic analysis where Sonnet missed points → Opus; "turn these 20 files into a finished board deck and supporting analysis" → Fable.

Source: https://academy.claude.com/tutorials/choosing-the-right-claude-model

---

## 5. Try the same task on two models

The exercise:
1. Run the same summarize-and-flag prompt on **Haiku**.
2. Run it again on **Sonnet**, in a **new chat**.
3. "Compare where the answers differ, not how long they are."
4. Judge each answer against what you already know about the source.

Takeaways (quotes):
- "if Haiku's summary covers everything you would have flagged yourself, the task is Haiku-shaped."
- "Save Sonnet, Opus, and Fable for the work where the lighter answer misses things that matter."

Why it matters: model choice should be **evidence-based** — test on your real task, compare **substance (coverage, accuracy)**, not length.

Source: https://academy.claude.com/tutorials/choosing-the-right-claude-model

---

## 6. Choosing models over time

- "Each new model brings its own strengths," so the tasks worth trying change with each release.
- "When a new model comes out, try out more ambitious tasks that may have hit a ceiling in the past."
- Free users can upgrade for "access to all models and a higher rate limit."
- How to choose in the app: use the **model picker** — "select it from the model picker when a task needs it."

Source: https://academy.claude.com/tutorials/choosing-the-right-claude-model

---

## Complement: official "choosing a model" framework (Claude Platform Docs)

Written for developers/API, but the reasoning is useful and consistent with the course:

- **Criteria:** capabilities, speed, cost — and **effort**: "Tuning effort is often a better lever than switching models."
- **Two starting strategies:**
  - **Efficiency-first:** start with the fast, cheap model (Haiku), test, "Upgrade only if necessary for specific capability gaps." Best for prototyping, tight latency, cost-sensitive, high-volume straightforward tasks.
  - **Capability-first:** start with the strongest model for the task, then optimize down (lower effort or cheaper model). Best for complex reasoning, nuanced understanding, accuracy over cost.
- **Testing:** build tests with your actual prompts/data; compare accuracy, quality, edge cases; weigh performance vs cost.
- Positioning in the docs' comparison table (volatile): Fable = demanding reasoning & long-horizon agentic work · Opus = long-running agentic coding and knowledge work · Sonnet = "The best combination of speed and intelligence" · Haiku = high-volume, latency-sensitive tasks (classification, extraction, routing). Latency: Haiku fastest, Sonnet fast, Opus/Fable moderate.

⚠️ **Don't mix the two contexts on the exam:** the **Academy tutorial (Claude app, business user, rate limits)** says *"if unsure, start with Sonnet"*. The **API docs** currently say most API workloads start with Opus. For CCAO-F (business users, no API) the course's Sonnet-first rule is the one to apply. **[INFERIDO]**

Sources: https://platform.claude.com/docs/en/about-claude/models/choosing-a-model · https://platform.claude.com/docs/en/about-claude/models/overview

---

## Common mistakes

- Using Opus/Fable "just in case" for simple tasks → burns rate limit unnecessarily.
- Jumping straight to Opus without first checking whether Sonnet handles it (course: Opus is for problems "where you've tested with Sonnet and it struggled").
- Comparing models by **answer length** instead of by **what each one catches or misses**.
- Forgetting the **Effort** setting — raising effort or lowering it can be a better lever than changing model.
- Expecting Fable to be fast: it takes longer and uses the most limit; it's for long, outcome-driven projects.
- Being surprised by a model switch on biology/security topics — Claude tells you when it switches.
- Assuming every plan has every model: Free = Haiku + Sonnet (per course; check current plans).

---

## Self-check quiz

1. **You're not sure which model a task needs. Which model does the course recommend starting with?**
   → Sonnet ("If you're not sure which model to pick, start here").

2. **Why can using Opus or Fable for a simple task be a problem?**
   → They use more tokens because they do more reasoning, so you consume more of your rate limit unnecessarily.

3. **Which model for summarizing a batch of articles, and why?**
   → Haiku — "Straightforward content extraction without complex reasoning."

4. **When does the course say to move up to Opus?**
   → For "Problems where you've tested with Sonnet and it struggled" (deep research, complex reasoning).

5. **What distinguishes Fable from the other models?**
   → It's for the largest, most critical, long-horizon projects where you "describe the outcome and let Claude plan the steps"; it plans, checks its own work, needs fewer mid-task check-ins, but is slower and uses the most rate limit. Available on paid plans.

6. **In the Haiku-vs-Sonnet exercise, what should you compare?**
   → "where the answers differ, not how long they are" — if Haiku covers everything you'd flag, the task is "Haiku-shaped."

7. **What does the Effort setting do, and what's the default advice?**
   → It adjusts how much thinking Claude applies (in the model picker). The default is right for most work; lower it for faster/lighter answers; save the highest for the hardest problems. Higher effort = slower and uses limits faster.

8. **You asked Fable a biology question and the answer came from a different model. What happened?**
   → On some biology and security topics Claude may switch to a different model than the one you picked, and it tells you when it does.
