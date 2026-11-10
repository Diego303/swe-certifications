> **Origen de estas notas.** La página del curso (https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations/governance-risk-responsible-use) se descargó el 2026-11-09. Es pública solo la ficha: eslogan, texto "About this course", los 4 objetivos y la duración (55 min, curso 6 de 8). **El temario de lecciones y su contenido requieren registro y NO se han podido leer.** Por eso el cuerpo sigue los 4 objetivos oficiales y está **reconstruido a partir de fuentes oficiales públicas de Anthropic**: Usage Policy (anthropic.com/legal/aup), artículos de privacy.claude.com y support.claude.com (entrenamiento, retención, chats incógnito, retención en Enterprise, HIPAA, skills), y material oficial de cursos de Anthropic incluido en el HTML público de Skilljar (resúmenes de AI Fluency y la lección "Best practices for working safely" del curso de Cowork). También se ha usado la guía del examen resumida en `../Guia.md`.
> Lo que es deducción mía y no aparece en una fuente oficial va marcado **[INFERIDO]**.
> **Aviso:** los plazos de retención, las funciones de cada plan, la lista de áreas de alto riesgo y la fecha de vigencia de la Usage Policy cambian con frecuencia. Compruébalos en las URLs antes del examen. La AUP consultada dice "Effective Nov 12, 2026", así que es posible que el examen se escribiera con la versión anterior.

# Governance, Risk & Responsible Use (Course 6 of 8, about 55 min)

## 0. Course framing (from the public course page)

Source: https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations/governance-risk-responsible-use

- Tagline: *"Build the judgement to decide what is safe and appropriate to bring to Claude."*
- About (quoted): *"Most people don't think about governance until something goes wrong whether it's a file uploaded where it shouldn't be or a Skill with too much access. Either one of these issues can put a hold on Claude for an entire team."*
- The page says avoiding these problems *"primarily comes down to judgment you can learn"*, which it breaks into three parts:
  1. **"knowing what's fair game"**: which use cases are appropriate (Objective 1)
  2. **"what your data and industry allow"**: data sensitivity and regulation (Objective 2)
  3. **"which rules your organization has in place"**: organizational policy (Objective 3)
- Learning objectives (official, and identical to exam Domain 6, weighted 15%):
  1. Identify appropriate and inappropriate use cases
  2. Apply data sensitivity, privacy, and regulatory considerations to Claude use
  3. Follow organizational AI policies and governance standards
  4. Understand the ethical implications of AI usage
- The course card on the Claude Associate path describes it as: *"Data sensitivity, what not to put where, and the judgment calls of everyday use."*

**Mental model for the exam [INFERIDO from the framing above]:** before you bring something to Claude, ask three questions in order.

1. Is this a use I'm allowed to make?
2. Is this data I'm allowed to share, here, on this plan?
3. Does my organization's policy allow it?

If any answer is "no" or "not sure", fix the input or escalate before you proceed. Abandoning the task is not the answer.

---

## 1. Identify appropriate and inappropriate use cases

Source: https://www.anthropic.com/legal/aup (Usage Policy, page dated "Effective Nov 12, 2026")

### 1.1 Structure of the Usage Policy
| Part | What it covers |
|---|---|
| **Universal Usage Standards** | Apply to everyone. They prohibit, among other things, illegal activity, privacy violations, surveillance, fraud, deception and disinformation, election interference, weapons, child safety violations, and platform abuse. They open with "Do Not Violate Applicable Laws or Engage in Illegal Activity". |
| **High-risk Use Case Requirements** | Extra controls for uses that affect health, legal rights, finances, livelihoods, or access to housing, education, or essential services. |
| **Additional Use Case Guidelines** | Consumer-facing chatbots and agents, products serving minors, agentic use, and others. |

### 1.2 High-risk areas, where a human must decide
The current AUP lists 11 "High-risk Areas": **Legal; Medical; Finance; Credit; Insurance; Housing; Employment; Education and credentials; Healthcare access; Public benefits and services; Legal status and adjudication.**
(Earlier versions grouped these as legal, healthcare, insurance, finance, employment & housing, academic testing, and media/journalism. Check which version applies.)

There are two key requirements when Claude produces a recommendation in a high-risk area:
- **Human-in-the-loop:** *"A qualified person must meaningfully review"* the recommendation, *"with the authority to change or modify it"*, before it is delivered or used. A qualified person is *"someone with the training or experience to evaluate the output in that field"*, and must be licensed where the law requires it. The reviewer stays responsible.
- **Disclosure:** people who receive the advice or are subject to the decision must be *"clearly told that AI was used to produce it."*
- If local law conflicts with these requirements or adds to them, *"Users should always default to following local laws."*

The AUP prohibits outright some decisions in law enforcement and criminal justice.

### 1.3 Prohibited behaviors relevant to business users (paraphrased from the AUP)
| Category | What's not allowed |
|---|---|
| Impersonation | Impersonating real people or entities, or creating fake personas or accounts, to mislead. Clearly disclosed parody, satire, or fiction is allowed. |
| Privacy | Collecting, soliciting, or accessing private information without permission. This includes non-public contact details, health data, biometric data, and confidential data. Also prohibited: violating privacy laws, for example by disclosing personal data without consent, and combining data from multiple sources into profiles without the people's awareness and agreement. |
| Discrimination | Engaging in or promoting discrimination based on protected attributes. |
| Deception | Creating or spreading deceptive or misleading information about a group, entity, or person, including medical or scientific misinformation. |
| IP | Uses that *"Infringe, misappropriate, or violate the intellectual property rights of a third party."* |
| Surveillance | Targeting or tracking a person without their consent. |
| AI disclosure | Consumer-facing chatbots and agents must *"disclose to users that they are interacting with AI rather than a human"*, at least at the start of each session or in the interface. The disclosure doesn't have to name Claude or Anthropic. |

### 1.4 Appropriate vs needs-a-human vs inappropriate (exam heuristic) [INFERIDO, built from the AUP rules above]
| Fine to do (normal review) | Allowed, but a qualified human decides and AI use is disclosed | Not allowed |
|---|---|---|
| Drafting emails, summarizing internal docs, brainstorming, analyzing **anonymized** data, first drafts of policies | Screening CVs or ranking candidates, credit or insurance recommendations, medical or legal advice to individuals, grading that decides admission or certification | Impersonating a real person or company, a fake review, covert profiling or tracking of individuals, discriminatory filtering, copying protected content to pass it off as your own |

Source for "when not to delegate": the official Cowork course lesson "Best practices for working safely" (in the public HTML of the Skilljar page) lists these:
- *"Regulated workflows that need an audit trail."* The lesson notes that Cowork activity isn't captured in audit logs, the Compliance API, or data exports.
- *"Anything you wouldn't trust a smart, quick colleague to do unsupervised"*, such as sending a legal document to a counterparty or posting a public announcement. In the lesson's words: *"Claude can prepare; you ship."*
- *"Highly sensitive personal data outside the boundary your IT team has explicitly approved."*

---

## 2. Apply data sensitivity, privacy, and regulatory considerations

### 2.1 Classify the data before uploading [INFERIDO: this is a standard industry classification scheme, not an Anthropic document]
| Class | Examples | Default action |
|---|---|---|
| Public | Published website copy, press releases | OK on any approved tool |
| Internal | Internal processes, non-sensitive meeting notes | OK on the **org-approved** plan |
| Confidential | Strategy, unreleased financials, contracts, source code, client data under NDA | Only on the approved commercial workspace, and only as much as the task needs |
| Regulated / highly sensitive | **PII** (names plus account numbers, IDs), **PHI** (health data), payment and financial account data, **credentials, passwords, or API keys**, biometric data | Remove, anonymize, or aggregate first. Use the raw data only if policy explicitly allows it **and** the plan is covered for it (for example HIPAA-enabled Enterprise for PHI). Never paste credentials. |

### 2.2 Decision rule for sensitive data (this matches the official sample item)
**The situation:** you want to analyze a file that contains regulated personal data, and your policy restricts that data.

**Correct path:** remove or anonymize the identifiers (names, account numbers, emails, IDs) **before** uploading, then run the analysis on the cleaned data. This is data minimization: send only what the task needs. Often aggregated or masked data, or a sample, is enough.

**Wrong answers to recognize:**
- *"Upload it and tell Claude not to retain/remember it."* A prompt instruction doesn't change how data is processed or retained. Retention is set by plan and settings, not by what you write in the chat. [INFERIDO from the retention articles in 2.3]
- *"Skip the analysis."* This is over-cautious. Governance aims to make safe use possible, not to stop the work.
- *"Use a personal/free account instead."* This moves the data to a non-approved, consumer account and makes the problem worse.
- *"Incognito chat makes it OK."* Incognito keeps the chat out of history, memory, and training, but **it is still retained for safety purposes**, and on Team or Enterprise it appears in Owner data exports (see 2.4).

### 2.3 Consumer vs commercial accounts (volatile: re-check)
Sources:
- https://privacy.claude.com/en/articles/10023580-is-my-data-used-for-model-training
- https://privacy.claude.com/en/articles/7996868
- https://privacy.claude.com/en/articles/10023548-how-long-do-you-store-my-data

| | **Consumer**: Free, Pro, Max | **Commercial**: Claude for Work (Team, Enterprise), API, Gov |
|---|---|---|
| Terms | Consumer Terms | Commercial Terms |
| Used for model training? | Only if the user **allows it** through the Model Improvement privacy setting, which they can change at any time. Also used if a chat is flagged for safety review, or if the user opts in another way (for example, Trusted Tester) | *"By default, we will not use your inputs or outputs from our commercial products"* for training. Exceptions are feedback submissions and an explicit opt-in. |
| Retention | Training on: up to **5 years**, de-identified, for new or resumed chats. Training off: up to **30 days** in back-end storage. Deleted chats leave history immediately and back-end storage **within 30 days**. Safety-flagged chats: inputs and outputs up to **2 years**, classification scores up to **7 years**. Feedback (thumbs up/down): **5 years**. | Separate commercial terms. Enterprise admins can set **custom retention** (see 2.5). |
| Who controls settings | The individual user | **Owners and admins** of the organization |

- Feedback is an exception on commercial plans too. Thumbs up/down stores the **whole conversation** for up to 5 years and may be used for training. Team and Enterprise Owners can turn off member feedback with the **"Rate chats"** setting (Organization settings > Data and Privacy).
- Raw content from connectors (Google Drive, MCP) is not part of training data, but content *"directly copied into your conversation"* can be. (Consumer training article.)
- **Exam point:** for company data, use the **organization's approved commercial workspace**, not a personal consumer account. [INFERIDO: this follows from the training and retention differences and from the AUP; no single official sentence states it]

### 2.4 Incognito chats
Source: https://support.claude.com/en/articles/12260368-use-incognito-chats
- Available on all plans. They are kept out of chat history and out of memory, and they are **not used for training**, *"even if you have enabled Model Improvement"*.
- They **are still retained** under the existing retention policy (the article mentions 30 days for safety, and longer if flagged).
- **On Team and Enterprise, incognito chats still appear in organizational data exports** available to Owners.
- They are not available inside Projects. An incognito chat can't be converted into a normal chat, and once closed it can't be reopened.
- **Takeaway:** incognito controls privacy toward your own history, memory, and training. It is **not** a way around company policy or a substitute for anonymization.

### 2.5 Enterprise data controls (conceptual)
Sources:
- https://support.claude.com/en/articles/10440198-custom-data-retention-controls-for-enterprise-plans
- https://support.claude.com/en/articles/13296973-hipaa-ready-enterprise-plans
- **Custom data retention (Enterprise only):** set by the Primary Owner or Owners. The minimum is **30 days**. Without a setting, data is kept indefinitely. When a period is shortened, data outside the new period is **deleted immediately and can't be recovered**. Retention changes are logged in **audit logs**. Some features are excluded (the article names Claude Design, Claude Tag, Managed Agents, and features built on Claude Code on the web).
- **HIPAA / PHI:** only **Enterprise** plans can enable HIPAA. Team and individual plans can't. Only the **Primary Owner** can accept the BAA (Business Associate Agreement), under Organization settings > Data and privacy. It is *"a one-way decision"*. Enabling HIPAA doesn't cover every feature: some are covered, some are available but not covered, and some are disabled. The guidance is *"Don't use PHI with a product that isn't covered."*

### 2.6 Regulatory awareness (conceptual) [INFERIDO: general knowledge; the AUP only says to follow applicable and local laws]
| Regulation | What triggers it | What a business user should do |
|---|---|---|
| GDPR / data-protection laws (EU and others) | Personal data about identifiable people | Minimize, anonymize or pseudonymize, use approved processors only, and use data only for its stated purpose |
| HIPAA (US) | PHI handled by covered entities and business associates | Only on a BAA-covered, HIPAA-enabled setup and covered features. Otherwise de-identify. |
| Financial / payment rules (e.g. PCI, banking secrecy) | Card and account numbers, customer financial records | Mask or remove account identifiers |
| Employment / anti-discrimination law, and AI-specific laws (e.g. EU AI Act) | Decisions about hiring, credit, and access to services | A qualified human decides, AI use is disclosed, and the result is checked for bias (matches the AUP's high-risk requirements) |

---

## 3. Follow organizational AI policies and governance standards

### 3.1 The user's checklist [INFERIDO: synthesis; individual items are tied to sources where possible]
1. **Use the approved tool, plan, and workspace.** No "shadow AI", meaning a personal account, an unapproved app, or a personal API key used for work data. The reason is that consumer and commercial accounts differ in training, retention, and admin visibility (2.3).
2. **Know what your org has configured:** retention period, whether feedback is allowed, which connectors and skills are enabled, and whether HIPAA is enabled. Owners and admins control these, not you (2.3, 2.5).
3. **Install or enable only trusted Skills and connectors.** Source: https://support.claude.com/en/articles/12512180-use-skills-in-claude. The article advises installing skills **only from trusted sources**. For a skill from a less-trusted source, including one a colleague shared, it advises reviewing its bundled files and any instructions that point Claude to external network sources before enabling it. It names **prompt injection** and **data exfiltration** as the main risks. Enterprise orgs can turn on skill and plugin **scanning**, which can warn about or block malicious skills. This is the course's "Skill with too much access" scenario.
4. **Least access for agentic tools.** Source: the Cowork lesson "Best practices for working safely". Point Claude at *"a dedicated working folder, not a catch-all"*. *"Back up anything irreplaceable"*. *"Test new workflows on copies first"*. Stay in "Ask before acting" for anything that sends, posts, or shares, and read confirmation prompts. Stop the task if scope creeps: *"'Something feels off' is a real signal."*
5. **Document and disclose AI use** where policy or the context requires it (see 4.1, Transparency Diligence).
6. **When policy is unclear, ask before acting.** Ask the data or policy owner, your manager, IT, security, privacy, legal, or the Claude admin. In the meantime, use the conservative path: anonymize, or use non-sensitive test data. Don't decide alone, and don't use the gap as permission. [INFERIDO]
7. **Report incidents.** If you uploaded something you shouldn't have, tell your admin or security team promptly. The admin has the retention, deletion, and export controls. [INFERIDO]

### 3.2 Who does what [INFERIDO from the admin articles]
| Role | Responsibility |
|---|---|
| End user | Classifies the data, follows the policy, minimizes the data, reviews output, discloses AI use, escalates |
| Owners and admins (Primary Owner) | Plan choice, retention, feedback ("Rate chats"), HIPAA/BAA, connectors and skills, scanning, exports and audit logs |
| Legal, privacy, compliance | Interpret regulation and set the policy |

---

## 4. Understand the ethical implications of AI usage

### 4.1 AI Fluency: Diligence, one of the 4Ds (Delegation, Description, Discernment, Diligence)
Source: official AI Fluency course summaries embedded in the public Skilljar HTML. Course: "AI Fluency: Framework & Foundations", https://academy.claude.com/
- *"Diligence = responsible AI use throughout collaboration"*. It has three aspects:
  - **Creation Diligence:** *"thoughtful AI system selection considering privacy, security, appropriateness"*. In practice this means the right tool and the right data.
  - **Transparency Diligence:** *"honest disclosure of AI assistance"*
  - **Deployment Diligence:** *"taking ownership and responsibility for AI-assisted outputs"*. You remain accountable for what you ship.
- **Human in the loop:** the *"Human maintains decision-making control in all AI interactions. You decide what to ask, evaluate AI outputs for accuracy/sense, determine if output is usable."*
- The AI Fluency "personal AI collaboration policy" covers usage boundaries and "red lines", **transparency standards** (when to disclose and how to document AI contributions), skill maintenance (*"Warning signs of over-reliance (and under-utilization)"*), and ethical guidelines (accuracy and fact-checking, respect for others' work, privacy).

### 4.2 Ethical themes to recognize [INFERIDO: grouping and examples are mine; the principles come from the AUP and AI Fluency]
| Theme | What it means in practice |
|---|---|
| **Bias and fairness** | Outputs can reflect bias. Check decisions about people for disparate impact, and never filter on protected attributes. The AUP prohibits discrimination. |
| **Transparency** | Disclose AI involvement to the people affected, especially in high-risk decisions (required by the AUP) and in customer-facing chat (also required). |
| **Accountability** | "AI said so" is never a justification. A named human owns the output (Deployment Diligence). |
| **Over-reliance** | Verify facts, citations, and numbers. Keep your own skills sharp. Don't let Claude make the final call in high-stakes matters. |
| **Privacy and consent** | Use people's data only for the purpose it was collected for, and only as much as needed. Don't profile people covertly. |
| **IP and honesty** | Don't present protected third-party content as your own. Don't create fake reviews or impersonate anyone. |

---

## 5. Quick decision rules (summary)
1. **Sensitive data:** first classify it, then **minimize or anonymize** it, then use it on the **approved workspace** only.
2. **Decision about a person** (hiring, credit, medical, legal, insurance, housing, education): Claude may assist, but a **qualified human decides** and AI use is **disclosed**.
3. **PHI:** only on HIPAA-enabled Enterprise, and only with covered features. Otherwise de-identify it.
4. **Policy unclear:** **ask the owner or escalate**, and meanwhile take the conservative path. [INFERIDO]
5. **Third-party Skill or connector:** trusted source and reviewed first, enabled by the org.
6. **Agentic actions** (send, post, delete): run on a dedicated folder or copies, keep "ask before acting" on, and **Claude prepares, you ship**.
7. **Prompt instructions are not controls.** "Don't remember this" changes nothing. Real controls are the plan, the settings, and what data you upload. [INFERIDO]

## 6. Common mistakes
- Uploading raw customer PII or PHI because "Claude is secure". Security of the vendor doesn't replace **your org's policy** or data minimization.
- Thinking incognito or a "please don't retain" instruction makes restricted data OK.
- Using a personal Free or Pro account for company work (shadow AI).
- Thinking consumer and commercial plans have the same training and retention rules. They don't.
- Thinking HIPAA is "on" for every plan or every feature. It is Enterprise only, opt-in by the Primary Owner, and limited to covered features.
- Letting Claude rank candidates or approve loans with no qualified human review and no disclosure.
- Over-correcting by refusing all useful work. The goal is safe use, not no use.
- Installing a colleague's Skill without reviewing it, or giving an agent access to the whole Documents folder.
- Not disclosing AI-generated content where policy or context requires it, or blaming "the AI" for an error.

---

## 7. Self-check quiz

1. **A PM wants Claude to analyze a spreadsheet with customer names and account numbers. Policy restricts regulated personal data. What should they do?**
   A: Remove or anonymize the identifiers before uploading, then analyze. Don't upload it and tell Claude not to retain it, and don't skip the analysis.

2. **An HR lead wants Claude to score 200 CVs and auto-reject the bottom half. What does the Usage Policy require?**
   A: Employment is a high-risk area. A qualified person must meaningfully review the recommendation with the authority to change it, and candidates must be told that AI was used. Also check for bias and avoid protected attributes.

3. **By default, are Team or Enterprise conversations used to train Anthropic's models?**
   A: No. Commercial inputs and outputs aren't used for training by default. The exceptions are feedback submissions (thumbs up/down) and an explicit opt-in. Owners can disable member feedback with "Rate chats".

4. **A user on a Pro plan turns on incognito and pastes confidential client data. Is that compliant?**
   A: Not automatically. Incognito chats are excluded from history, memory, and training, but they're still retained for safety. A personal consumer account may not be an approved tool for client data in the first place. Follow policy and anonymize.

5. **A clinic team on a Team plan wants to summarize patient notes with Claude. What's the issue?**
   A: Team plans can't enable HIPAA. Only Enterprise can, after the Primary Owner accepts the BAA, and even then only covered features may be used with PHI. On Team, the notes must be de-identified, or the team shouldn't do it.

6. **A colleague shares a Skill from an unknown GitHub repo that "auto-emails reports". What should you do first?**
   A: Treat it like installing software. Use skills only from trusted sources, review the skill's files and any instructions to external sources before enabling it, and follow the org's process (admin approval or scanning). The main risks are prompt injection and data exfiltration.

7. **You're unsure whether your company policy allows uploading vendor contracts to Claude. What's the best action?**
   A: Ask the policy or data owner (legal, IT, or the Claude admin) before uploading. In the meantime, use a redacted or minimal version, or wait. Don't assume it's allowed, and don't move the work to a personal account. [INFERIDO]

8. **Which AI Fluency competency covers disclosing AI assistance and owning the final output?**
   A: Diligence, specifically Transparency Diligence (honest disclosure) and Deployment Diligence (taking ownership and responsibility for AI-assisted outputs). Creation Diligence covers choosing the right system with privacy and security in mind.

---

## Sources (all accessed 2026-11-09)
- Course page (public listing only): https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations/governance-risk-responsible-use
- Path page: https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations
- Anthropic Usage Policy: https://www.anthropic.com/legal/aup
- Consumer model training: https://privacy.claude.com/en/articles/10023580-is-my-data-used-for-model-training
- Commercial products and training: https://privacy.claude.com/en/articles/7996868
- Consumer retention: https://privacy.claude.com/en/articles/10023548-how-long-do-you-store-my-data
- Incognito chats: https://support.claude.com/en/articles/12260368-use-incognito-chats
- Enterprise custom retention: https://support.claude.com/en/articles/10440198-custom-data-retention-controls-for-enterprise-plans
- HIPAA-ready Enterprise: https://support.claude.com/en/articles/13296973-hipaa-ready-enterprise-plans
- Use skills in Claude: https://support.claude.com/en/articles/12512180-use-skills-in-claude
- AI Fluency (Diligence) and Cowork "Best practices for working safely": official lesson summaries embedded in the public HTML of the Skilljar course page above. Course: https://academy.claude.com/
- Exam domain list: `../Guia.md` (summary of the official exam guide)
