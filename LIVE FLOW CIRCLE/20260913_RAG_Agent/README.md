# Exercise: Build an Agentic RAG Knowledge Base — NexaFlow Technologies

`nexaflow_docs/` holds 25 internal Markdown documents for **NexaFlow Technologies**, a fictional B2B SaaS company selling a workflow automation and AI operations platform. The documents cover five areas — Product, Pricing, Implementation, Case Studies and Sales — and are deliberately messy: they overlap, cross-reference each other, and one of them contains **outdated prices**.

You will turn this folder into an indexed knowledge base, then use it as a RAG agent that follows this flow:

```
Question → Read root index → Pick folder → Read folder index → Open only 2–3 files → Answer with citations
```

**How to use:** Point Claude (Cowork / Claude Code) at the folder containing `nexaflow_docs/`. Run the prompts below **one by one, in order**. Start a new chat only where the step says so.

---

## Step 1 — Scan the Metadata Only

```
The nexaflow_docs folder contains 25 Markdown files. Do NOT read the full content of every file.

For each file, read only the "Metadata" section at the top and give me one table with these columns:
File Name | Category | Document Type | Version | Status | Last Updated | Authoritative

Below the table, point out:
- Any file that is marked as NOT authoritative.
- Any file whose status mentions historical or outdated content.
```

---

## Step 2 — Build the Knowledge Base

```
Read every file in the nexaflow_docs folder and build a small knowledge base that another AI agent can navigate quickly.

1. Create a new folder called "knowledge_base" next to nexaflow_docs.
2. Inside it, create one sub-folder per category: product, pricing, implementation, case_studies, sales.
3. Copy each Markdown file into the correct sub-folder. Do NOT change the text of any file. Do NOT modify or delete the originals in nexaflow_docs.
4. Inside each sub-folder, create an index.md with a table listing every file in that folder:
   File | 1–2 sentence factual summary | Version | Status | Authoritative | Keywords | Use When
5. Create a root knowledge_base/index.md that contains:
   - A one-paragraph description of the company and the knowledge base.
   - A table of the 5 categories with a link to each folder's index.md and the types of questions that belong there.
   - An "Intent Routing" section with 2–3 example questions per category.
   - A "Version Control" section that names the authoritative source for prices and flags any file that contains outdated information.

The goal is to help another AI agent find the smallest set of correct files before answering a question.
```

---

## Step 3 — Verify the Knowledge Base

```
Check the knowledge_base folder you just created and report:

1. Are all 25 files present, each in exactly one category folder?
2. Is the content of every copied file identical to the original in nexaflow_docs?
3. Does every link in the root index.md and in each folder index.md point to a file that exists?
4. Are there any facts that conflict across files (for example different prices or timelines)? For each conflict, say which file is authoritative and whether the index already flags it.

Fix anything that is broken or missing in the index files, then show me the final root index.md.
```

---

## Step 4 — Write the Retrieval Agent Instructions

```
Create a file called knowledge_base/AGENT_INSTRUCTIONS.md that tells an AI agent exactly how to answer questions using this knowledge base.

The instructions must enforce this workflow:
1. Always read knowledge_base/index.md first.
2. Identify the intent of the question and choose the most relevant category folder (or two folders if the question truly spans both).
3. Read that folder's index.md.
4. Open only the 2–3 most relevant files. Never open every file.
5. Prefer files marked "Authoritative: Yes" and the latest version. Ignore content marked historical or outdated unless the question is explicitly about history.
6. Answer only from the files opened. If the answer is not in the knowledge base, say so clearly — do not guess.
7. End every answer with a "Sources" list of the exact file paths used.
8. Before the answer, show a short "Retrieval Path": intent detected → folder chosen → files opened → files deliberately skipped.

Keep the instructions short and clear.
```

---

## Step 5 — Test: Implementation Question

**Start a new chat.** (Steps 5–11 can all run in this same new chat.)

```
Follow the rules in knowledge_base/AGENT_INSTRUCTIONS.md exactly.

Question: "What is the onboarding process and typical timeline for an enterprise customer?"
```

---

## Step 6 — Test: Pricing Question

```
Follow the rules in knowledge_base/AGENT_INSTRUCTIONS.md exactly.

Question: "What does the Enterprise plan cost, and are annual discounts available?"
```

---

## Step 7 — Test: Product Question

```
Follow the rules in knowledge_base/AGENT_INSTRUCTIONS.md exactly.

Question: "Does the platform support APIs, SSO, audit logs and role-based access? Which plans include them?"
```

---

## Step 8 — Test: Case Study Question

```
Follow the rules in knowledge_base/AGENT_INSTRUCTIONS.md exactly.

Question: "Have we helped a manufacturing company reduce manual work? Give me the numbers and how long the implementation took."
```

---

## Step 9 — Test: Sales Question

```
Follow the rules in knowledge_base/AGENT_INSTRUCTIONS.md exactly.

Question: "How should I respond if a prospect says the solution is too expensive? How much discount am I allowed to offer without approval?"
```

---

## Step 10 — Test: The Version-Control Trap

```
Follow the rules in knowledge_base/AGENT_INSTRUCTIONS.md exactly.

Question: "A customer says our Enterprise plan costs $85 per user per month. Are they right?"

In your answer, explain which file contains the $85 figure, why it is not the current price, and which file you treated as the source of truth.
```

---

## Step 11 — Test: Cross-Folder and Out-of-Scope Questions

```
Follow the rules in knowledge_base/AGENT_INSTRUCTIONS.md exactly. Answer these two questions separately, each with its own Retrieval Path and Sources.

Question A: "A 3,000-person healthcare provider needs HIPAA compliance. Roughly how long will onboarding take, and do we have a similar customer we can reference?"

Question B: "What is NexaFlow's refund policy if a Starter customer cancels in the middle of a month?"
```
