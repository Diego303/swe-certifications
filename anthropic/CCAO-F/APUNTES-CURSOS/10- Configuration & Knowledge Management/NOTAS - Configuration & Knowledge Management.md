# NOTAS – Configuration & Knowledge Management (CCAO-F, Dominio 5 · 12%)

> **Origen:** Se consultó la página del curso (https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations/configuration-knowledge-management) y la del path. Solo es pública la ficha: *Course 5 of 8*, 47 min, descripción y 4 objetivos de aprendizaje. **El contenido de las lecciones está restringido (requiere registro/login en Skilljar) y no se ha podido leer.** Estas notas se han **reconstruido** a partir de fuentes oficiales públicas de Anthropic: centro de ayuda support.claude.com (Projects, compartir proyectos, RAG, subida de archivos, personalización, memoria, chats de incógnito, connectors, Google Workspace, custom connectors/MCP remoto, skills, enterprise search), Claude Academy (Claude 101: *Introduction to projects*, *Working with skills*, *Connecting your tools*, *Getting better results*; caso de uso legal con Projects) y la guía oficial *Reduce hallucinations* de platform.claude.com.
> **Fecha de investigación:** 2026-11-09.
> **Aviso:** los datos volátiles (límites de archivos, número de proyectos en Free, disponibilidad por plan, nombres exactos de menús como *Settings > Your Claude* o *Customize > Connectors*, funciones en beta) cambian a menudo. Compruébalos en la web oficial antes del examen. Lo marcado **[INFERIDO]** es deducción propia, no texto oficial.

---

## 0. Course overview (public course page)

- **Description (public page, paraphrased):** the module covers the setup that happens *before any single conversation*: creating a Project, writing its instructions, adding knowledge sources so Claude starts with the right context; how this setup lets a skill **scale from one person to a team**; and a **maintenance routine** to keep the configuration from going stale.
- Path summary line: "Configure Claude once so every later conversation starts with the right context."
- **Learning objectives (= exam Domain 5):**
  1. Configure Claude Projects with instructions and knowledge sources.
  2. Manage uploaded knowledge and connectors.
  3. Create effective project-level instructions.
  4. Inform, maintain, and update configurations, knowledge sources, and instructions.
- Lesson titles: **not visible** (gated). The headings below follow the four objectives.

Sources: https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations/configuration-knowledge-management · https://anthropic-partners.skilljar.com/path/claude-certified-associate-foundations

---

## 1. Configure Claude Projects with instructions and knowledge sources

### 1.1 What a Project is
- Projects are "self-contained workspaces with their own chat histories and knowledge bases" (help center). Academy adds: each has its own chat history, knowledge base **and instructions**; they fit **ongoing work across many conversations**, not one-off questions.
- Availability: all users, including Free; **Free users can create up to five projects** (volatile).
- **Name and description: Claude cannot see them** – they are for you and your teammates. (So never put guidance in the description.)
- On Team/Enterprise you choose **private or shared** at creation; Enterprise admins may require **project tags**.

### 1.2 The three "containers" of context

| Container | Scope | What goes there | Official wording |
|---|---|---|---|
| **Project knowledge** | Every chat in that project | Stable reference material: brand/style guides, templates, research, meeting notes, requirements, **examples of work to emulate**, specs | "Anything you upload to this space will be used across all of your chats within that project." |
| **Project instructions** | Every chat in that project | How Claude should behave: context, role/perspective, process, tone, requirements | "Project instructions help Claude understand the specific context and requirements for a particular project. These instructions only apply to chats within that project." |
| **Individual chat (upload/paste in the chat)** | That conversation only | One-off material you do not want in the shared knowledge base | Academy: to share content for a single conversation without adding it to the knowledge base, upload it directly in that chat. |

- Key fact (exam favourite): **"Context is not shared across chats within a project unless the information is added into the project knowledge base."** A decision made in chat A is not known in chat B unless you put it in knowledge (or memory picks it up – see §1.5).
- Help center: Claude "performs best when you use project instructions for **general context** around your project, **key guidelines**, and **Claude's role**."

### 1.3 Project vs. regular chat – decision rule (Academy)
- **Use a project** when you repeatedly need the same reference materials, want consistent response requirements, or need teammates working from the same foundation.
- **Use a regular chat** for quick, standalone questions.

### 1.4 Layering of personalization features

| Layer | Scope | Set where (volatile UI) | Use it for |
|---|---|---|---|
| **Instructions for Claude** (account-wide / profile instructions; formerly "profile preferences") | **All** your conversations | Settings > Your Claude > Instructions (older layout: Settings > Account) | Preferred approaches, common terms you use, typical scenarios, general communication preferences |
| **Project instructions** | Only chats in that project | Project page | Project-specific context, workflow guidelines, task requirements, roles/perspectives |
| **Skills** | Load **dynamically, only when relevant**, anywhere in Claude | Skills list (org owners can provision) | Repeatable procedures/how a task is done; help article also lists "customize how Claude formats and delivers its responses" |
| **Memory** | Built from your chats; account memory + per-project memory | Settings > Your Claude > Your memory | Continuity across conversations (see §1.5) |
| **Project knowledge** | Always available in that project | Project page | Reference information |

- Official "Choosing the right feature": "Use profile instructions for account-wide settings that affect all your interactions with Claude." · "Use project instructions when you need specific guidance or context for a particular project" · "Use skills when you want to customize how Claude formats and delivers its responses." · "You can use these features independently or in combination."
- **Projects vs. Skills:** "Projects provide static background knowledge that's always loaded when you start chats within them. Skills provide specialized procedures that activate dynamically when needed and work everywhere across Claude." Academy shorthand: **"projects store knowledge, skills perform tasks."** A skill can draw on knowledge stored in a project (e.g., a "customer call prep" skill using customer profiles in a project).
- **Skills vs. custom instructions:** custom instructions apply to all conversations; skills are task-specific and "only load when relevant." Skills can include scripts; they require **code execution** to be enabled.
- **Skills vs. MCP/connectors:** MCP connects Claude to external services and data; skills supply the procedures for using those tools well.
- **Styles:** the current help article on personalization **does not mention "Styles"**; formatting/delivery customization is attributed to skills. If your Claude.ai UI still shows Styles, treat them as response-formatting/tone presets – verify before the exam. [INFERIDO]
- Precedence between layers is **not documented officially**. Rule of thumb: put the general in the broad layer and the specific in the narrow one, and avoid contradictions between layers. [INFERIDO]

### 1.5 Memory, project-scoped memory and incognito
- Memory is built "as a set of individual topics as you chat"; Claude saves memories on its own, and you can say "remember this", or ask it to change/forget an item.
- **Project memory:** each project has its own memory. In a project Claude uses that project's memory **plus your non-project memory, but not memory from other projects**. To isolate a project completely: turn off **"Use account memory"** on the project page.
- **View/edit:** Settings > Your Claude > Manage next to "Your memory"; read, edit, delete topics. "Fix something in one topic and the change applies to every conversation from then on."
- **Controls:** "Generate memory from chats" toggle; **Pause** (keeps memories but stops using/creating them); **Reset** (deletes all memories incl. project memories – "cannot be undone"); **memory off for a single chat** via the "+" menu *before the first message* (chat stays in history and is searchable).
- **Chat search** (paid plans): searches chats outside projects, or within one project – **not across projects**. Toggle "Search and reference chats".
- **Plans:** Free/Pro/Max/Ultra – memory on by default. **Team/Enterprise – owners decide** (Organization settings > Capabilities); turning it off org-wide **permanently deletes** all memory data; **owners can't view or edit a user's individual memories**.
- **Incognito chats:** not saved to chat history or memory, not used for training, not searched later, cannot be reopened; still **retained 30 days by default** (or per Enterprise retention policy) and included in org data exports / Compliance API. **Not available inside projects** – inside a project, turn off Memory in the "+" menu instead.

Sources: https://support.claude.com/en/articles/9517075-what-are-projects · https://support.claude.com/en/articles/9519177-how-can-i-create-and-manage-projects · https://academy.claude.com/courses/claude-101/introduction-to-projects · https://support.claude.com/en/articles/10185728-understanding-claude-s-personalization-features · https://support.claude.com/en/articles/12512176-what-are-skills · https://academy.claude.com/courses/claude-101/working-with-skills · https://support.claude.com/en/articles/11817273-use-claude-s-chat-search-and-memory-to-build-on-previous-context · https://support.claude.com/en/articles/12260368-use-incognito-chats

---

## 2. Manage uploaded knowledge and connectors

### 2.1 Uploaded knowledge – limits and behaviour (volatile, from help center)

| | Chat uploads | Project knowledge files |
|---|---|---|
| Size | 500MB per file | **30MB per file** |
| Number | Up to 20 files per chat | "Unlimited, but total content must fit within Claude's context window" (RAG extends this on paid plans) |
| Processing | – | "Text extraction only (except for multimodal PDFs)" |

- Supported documents: PDF, DOCX, CSV, TXT, HTML, ODT, RTF, EPUB, JSON, XLSX (XLSX needs code execution and file creation enabled); images JPEG, PNG, GIF, WebP.

### 2.2 Large knowledge bases – RAG
- Paid plans (Pro, Max, Ultra, Team, Enterprise). When project knowledge **approaches the context window limit**, Claude **automatically** switches to RAG; "expand your project's capacity by up to 10x"; **no setup required**; a **visual indicator** shows a RAG-enabled project; can switch back if knowledge drops below the threshold.
- Uses a **"project knowledge search tool"** to retrieve only the most relevant passages instead of loading everything.
- Official tips: upload all relevant files upfront; **clear, descriptive filenames**; group related documents in the same project; **reference specific documents by name** in questions.

### 2.3 Curating knowledge (best practices)
- Academy: "Keep the knowledge base current" – **outdated documents lead to outdated answers**; name files descriptively; keep related files together; mention specific documents in questions.
- Single source of truth / avoid duplicates and conflicting versions: one current version per document, remove superseded ones, put version/date in the filename (e.g., `Pricing-Policy_v3_2026-10.pdf`). [INFERIDO from "keep current" + "descriptive filenames"; not an official rule]
- Start with **one focused use case**, then expand (Academy) – don't build one project for everything.

### 2.4 Connectors – what they are
- "Connectors let Claude access your apps and services, retrieve your data, and take actions within connected services." Claude **inherits the user's permissions** from the connected service.
- Types: **directory connectors** (pre-built), **web connectors** (all users), **desktop extensions** (Claude Desktop, local), **custom connectors (remote MCP)** – Free users limited to **one** custom connector.
- Enable from Customize > Connectors or the "+" menu; **not automatically active in every conversation** – toggle the services you want per conversation.
- Academy: connectors let you ask about the **live source** "instead of pasting in a copy".

### 2.5 Google Workspace connectors (Drive, Gmail, Calendar)
- **Gmail:** search/read emails in natural language, draft messages; sending/replying/forwarding **require approval by default**; **attachments not accessible (metadata only)**.
- **Calendar:** create, update, delete events; find free times.
- **Drive:** search/retrieve files, upload, create folders, save Claude-generated files.
- **Drive in project knowledge:** you can add Drive files to a project's Files section **only in private projects** (not shared projects). Google Docs added to chats/projects "sync directly from Google Drive" (stay current).
- Claude extracts text from Drive files; does not process images embedded in documents.
- Access "mirrors" what you can already see in Workspace. Team/Enterprise: an **Owner or Primary Owner must enable** the connectors at org level first; Workspace admin may need to trust the app.
- Privacy: "We do not train our models on your Gmail, Drive, or Calendar connector data" (consumer accounts opted into training: copied connector content may be used); retrieved data is stored with the chat and deleted with it.

### 2.6 Uploads vs. connectors – decision table

| Question | Upload to knowledge | Connector |
|---|---|---|
| Data freshness | Static snapshot – you must re-upload when it changes | Live source (e.g., synced Google Docs, live MCP calls) |
| Best for | Stable reference docs (guidelines, templates, examples) | Frequently changing data, email, calendar, docs in Drive, internal tools |
| Access control | Anyone with project access sees the file | Permission-aware: each user sees only what they can access in the source (unless a shared credential is used) |
| Actions | Read only | Can also act (draft/send email, create events) – subject to approval settings |
| Maintenance | Owner must replace stale files | Owner maintains connection, permissions, disconnects unused services |

(Columns synthesised from the official articles above. [INFERIDO] for the table framing.)

### 2.7 Custom / remote MCP connectors (business level)
- Add via Customize > Connectors with a name and remote MCP URL; connections come **from Anthropic's cloud**, so the server must be publicly reachable (or allowlist Anthropic IPs).
- Team/Enterprise: only **Owners** (and some Enterprise custom roles) add connectors for the org; each member then connects individually – **unless a shared credential** (e.g., API key) is used, which gives everyone that credential's access.
- **Custom connectors are not verified by Anthropic**; review requested permissions; beware **prompt injection**; tools can modify or delete data.

### 2.8 Least-access & admin controls
- Only connect trusted services; review requested access; **grant only the permissions you need**; **disconnect services you no longer use**; test a new connection with a simple request (Academy).
- Admins can set per tool / category: **Always allow / Needs approval / Blocked**; restrictions can narrow but never exceed what the source system allows.
- "Enabling a connector makes it available to your team, but it doesn't automatically grant anyone access."
- **Enterprise search** ("Ask Your Org" project, Team/Enterprise): preconfigured project, Owner completes setup (needs a Documents and a Chat connector); **system prompt maintained by Anthropic**; permission-aware; "No data from connected services are indexed in our systems" – results come from live MCP calls.

Sources: https://support.claude.com/en/articles/8241126-upload-files-to-claude · https://support.claude.com/en/articles/11473015-retrieval-augmented-generation-rag-for-projects · https://academy.claude.com/courses/claude-101/introduction-to-projects · https://support.claude.com/en/articles/11176164-use-connectors-to-extend-claude-s-capabilities · https://support.claude.com/en/articles/10166901-use-google-workspace-connectors · https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp · https://academy.claude.com/courses/claude-101/connecting-your-tools · https://support.claude.com/en/articles/12489464-use-enterprise-search

---

## 3. Create effective project-level instructions

### 3.1 What to include (Academy, with official examples)
- **Context:** "This project is for creating marketing content for our B2B software product."
- **Process:** "First consider a blog structure that will entice this audience, then write the draft."
- **Tone and style:** "Use a professional but conversational tone. Avoid jargon when possible."
- **Requirements:** "Always include a call-to-action at the end of marketing copy."
- **Automation:** "When I upload a meeting transcript, create a structured summary using this template."
- Also: expertise level, response format, desired outcomes. **"Vague instructions produce inconsistent results."**
- Help center: role or industry perspective, formal tone, etc.

### 3.2 Checklist for a good instruction set
| Element | Example | Source |
|---|---|---|
| Role / perspective | "Answer as our senior HR policy advisor." | help center (role/industry perspective) |
| Audience | "Readers are non-technical store managers." | Academy *Getting better results* (audience) |
| Format | "Bullets with bold headers; max one page." | Academy ("Show, don't just tell") |
| Constraints / length | "Two-paragraph summary." | Academy |
| Which knowledge to use | "Use only the documents in project knowledge; name the file you used." | platform docs: *External knowledge restriction*, *Verify with citations* |
| Missing info | "If the documents don't contain the answer, say so instead of guessing." | platform docs: "Allow Claude to say 'I don't know'" |
| Cite sources | "Quote the passage and cite the document name for each claim." | platform docs: "have it cite quotes and sources for each of its claims" |
| Examples | Put sample outputs in knowledge, reference them in instructions | Academy (examples of work to emulate) |

- Instructions = **how to behave**; knowledge = **what to know**. Don't paste long reference documents into the instructions field; don't put behavioural rules only inside a knowledge file. [INFERIDO]
- Let Claude help draft them: the Academy legal use case gives Claude the playbook/template, has it produce a **standards guide for knowledge** plus **ready-to-paste custom instructions**.

Sources: https://academy.claude.com/courses/claude-101/introduction-to-projects · https://academy.claude.com/courses/claude-101/getting-better-results · https://support.claude.com/en/articles/9517075-what-are-projects · https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations · https://academy.claude.com/use-cases/organize-your-legal-workflows-using-projects

---

## 4. Inform, maintain and update configurations

### 4.1 Official maintenance guidance
- Academy: **review and update knowledge documents periodically**; **revise instructions as your needs change**; star frequently used projects; **archive or delete** projects you no longer need.
- **Test before relying:** run "3-5 already reviewed NDAs through the Project", compare with how your associates handled them, note where Claude "misses nuance or applies the wrong severity level", then refine instructions. "Ten minutes of calibration prevents hundreds of inconsistent reviews."
- **Team propagation:** "update the knowledge base once, and the change propagates to all users" of a shared project. Start from a well-documented process; formalise tribal knowledge first.
- Archiving: moves the project down; sharing, members and knowledge are preserved; archived projects must be unarchived before deletion.

### 4.2 Recommended routine [INFERIDO – operational practice consistent with the above]
1. **Owner:** one named owner (with "Can edit") per shared project.
2. **Cadence:** review knowledge + instructions on a fixed schedule and whenever a source policy/document changes.
3. **Change log:** record date, what changed and why (e.g., a "Changelog" section at the end of the instructions or a small knowledge file).
4. **Regression test:** keep 3-5 sample prompts with known-good answers; re-run them after every change.
5. **Prune:** remove stale/duplicate files; check connectors still needed; check memory topics for outdated facts.
6. **Inform users:** tell project members what changed (instructions apply to every new chat).

### 4.3 Sharing & roles (Team/Enterprise)
- Visibility: **Public** (everyone in the org can view and use) or **Private** (only invited members); switchable from Share.
- **Can view:** see contents, knowledge, instructions and chat – cannot edit. **Can edit:** modify instructions and knowledge, manage members (Enterprise: add tags).
- **"Chats within a project are not shared by default"** – sharing a project does not expose members' chats; individual chats can be shared by link (snapshot).
- Owners can turn off project sharing (Enterprise: per role); public projects then become private. Group sharing = Enterprise, beta.

Sources: https://academy.claude.com/courses/claude-101/introduction-to-projects · https://academy.claude.com/use-cases/organize-your-legal-workflows-using-projects · https://support.claude.com/en/articles/9519177-how-can-i-create-and-manage-projects · https://support.claude.com/en/articles/9519189-manage-project-visibility-and-sharing · https://support.claude.com/en/articles/9517075-what-are-projects

---

## 5. Common mistakes

| Mistake | Fix |
|---|---|
| Expecting chat B to know what was decided in chat A of the same project | Add it to project knowledge (context isn't shared across chats otherwise) |
| Writing guidance in the project **description** | Claude can't see the description – use instructions |
| Vague instructions ("be helpful, be good") | Specific role, audience, format, constraints, process |
| Stale or duplicate files left in knowledge | Periodic review; one current version; descriptive names |
| Uploading a static copy of fast-changing data | Use a connector / synced Google Doc instead |
| Connecting everything "just in case", broad permissions | Least access; enable connectors per chat; disconnect unused |
| Trusting a custom connector blindly | Not verified by Anthropic; check permissions, prompt-injection risk |
| Trying to add Drive files to a **shared** project | Only possible in private projects |
| Using incognito inside a project | Not available; turn Memory off in the "+" menu before first message |
| Changing instructions without testing | Re-run sample prompts / already-reviewed cases |
| Putting a repeatable multi-step procedure only in one project | Consider a skill (works everywhere, loads when relevant) |
| Assuming an admin enabling a connector gives everyone data access | Each user still authenticates; access mirrors their source permissions |

---

## 6. Self-check quiz (8)

1. **A teammate asks why Claude in a new project chat doesn't know the pricing decision made yesterday in another chat of the same project. Why, and fix?**
   → Context isn't shared across chats in a project unless added to project knowledge. Add the decision to knowledge (or a doc in knowledge).
2. **Where do you put "Answer as our compliance analyst, cite the policy file, say 'not in the documents' if unsure": description, instructions or knowledge?**
   → Project instructions. Description is not visible to Claude; knowledge is for reference material.
3. **Your project's documents approach the context window on a Team plan. What happens?**
   → RAG activates automatically (no setup), using a project knowledge search tool; capacity up to ~10x; descriptive filenames and naming the document in questions help retrieval.
4. **Sales figures change daily in a Google Sheet/Doc. Upload a PDF export or use the Drive connector?**
   → Connector (live/synced source); an upload is a static snapshot that goes stale.
5. **You want a client project's memory not to mix with your personal memory. What do you do?**
   → Turn off "Use account memory" on that project's page (projects never use other projects' memory anyway).
6. **On Enterprise, the admin enabled the Gmail connector. Can Claude now read every employee's mailbox for you?**
   → No. Enabling makes it available, it doesn't grant access; each user authenticates and Claude only sees what that user can access. Sending email needs approval by default.
7. **Difference between project knowledge, project instructions and a skill?**
   → Knowledge = what Claude should know (always loaded in that project); instructions = how to behave in that project; skill = a repeatable procedure that loads only when relevant and works everywhere ("projects store knowledge, skills perform tasks").
8. **You revised the instructions of a shared contract-review project. What should you do before announcing it?**
   → Test against 3-5 already-reviewed cases / sample prompts and compare; refine; then inform members (the change propagates to all users). Keep a change log [INFERIDO].
