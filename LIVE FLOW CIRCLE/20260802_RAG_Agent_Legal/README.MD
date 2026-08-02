# Exercise: Build a Simple Legal Contract RAG Knowledge Base

## Learning Objective

By the end of this exercise, participants should understand:

- Why RAG (Retrieval-Augmented Generation) exists.
- Why sending every document to an LLM is expensive.
- How indexing reduces token usage and cost.
- How Claude CoWork can organize documents into a searchable knowledge base.

---

# Breakout Room 1 — Why Do We Need RAG?

## Scenario

Imagine a company has **25 legal contracts**.

The CEO asks:

> "Which contracts allow termination for convenience?"

### Option A (No RAG)

The AI reads all 25 contracts every time.

```
Question
      ↓
Read 25 Contracts
      ↓
LLM
      ↓
Answer
```

Problems

- Large input tokens
- Slow responses
- Higher API cost
- Doesn't scale to 1000+ contracts

---

### Option B (With RAG)

The AI first finds the relevant contracts.

```
Question
      ↓
Find Relevant Contracts
      ↓
Read Only 2-3 Contracts
      ↓
LLM
      ↓
Answer
```

Benefits

- Lower token usage
- Lower cost
- Faster responses
- Scales to thousands of documents

---

## Discussion Questions

Research and discuss:

- What is an LLM?
- What are Input Tokens?
- What are Output Tokens?
- Why do tokens cost money?
- What is RAG?
- Why doesn't RAG send every document to the model?

---

## Takeaway

> **The challenge is not answering questions.**
>
> **The challenge is finding the smallest set of relevant documents before asking the LLM.**

---

# Breakout Room 2 — Build a Simple Knowledge Base

## Starting Folder

```
contracts/

01.md
02.md
03.md
...
25.md
```

Each Markdown file contains one legal contract.

---

## Your Goal

Help Claude organize these contracts so it can answer questions without reading all 25 files every time.

Claude should:

- Read every contract
- Identify the contract type
- Group similar contracts together
- Create an index
- Add a short summary for each contract
- Keep the original contract unchanged

The final folder might look like:

```
contracts/

index.md

service-agreements/
    index.md
    01.md
    04.md

employment/
    index.md
    08.md

vendor/
    index.md
    11.md

nda/
    index.md
    17.md
```

Claude should decide the categories based on the documents.

---

# Simple Claude Prompt

```
You have a folder containing Markdown versions of legal contracts.

Read every contract.

Create a small knowledge base by:

1. Grouping similar contracts into folders.
2. Creating an index.md inside each folder listing every contract.
3. Creating a root index.md linking to every category.
4. Writing a short factual summary for each contract.
5. Do not change the contract text.

The goal is to help another AI quickly locate the correct contracts before answering questions.
```

---

# Example Retrieval Flow

```
User asks

"Which contracts contain automatic renewal?"

        ↓

Read index.md

        ↓

Open "Service Agreements"

        ↓

Read category index

        ↓

Open only 2 relevant contracts

        ↓

Answer with clause references
```

Instead of reading all 25 contracts, the AI reads only what it needs.

---

# Sample Questions

- Which contracts expire this year?
- Which contracts mention automatic renewal?
- Which agreements contain confidentiality clauses?
- Which contracts are governed by Indian law?
- Compare payment terms across service agreements.
- Which contracts have missing dates?
- Which contracts should be reviewed manually?

---

# Pre-Step (Before the Exercise)

The contracts are initially PDFs.

A simple conversion script is run first:

```
PDF
   ↓
Markdown (.md)
```

Claude CoWork then works only with the Markdown files to build the knowledge base.

---

# Key Learning

The objective is **not** to build a perfect legal search engine.

The objective is to understand the RAG workflow:

```
PDFs
      ↓
Markdown Conversion
      ↓
Knowledge Base Creation
      ↓
Index Generation
      ↓
User Question
      ↓
Find Relevant Documents
      ↓
LLM Reads Only Those Documents
      ↓
Grounded Answer
```

> **Core Principle:** The more accurately you narrow down the documents before sending them to the LLM, the lower the token cost, the faster the response, and the better the scalability.