> **Origen de estas notas**
> - **Página del curso consultada:** sí, solo la página de presentación. *"Introduction to Claude Cowork"* (Course 6 of 8 del path Claude Associate) en https://anthropic-partners.skilljar.com/path/claude-associate/introduction-to-claude-cowork y su versión pública en https://anthropic.skilljar.com/introduction-to-claude-cowork. Ahí se ven la descripción, los objetivos y el **temario completo (20 lecciones en 5 módulos)**.
> - **Contenido de las lecciones:** **protegido por login** (registro gratuito en Skilljar). No se pudo leer el texto de las lecciones.
> - **Reconstruido** a partir de fuentes oficiales públicas: Claude Help Center (support.claude.com, colección "Claude Cowork": *Get started*, *Use Claude Cowork safely*, *web/desktop/mobile*, *Team & Enterprise*, *Projects*, *Cowork and chat are one Claude*, *What are skills?*, *Use plugins in Claude*), Anthropic Academy (tutorial *Customize Claude Cowork*), y páginas de producto de claude.com (Cowork, Claude in Chrome, Claude for Microsoft 365, artículo "Cowork and chat are now one Claude", guía de producto de Cowork).
> - Los títulos de sección siguen el temario real del curso. El contenido de cada sección viene de las fuentes citadas debajo de ella, no de la lección en sí.
> - **Fecha de la investigación:** 2026-11-09.
> - ⚠️ **Datos volátiles:** Cowork cambia muy deprisa. En sep–oct 2026 se fusionó con el chat ("Claude Cowork is now just Claude"), las tareas pasaron a ejecutarse en la nube y la disponibilidad por plan y plataforma sigue en despliegue. Las fechas, los planes, los precios, los modos de permisos por defecto y lo que es "beta" o "desktop-only" **deben comprobarse** antes del examen.
> - Lo que no está escrito literalmente en una fuente oficial se marca como **[INFERIDO]**.

# Introduction to Claude Cowork

**Course description (quote):** "Learn to work alongside Claude on your real files and projects." The course covers "the Cowork task loop, plugins and skills, file and research workflows, and how to steer multi-step work responsibly."

**What you'll do (course page):**
- Run a first end-to-end task.
- Give Claude standing context using projects, skills, and plugins.
- Use Claude in Chrome, Word, Excel, PowerPoint, and Outlook.
- Build habits that keep multi-step work safe to share with your team.

**Note on the course page:** "Claude Cowork is now just Claude", rolling out to Pro and Max first, "with more plans to follow."

**Course outline:**
1. **Meet Claude Cowork:** What is Claude Cowork · Setting up Claude Cowork · What Claude Cowork can do for you · Hand Claude Cowork your first task · Make Claude Cowork yours
2. **Get better results faster:** Standing context (global instructions and projects) · Skills (teach Claude Cowork your way) · Plugins (encode your team's expertise)
3. **Use Claude wherever you work:** Claude in Chrome · Claude for Microsoft 365
4. **Sharing and safety in Claude Cowork:** Best practices for working safely · Validating skills for plugins · Share what you build with your team
5. **Wrap up and next steps:** Check your understanding · Quiz

Sources: https://anthropic.skilljar.com/introduction-to-claude-cowork · https://anthropic-partners.skilljar.com/path/claude-associate/introduction-to-claude-cowork

---

## Module 1: Meet Claude Cowork

### What is Claude Cowork

- The Help Center says Cowork "brings the agentic architecture of Claude Code to knowledge work", with no terminal required.
- **Key difference from chat:** Claude "can take on multi-step tasks and carry them out" instead of answering one prompt at a time. **You describe an outcome and come back to finished work.**
- Product guide: "a version of Claude that reads and writes files on your computer, uses your connected work apps, and runs multi-step tasks on your behalf." It is "built for the work, not just the answer."
- Task loop: "Claude plans the steps, executes them, and delivers something tangible across your files and tools."
- The product page describes it as Anthropic's agent for **"non-coding knowledge work."**

**Cowork vs other Claude surfaces**

| | Chat | Projects | Cowork | Claude Code |
|---|---|---|---|---|
| Purpose | Answers questions and has conversations | Workspace with standing knowledge and instructions | Does multi-step knowledge work end to end on your files and apps | Agentic **software engineering** (GitHub/IDE integrations) |
| Interaction | One prompt, one response | Chats inside a project share its context | Describe the outcome; Claude plans, executes, and delivers | Same agentic approach, aimed at code |
| Typical output | Text answer | Answers grounded in project files | Finished files: reports, spreadsheets, decks, research | Code changes |

- Product page: "Chat answers questions. When a task needs file access, Claude brings in Cowork's capabilities so it can do the work instead of describing it."
- **Merge (announced 2026-09-16):** "Claude Cowork and chat are merging into one Claude." You no longer choose a mode first. Claude decides which tool a task needs, so quick questions and multi-step work happen in one conversation. Until the new experience reaches your account, the message box shows separate **Chat** and **Cowork** options. Once you have the new experience, you can't switch back.
- **Projects in Cowork** group related tasks into workspaces "with their own files, context, instructions, and memory." They are "only available in Cowork, not in Claude Code."

Sources: https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork · https://claude.com/resources/guides/claude-cowork-product-guide/what-is-claude-cowork · https://claude.com/product/cowork · https://claude.com/resources/articles/cowork-is-now-claude · https://support.claude.com/en/articles/16761823-claude-cowork-and-chat-are-one-claude

### Setting up Claude Cowork (availability: volatile)

- **Paid plans only.** Cowork is not on the Free plan. The Help Center lists Pro, Max, Ultra, Team, and Enterprise.
- **Surfaces:** "desktop, web, mobile, and in the Claude in Chrome side panel." The desktop app runs on macOS, Windows, and Linux (Linux in beta).
- **Team:** web and mobile are in beta. **Enterprise:** available only when an owner enables it, and cloud sessions are off by default.
- **Where the work runs:** in an **isolated environment on Anthropic's servers** (cloud). Sessions save to your account. "Work continues in the background. Close your laptop and Claude keeps going." Since 2026-10-06, new Cowork tasks on Pro, Max, and Ultra run in the cloud, and the "Only on your computer" option was removed.
- **Desktop-only capabilities:** local files and folders, local connectors, the built-in browser, and computer use need the **Claude Desktop app open**. "Claude reaches only the folders you've connected, through the desktop app, and only while it's open."
- **Usage:** multi-step tasks use more usage than quick questions. The product page says "Claude Cowork consumes limits faster than Chat." Tips from the Help Center: group related work, start new conversations for unrelated work, and check Settings > Usage.

Sources: https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork · https://support.claude.com/en/articles/15520349-use-claude-cowork-on-web-desktop-and-mobile · https://support.claude.com/en/articles/13455879-use-claude-cowork-on-team-and-enterprise-plans · https://claude.com/product/cowork

### What Claude Cowork can do for you

Use cases from the official product page:
- **Scheduled reports**, such as a weekly marketing readout built from analytics and Drive data.
- **Spreadsheet reconciliation**, flagging variances across regional exports and budget files.
- **First-pass contract review** against your playbook, with clause-level citations.
- **Analysis of sales call notes** to find blocked deals and recurring objections.
- Research, document and deck creation, and multi-step tasks in general.

The product guide adds recurring work ("weekly updates, meeting prep, catch-ups, triage") and traceable results ("citations back to the real files and messages").

Other capabilities:
- **Supported files:** documents, PDFs, spreadsheets, presentations, images, data formats, notebooks, and most code files.
- **Scheduled tasks:** these run in the cloud, so they don't need your computer awake.
- **Computer use:** in beta or research preview. Claude "only uses your screen as a last resort" and asks permission before accessing each application.
- **Assign from your phone:** start a task on mobile, and Claude keeps working in the cloud.
- **Live artifacts** can be shared, but sessions themselves can't.

Sources: https://claude.com/product/cowork · https://claude.com/resources/guides/claude-cowork-product-guide/what-is-claude-cowork · https://support.claude.com/en/articles/15520349-use-claude-cowork-on-web-desktop-and-mobile

### Hand Claude Cowork your first task

Steps from the Help Center:
1. Open Claude on the web, desktop, or mobile.
2. Select **"Cowork"** in the message box. In the merged experience, just describe the task.
3. **Describe the task**: the outcome you want.
4. **Review Claude's approach, then let it run.**

Behind the scenes, Claude plans the work, breaks it into subtasks, runs code and shell commands in the isolated environment, may run parallel workstreams, and delivers outputs to your session.

- Keep the desktop app open if the task needs local files, your browser, or your computer. Cloud-only work continues when the app is closed.
- The product page says that with permissions on, "Claude shows its plan and waits for approval before significant actions." You can redirect or stop it at any time.
- **[INFERIDO]** A good first task is low-risk and outcome-focused, with a clear deliverable, run in a dedicated working folder. This combines the Help Center steps with its safety advice.

Sources: https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork · https://claude.com/product/cowork

### Make Claude Cowork yours (connectors, files)

- **Connectors** "plug Claude into the systems where your work already is", such as Slack, Jira, or Microsoft 365. They let Claude read data and also act on it, for example updating a ticket or posting to a channel. Enable them from the **"+" menu** or the **Customize > Connectors** page. Enterprise admins control which connectors are available and whether they have read-only or write access.
- **Local folders:** on desktop, Claude reads and writes files without manual uploads, but "Claude can only read and write files in folders you've connected." **Folder instructions** add project-specific context when you select a local folder.

Sources: https://academy.claude.com/tutorials/customize-claude-cowork · https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork

---

## Module 2: Get better results faster

The Academy tutorial frames customization as three levels:

| Level | Feature | What it is (quotes) | Where to set it |
|---|---|---|---|
| 1. Context and tools | **Connectors** | Access to tools and data | Customize panel or chat bar |
| 1. Context and tools | **Global instructions** | "Global instructions apply to every task you run." | Settings |
| 1. Context and tools | **Project instructions** | "apply only inside that Project, on top of your global ones" | Project's right panel, under Instructions |
| 1. Context and tools | Organization instructions | Enterprise admins set org-wide guidance | Admin settings |
| 2. Capture your process | **Skills** | "instruction files for Claude to complete specific tasks in a repeatable way" | Created in a session, or by asking Claude |
| 3. Bundle and share | **Plugins** | "bundle skills and connectors so teammates have what they need to get started" | Customize > Plugins (Discover) |

**Rule of thumb (quote):** "General rules go in Instructions; a repeatable process goes in a Skill."

Source: https://academy.claude.com/tutorials/customize-claude-cowork

### Standing context: global instructions and projects

- Instructions are "standing rules you write for how Claude should work", covering tone, formatting, and sources.
- **Projects** group related tasks into "persistent workspaces with their own files, links, instructions, and memory." Each project can have its own instructions, scheduled tasks, context (local folders, linked chat projects, URLs), and memory.
- **Project memory doesn't cross projects:** "What Claude learns in one project doesn't carry over to other projects."
- Projects created in Cowork save to your Claude account. Sharing (Can view or Can edit) is available on Team and Enterprise.

Sources: https://academy.claude.com/tutorials/customize-claude-cowork · https://support.claude.com/en/articles/14116274-organize-your-tasks-with-projects-in-claude-cowork

### Skills: teach Claude Cowork your way

- Skills are "folders of instructions, scripts, and resources that Claude loads dynamically" for specialized tasks.
- They load by **progressive disclosure**: Claude reviews the available skills and loads only the relevant ones, which helps "prevent context window overload."
- **Skills vs Projects:** Projects hold "static background knowledge that's always loaded." Skills activate only when needed and work across Claude.
- **Skills vs custom instructions:** instructions "apply broadly to all your conversations." Skills are narrow and task-specific.
- **Skills vs connectors (MCP):** connectors give access to external data and services. Skills give the procedural know-how for using them. The two work together.
- **Invoke a skill** by typing `/skill-name` or by describing the task in plain language.
- **Create a skill** by finishing a workflow and asking Claude: "Package what we just did into a skill."
- **When to create one:** after you've run the same task a few times.
- Skills require code execution to be enabled.

Sources: https://support.claude.com/en/articles/12512176-what-are-skills · https://academy.claude.com/tutorials/customize-claude-cowork

### Plugins: encode your team's expertise

- "Plugins customize how Claude works for your role, team, and company."
- "Each plugin bundles skills, connectors, and sub-agents into a single package." Some plugins also include hooks and local MCP servers.
- Anthropic publishes role-based examples, such as Sales, Product, Legal, Operations, Finance, and Brand voice.
- **Install:** Customize > Plugins > Discover > Add. You can also upload your own plugin file.
- **Customize:** open an installed plugin and click "Customize." This starts a Cowork task that helps you adjust its skills and connectors.
- **Where plugins work:** skills and commands work in chat and Cowork. "Hooks and sub-agents run in Cowork and Claude Code, not in chat." Plugins also sync to Claude Code.
- **Plans:** all paid plans.

Sources: https://support.claude.com/en/articles/13837440-use-plugins-in-claude · https://claude.com/product/cowork

---

## Module 3: Use Claude wherever you work

### Claude in Chrome

- "Claude in Chrome is a browser extension that lets Claude work on the web pages you have open." It "reads the page you're signed in to, then clicks, types, and fills forms."
- Example uses: pulling metrics from dashboards, organizing Google Drive files, and logging sales calls to a CRM, with you approving changes before they take effect.
- **Cowork also has its own built-in browser**, "Separate from your own browser, logins, and tabs." It needs no installation.
- **Safety:**
  - Claude waits for you on "Purchases, financial actions, and anything you can't undo."
  - The product page advises: "Avoid banking, health records, and anything involving credentials."
  - "Pages can hide instructions meant to redirect Claude." Protections "aren't foolproof."
  - Team and Enterprise admins can set site allowlists and blocklists.
- Available on all paid plans.

Sources: https://claude.com/claude-in-chrome · https://claude.com/product/cowork

### Claude for Microsoft 365

Claude for Microsoft 365 is a set of add-ins: "Claude works inside Excel, PowerPoint, Word, and Outlook."

| App | What Claude does |
|---|---|
| Excel | Answers questions about cells, updates assumptions while keeping formulas intact, builds models |
| PowerPoint | Builds slides in your template, edits selected content, generates native charts and diagrams |
| Word | Makes edits as **tracked changes**, replies to comment threads, applies company styles |
| Outlook (beta) | Triages your inbox, drafts replies for you to review, finds meeting times |

- Context carries across the apps, and skills and connectors work in all of them.
- "Nothing goes out or gets saved until you say so." Outlook drafts and invites "wait for you to click send."
- Excel, PowerPoint, and Word are generally available on all paid plans. Outlook is in beta.
- **Safety note:** with the Excel and PowerPoint add-ins, data can move between apps without you directing it. **Avoid using sensitive data in the Office add-ins while Cowork is active.**

Sources: https://claude.com/claude-for-microsoft-365 · https://support.claude.com/en/articles/13364135-use-claude-cowork-safely

---

## Module 4: Sharing and safety in Claude Cowork

### Best practices for working safely

**Permission modes** (changed from the mode selector):

| Mode | Behavior | When to use |
|---|---|---|
| **Manual / Manually approve** | Claude asks before actions; you choose Allow or Deny | Sensitive files, accounts, or sites; first-time tools or sites; hard-to-undo actions |
| **Auto / Automatically approve** | Claude screens each action for safety and blocks unsafe ones, then looks for a safer route or asks you | Routine, trusted work |
| **Skip all approvals** | Nothing is checked; the Help Center calls it the riskiest option | "Only use this when you completely trust every action, connector, file, app, etc. involved in the task." |

- **In every mode, Claude asks before permanently deleting files.**
- **Defaults (volatile):** Auto on Pro, Max, Ultra, and Team; Manual on Enterprise. Team and Enterprise owners can hide Auto or change the starting mode.

**Main risks:**
- **Prompt injection:** malicious instructions are hidden in content Claude reads, such as an email that says "transfer $1000." An attack needs both untrusted content and the ability to act.
- **Write tools** (deleting files, running commands, clicking the screen) "inherently carry more risk."
- **Computer use** acts directly on your screen without the permission checks that gate other tools.
- **Browsers** (the built-in browser and Claude in Chrome) can see logged-in pages, so keep sensitive information out of them.
- **Connectors, MCPs, and plugins** each add a way for attacks to reach Claude. Local MCP servers run with your computer's permissions.

**Recommended practices:**
- Limit file access: use a **dedicated working folder** and keep backups.
- Allow internet access only to sites you trust, and be deliberate about which tabs are open.
- **Monitor** for unexpected files, websites, or scope creep. **Stop the task** if something seems wrong.
- **Scheduled tasks:** start with simple, low-risk work, review each run's output, and pause or delete tasks you no longer use.
- **Don't** grant access to sensitive local files (financial documents, credentials). **Don't** use Cowork for banking or healthcare portals. **Don't** schedule tasks that take hard-to-reverse actions, such as sending messages or making purchases.
- Report suspicious behavior through in-app feedback.

**Human oversight:** you remain responsible for everything Claude does on your behalf, including messages sent, purchases, data changes, and scheduled-task actions. Stay close to tasks with real-world consequences.

**Limits of the safeguards:**
- They reduce risk but don't eliminate it; the risk of an attack is "still non-zero."
- Isolation protects your computer from the code Claude runs, but it doesn't limit what Claude can read or do through the access you've granted.
- Network egress settings don't apply to web fetch, web search, MCPs, or Claude in Chrome.

**Data:**
- Sessions run in isolated, temporary cloud environments that can't reach your home or company network.
- Local files a session opens are processed on Anthropic's servers.
- Deleted tasks are removed from backend storage within 30 days.

Sources: https://support.claude.com/en/articles/13364135-use-claude-cowork-safely · https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork · https://support.claude.com/en/articles/16761823-claude-cowork-and-chat-are-one-claude

### Validating skills for plugins

The lesson content is gated. These points come from official help articles:
- "Only install plugins from sources you trust."
- "Plugins may include local MCP servers that run on your computer with the same permissions as any other program you run."
- Review a plugin shared with you before turning it on. Plugins "can expand Claude's scope of action significantly."
- On Enterprise, **skill scanning** checks skills and plugins for malicious content at installation. A malicious plugin is blocked, and a possibly risky one shows a caution banner.
- Enterprise admins may restrict which plugins can be installed or disable local MCP servers.
- **[INFERIDO]** Before packaging a skill into a team plugin, test it on real tasks, check its outputs, and review what files, connectors, and actions it uses. This follows the Academy advice to write a skill only after running a task a few times, plus the trust guidance above. The lesson's exact checklist is not public.

Sources: https://support.claude.com/en/articles/13837440-use-plugins-in-claude · https://support.claude.com/en/articles/13364135-use-claude-cowork-safely · https://support.claude.com/en/articles/12512176-what-are-skills

### Share what you build with your team

- Share a skill or plugin "once a teammate asks how to set up their own." Use plugins "to distribute the org's standard set across roles."
- **Team and Enterprise:**
  - Share a plugin or skill with specific people or groups, or publish it to the organization's library. **Shared plugins and skills are view-only.**
  - Owners can create **plugin marketplaces** and set plugins as installed by default, available, required, or hidden.
  - Projects can be shared with Can view or Can edit access.
- **What can't be shared:** Cowork **sessions** can't be shared, but individual artifacts can.
- **Admin controls:**
  - Cowork is on by default for Team and Enterprise, and owners can turn it off.
  - Activity on web, desktop, and mobile is captured in the **Compliance API**.
  - Owners can stream Cowork events (tool calls, approval decisions) to SIEM tools through **OpenTelemetry**, but this "doesn't replace audit logging for compliance purposes."

Sources: https://academy.claude.com/tutorials/customize-claude-cowork · https://support.claude.com/en/articles/13837440-use-plugins-in-claude · https://support.claude.com/en/articles/13455879-use-claude-cowork-on-team-and-enterprise-plans · https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork

---

## Limitations to remember (volatile)

- Not available on the Free plan.
- Local files, the built-in browser, and computer use need the desktop app open, and only folders you've connected are reachable.
- Sessions can't be shared; artifacts can.
- Cowork uses limits faster than chat.
- In the merged experience: incognito chats use the old experience (no file creation or code), you can't branch a conversation from an earlier point, and search doesn't cover older Cowork tasks.
- Prompt injection risk is non-zero even with all the safeguards.

Sources: https://support.claude.com/en/articles/16761823-claude-cowork-and-chat-are-one-claude · https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork

---

## Common mistakes

- Treating Cowork like chat: it is built for **delegating outcomes**, not for one-off Q&A.
- Connecting your whole drive or sensitive folders instead of a **dedicated working folder**.
- Using **Skip all approvals** for tasks that involve untrusted content or hard-to-undo actions.
- Thinking safeguards remove responsibility: **you remain responsible** for what Claude does on your behalf.
- Putting a repeatable process in global instructions. Repeatable processes belong in a **skill**; general rules belong in **instructions**.
- Installing plugins or skills from untrusted sources. Plugins can run local MCP servers with your computer's permissions.
- Scheduling tasks that send messages or make purchases.
- Confusing Cowork with Claude Code. Claude Code is for software engineering; Cowork is for non-coding knowledge work.

---

## Self-check quiz

1. **What is the core difference between Cowork and a regular chat?**
   → Cowork takes on **multi-step tasks and carries them out**. You describe an outcome, Claude plans and executes the steps across your files and tools, and it delivers finished work. Chat answers one prompt at a time.

2. **How does Cowork differ from Claude Code?**
   → Both use the same agentic approach. Claude Code targets software engineering, while Cowork targets non-coding knowledge work such as research, analysis, documents, spreadsheets, and decks, with no terminal needed.

3. **Which permission mode should you use for a task that touches sensitive files or takes hard-to-undo actions?**
   → **Manually approve**: Claude asks before each action. Skip all approvals is the riskiest mode and is only for fully trusted tasks. In every mode, Claude asks before permanently deleting files.

4. **What is prompt injection, and what does it need to succeed?**
   → Malicious instructions hidden in content Claude reads, such as an email or web page. It needs both untrusted content and the ability to take action.

5. **Where should a repeatable multi-step process go: global instructions, project instructions, or a skill?**
   → A **skill**: "General rules go in Instructions; a repeatable process goes in a Skill." Skills load only when relevant, through progressive disclosure.

6. **What does a plugin contain, and what's the key safety rule?**
   → Skills, connectors, and sub-agents (sometimes hooks and local MCP servers) in one package. "Only install plugins from sources you trust." Local MCP servers run with your computer's permissions.

7. **Can Claude reach your local files when you close the desktop app?**
   → No. Cloud tasks keep running, but local files, the built-in browser, and computer use need the desktop app open, and only folders you've connected are reachable.

8. **Who is responsible for actions Claude takes in Cowork, such as sent messages or purchases?**
   → **You are.** Stay close to tasks with real-world consequences, monitor for scope creep, and stop the task if something looks wrong.
