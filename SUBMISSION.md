# SafeO — Hackathon Submission Descriptions

Track: Track 3 — Unicorn Track
Live demo: https://safeo-shield-1.onrender.com
Repository: https://github.com/CandyButcher27/safeo-shield

---

## SHORT DESCRIPTION
(~150 characters — for submission tagline / card preview)

SafeO is an Arabic-aware, multi-agent cybersecurity engine that blocks malicious ERP inputs in real time — powered by Gemma 3 on AMD via Fireworks AI.

---

## MEDIUM DESCRIPTION
(~400 characters — for submission summary field)

SafeO is a real-time risk decision engine embedded inside enterprise workflows. It scans ERP forms, APIs, and messages, then returns ALLOW, WARN, or BLOCK before any data is saved. A 3-tier ML pipeline escalates to a 5-agent LangGraph investigation graph when needed. The ForensicsAgent runs Google DeepMind's Gemma 3 4B via Fireworks AI on AMD-hosted GPUs. Built-in Arabic and Arabizi normalization catches mixed-script evasion that English-first tools miss entirely.

---

## LONG DESCRIPTION
(for the "Project description" / "About" field on lablab.ai — paste as-is)

---

SafeO is a real-time cybersecurity decision engine that protects enterprise applications at the exact moment malicious input tries to enter — before it is saved, executed, or forwarded.

**The problem:** Every ERP system is full of text fields — invoice memos, CRM notes, vendor onboarding forms, HR messages. Attackers exploit those fields with SQL injection, prompt injection, ERP fraud instructions, and — critically for the MENA region — Arabic and Arabizi obfuscation that English-first tools do not detect. Traditional perimeter defences (WAF, SIEM) are too late: by the time a log is reviewed, the damage is done.

**What SafeO does:** Every scan hits a 3-tier ML pipeline and returns one of three decisions — ALLOW, WARN, or BLOCK — in milliseconds, before data persistence:

- **Tier 1** — deterministic heuristics (SQLi, XSS, prompt injection, ERP fraud, IDN homograph, entropy, n-gram)
- **Tier 2** — DistilBERT / TF-IDF classifier (ROCm-ready, with feedback retraining loop)
- **Tier 3** — optional LLM via Fireworks AI on AMD hardware (Gemma 3 4B, Llama 3.1 70B, DeepSeek-R1)

For WARN and BLOCK decisions, a 5-agent LangGraph-style investigation graph runs in parallel:
1. **MultilingualAgent** — normalises Arabic, Arabizi, and mixed-script input (AraBERT-based)
2. **PolicyAgent** — cites applicable enterprise policy and UAE compliance rules
3. **ForensicsAgent** — maps to MITRE ATT&CK via an attack-pattern knowledge graph; **powered by Gemma 3 4B via Fireworks AI on AMD**
4. **VerifierAgent** — meta-judge that downgrades false positives before action
5. **RemediationAgent** — selects playbook, generates Jira payload, drafts WhatsApp-safe reply

Every agent transition produces a SHA-256 checkpoint hash, forming a tamper-evident audit chain.

**User-facing features:**

🤖 **SafeO Assistant** — role-adaptive security chatbot. Same forensic engine for every user; the UI adapts to their role (non-technical, security analyst, ERP manager, developer). Includes a live side-by-side demo: a homograph phishing URL that ChatGPT calls "looks safe" — SafeO returns BLOCK with the exact Unicode codepoints flagged.

🖼 **Visual Evidence Capture** — Playwright headless screenshots with Pillow-annotated bounding boxes showing exactly where the threat is on the page. GitHub repos are fetched and rendered as dark-theme code images with line-level secret and prompt-injection highlights.

🔧 **Workflow Builder** — drag-and-drop security pipeline editor. Security teams can compose source → detection → decision → output pipelines without code changes, and deploy them per tenant.

📋 **Logs + Jira Escalation** — every scan decision is logged and can be escalated to a Jira ticket in one click, with the full forensic summary pre-filled.

🌍 **Arabic and Arabizi Security Layer** — SafeO's core differentiator. The MultilingualAgent normalises `3tini admin access`, `١=١ UNION SELECT`, and `إسقاط جدول users` before any pattern matching runs, catching the mixed-script evasion techniques that bypass English-first tools.

**AMD infrastructure:** The ForensicsAgent calls Gemma 3 4B via Fireworks AI, which runs its entire GPU fleet on AMD Instinct hardware — making every forensics reasoning step AMD-powered. The codebase is fully ROCm-ready: bf16 LoRA fine-tuning, PyTorch ROCm wheels, and AMD-optimised DistilBERT and AraBERT paths. We applied for AMD AI Developer Cloud credits; approval did not arrive before the submission deadline. The Fireworks (AMD-hosted) path is the active AMD-infrastructure connection in this build. The `amd_setup/` scripts (ROCm install, vLLM startup, GPU check) are implemented and ready to activate once credits are provisioned.

**Self-improving:** A Bayesian threshold engine (SQLite-backed Beta distributions per attack class) learns from analyst feedback and adapts block thresholds within hard safety bounds [0.45, 0.90]. A LoRA fine-tuning controller decides when Tier 2 should be retrained, with a deployment gate that blocks updates if the false-negative rate worsens.

**Market:** MENA enterprise (UAE, Saudi, GCC) — 348M Arabic internet users, under-served by English-first security tools. Target buyers: any company running Odoo, SAP, or Oracle with Arabic-speaking users or cross-border operations exposed to Arabizi and mixed-script payloads.

**Fully operational:** API, React dashboard, 5-agent graph, ERP Odoo module, WebSocket investigation replay, visual evidence capture, workflow builder, and Jira escalation — all deployed and live at https://safeo-shield-1.onrender.com.

---

## GEMMA PRIZE CALLOUT
(If submitting for "Best AMD-Hosted Gemma Project" — $2,000 prize)

SafeO uses **Gemma 3 4B (gemma3-4b-it)** via Fireworks AI on AMD-hosted infrastructure as the reasoning engine inside the ForensicsAgent — the specialist agent that maps attack payloads to MITRE ATT&CK techniques, performs chain-of-thought analysis, and produces structured forensic evidence for the investigation audit chain. Gemma was chosen specifically because it runs on AMD hardware via Fireworks, aligning with the hackathon's AMD-sustainable infrastructure mandate. The ⚡ "Powered by Gemma on AMD" badge is displayed on every page of the SafeO dashboard.

---

## KEY NUMBERS FOR SUBMISSION FORM

- Agents: 5
- ML tiers: 3
- Attack-pattern graph nodes: 15
- Decisions: ALLOW / WARN / BLOCK
- OpenAI keys required: 0
- AMD LLM provider: Fireworks AI (AMD Instinct GPUs)
- Gemma model: accounts/fireworks/models/gemma3-4b-it
- Live URL: https://safeo-shield-1.onrender.com
- GitHub: https://github.com/CandyButcher27/safeo-shield
