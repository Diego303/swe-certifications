> **Origen de estas notas.** La página del curso (Skilljar, curso 8 de 8, ~8 min) se descargó el 2026-11-09, pero **el contenido está detrás de registro/login**: solo es pública la descripción, que se cita abajo. El repaso por dominios está **reconstruido** a partir de la guía oficial del examen CCAO-F (PDF v1.0, julio 2026, en `APUNTES-CURSOS/`) y de fuentes oficiales públicas de Anthropic (support.claude.com, academy.claude.com, platform.claude.com). Lo marcado **[INFERIDO]** es síntesis propia.
> **Fecha de investigación:** 2026-11-09.
> **Aviso:** precios, políticas del examen, nombres de modelos y funciones de los planes pueden cambiar. Verifica siempre en la guía del examen y en la Partner Academy.

# Course Summary & Next Steps

## 1. What the course officially says (public page)

> "At this stage, you have completed the modules covering the seven skills for operating Claude with confidence. This module teaches you how to tie these skills together into one discipline."
> "The module provides a recap to connect **selection, prompting, evaluation, integration, configuration, governance, and troubleshooting** into one workflow you can carry into real projects. The module then provides a brief overview of the Claude Certified Associate Foundations exam."

Course outline: not public.

Sources:
- https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations/course-summary-next-steps
- https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations

---

## 2. The seven skills as one workflow [INFERIDO – order follows the course's own list]

**Select → Prompt → Evaluate → Integrate → Configure → Govern → Troubleshoot** (and loop back)

1. **Select** the feature and model that fit the task.
2. **Prompt** with clear context, format, and examples; break big tasks into steps.
3. **Evaluate** the output before using it.
4. **Integrate** Claude into the real workflow, with a human at the right checkpoints.
5. **Configure** Projects, instructions, knowledge, and Skills so good setups are reused.
6. **Govern**: in every step, check what data and uses are allowed.
7. **Troubleshoot**: find the root cause and make the fix permanent.

---

## 3. Domain-by-domain recap (blueprint weights from the exam guide)

| # | Domain | Weight | Objectives (exam guide, condensed) | Key ideas to remember |
|---|---|---|---|---|
| 2 | Output Evaluation & Validation | **21%** | Accuracy/completeness; spot hallucinations, inconsistencies, bias; fact-check; decide when human review is needed; adapt for the audience; pick the output format (artifact, inline, structured data) | Verify specific claims (citations, numbers) against the authoritative source. Self-reported confidence is not a reliable signal (sample Q1). Ask for quotes and citations. Allow "I don't know". |
| 4 | Workflow Integration & Solution Design | **16%** | Analyze requirements/use cases; research, planning, process optimization; support solution design and iteration; augment or redesign workflows; communicate value and limits to stakeholders | Delegation (AI Fluency): decide what goes to Claude and what stays with people. Be honest with stakeholders about limitations. |
| 6 | Governance, Risk & Responsible Use | **15%** | Appropriate vs inappropriate use; data sensitivity, regulation, privacy; follow org AI policy; ethics | Anonymize or remove regulated identifiers before uploading. Telling Claude "not to retain" data does not satisfy a policy control (sample Q3). Diligence: you own the result. |
| 1 | Prompting & Task Execution | **14%** | Effective prompts; task decomposition; iteration; adapt strategy to the task type (analysis, research, drafting, brainstorming) | "Brilliant but new employee"; give context and the *why*; 3–5 examples; XML tags; say what to do, not what to avoid. |
| 3 | Product & Model Selection | **12%** | Choose the feature (Projects, research, chat, artifacts); tell Haiku, Sonnet and Opus apart; match cost, speed and quality; manage context limits (restart, summarize, persist) | Use a faster, cheaper model for simple high-volume work (sample Q2). Sonnet is the default; Opus is for hard reasoning. Start new chats for new topics. |
| 5 | Configuration & Knowledge Management | **12%** | Configure Projects (instructions and knowledge); manage uploads and connectors (Drive, Gmail); write system-level instructions; keep everything up to date | Project instructions apply to all chats in that project; keep them concise. Knowledge is shared across a project's chats, but chat context is not. Skills work everywhere and load only when relevant. |
| 7 | Troubleshooting & Optimization | **10%** | Diagnose underperforming prompts/outputs; adjust based on feedback; optimize workflows | 4 root causes: under-specification, context overload, wrong feature/model, stale configuration. Change one thing at a time. Promote repeated fixes into Projects, Skills, or instructions. |

Exam-strategy note [INFERIDO]: Domain 2 (21%) plus Domains 4 and 6 make up 52% of the exam, so prioritize evaluation, integration and governance judgement.

Sources:
- CCAO-F Exam Guide v1.0 §6 and §8 (local PDF)
- https://academy.claude.com/courses/ai-fluency-framework-foundations/the-4d-framework
- https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices
- https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations
- https://academy.claude.com/tutorials/choosing-the-right-claude-model
- https://support.claude.com/en/articles/9519177-how-can-i-create-and-manage-projects
- https://support.claude.com/en/articles/12512176-what-are-skills

---

## 4. Exam overview (exam guide v1.0 – verify before booking)

- Code **CCAO-F**; **60 items**, multiple-choice and multiple-response ("each item states how many responses to select"); **120 minutes**.
- Proctored by Pearson VUE (online or at a test center). Fee **$99 USD** (partner-tier discounts may apply at checkout).
- **Passing: scaled 720 on 100–1,000**. The exam is criterion-referenced (you are measured against a fixed standard, not against other candidates). The score report shows % correct per domain, but pass/fail depends only on the total score.
- Retakes: wait 14 days after the 1st fail, 30 after the 2nd, 90 after the 3rd; maximum 4 attempts in a rolling 12 months.
- Cancel or reschedule up to 24 h before the exam, otherwise you lose the fee. Bring a government photo ID that matches your registration name exactly.
- Valid for **12 months**. On-time renewal is a **free, non-proctored** assessment on the Partner Academy. If the credential lapses you must retake the full exam.
- No mandatory prerequisites. The guide recommends Projects, Artifacts, Memory, Skills and Code Execution docs, plus hands-on practice and the sample questions.

Source: CCAO-F Exam Guide v1.0 §5, §7, §9–§14.

---

## 5. Next steps: other certifications

- The exam guide says the Associate is not for people who "build against APIs or design agentic systems" or "enterprise-scale AI architectures or integrations". That scope "belongs to the **Claude Architect and Claude Developer** credentials, to which Associates escalate more complex or technical work."
- The Partner Academy currently lists: **Associate – Foundations**, **Developer – Foundations**, **Architect – Foundations**, **Architect – Professional** (plus a Claude Code partner badge, which is a course path, not an exam). Fees are shown on the site (volatile).
- [INFERIDO] Choose your next certification by role. If you will build with the API, take Developer. If you will design Claude solutions and agentic systems, take Architect (Foundations, then Professional). If you stay a business user, keep the Associate current with the free annual renewal.

Sources: CCAO-F Exam Guide v1.0 §1, §3 · https://anthropic-partners.skilljar.com/

---

## 6. Self-check quiz (4)

1. **Which domain has the highest weight, and what is its core habit?**
   → Output Evaluation & Validation (21%). Verify claims against authoritative sources before you share them, and decide when a human must review.
2. **What score do you need to pass, and is it relative to other candidates?**
   → A scaled 720 out of 100–1,000. It is criterion-referenced: you are measured against a fixed standard, not graded on a curve.
3. **A teammate wants Claude to call the CRM API automatically every night. Is this Associate scope?**
   → No. API and integration work is escalated to Claude Developers or Architects.
4. **Your credential expires in a month. What is the cheapest way to keep it?**
   → Renew before it lapses with the free, non-proctored renewal assessment on the Partner Academy. If it lapses, you must retake the full exam and pay the full fee.
