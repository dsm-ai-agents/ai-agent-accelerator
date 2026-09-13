# Simple NexaFlow Knowledge Base Demo

## Purpose

This is the simplest version of the RAG demonstration.

The starting point is a folder containing 25 internal Markdown (`.md`) documents
for **NexaFlow Technologies**, a fictional B2B SaaS company that sells a workflow
automation and AI operations platform. The documents cover product, pricing,
implementation, customer case studies and sales. The files are numbered `01`
through `25`.

The team then runs **one prompt**. The agent reads the documents, normalizes
their metadata, identifies the natural knowledge categories, creates the
knowledge-base folders and indexes, and moves the files into the appropriate
folders.

## Starting folder

```text
nexaflow_knowledge_base/
├── 01_product_overview.md
├── 02_feature_matrix.md
├── 03_integration_guide.md
├── ...
└── 25_demo_script.md
```

## The one prompt

Point the agent at the `nexaflow_knowledge_base` folder and paste this prompt:

```text
You are a company knowledge-base organizer.

CONTEXT
The current folder contains 25 internal Markdown documents for NexaFlow
Technologies, a B2B SaaS company selling a workflow automation and AI operations
platform. The documents cover product, pricing, implementation, case studies and
sales. Some documents overlap, and some contain outdated or historical
information. Build a simple, navigable knowledge base from these files.

OBJECTIVE
Read the Markdown documents, classify them by their dominant business purpose,
normalize their metadata, organize them into useful folders, and create indexes
that another LLM can use for index-first retrieval.

WORKFLOW
1. Inventory every Markdown document in the current folder.
2. Read each document sufficiently to identify its title, document type,
   dominant purpose, version, status, last-updated date, whether it is
   authoritative, the questions it answers, and its important topics.
3. Normalize the YAML front matter at the top of each document using the shape
   below. Keep existing correct values. Do not change the body text while
   adding metadata.
4. Infer a small and practical taxonomy from the actual documents. Prefer
   approximately 4 to 6 non-overlapping main categories. Do not invent a
   category before examining the corpus.
5. Assign every document exactly one main category. A document may have several
   secondary topics and RAG tags.
6. Create one filesystem-safe folder for each main category.
7. Move each document into its assigned category folder. Preserve its document
   ID and filename.
8. Create an index.md inside every category folder.
9. Create a root index.md that routes questions to the correct category index.
10. Validate all links, metadata, document counts, and file locations.

USE THIS YAML SHAPE
---
document_id: "NEXA-001"
title: "Full document title"
document_type: "Guide, Policy, Price List, FAQ, Case Study, Template, or other"
main_category: "One primary category"
secondary_topics:
  - "Topic one"
  - "Topic two"
rag_tags:
  - "lowercase-kebab-case-tag"
  - "another-search-tag"
version: "Version number"
status: "Current, Historical, Draft, or Unknown"
last_updated: "YYYY-MM-DD or Unknown"
authoritative: "Yes or No"
supersedes: "Older document or version this replaces, or None"
contains_outdated_information: "Yes or No"
related_documents:
  - "NN_filename.md"
summary: "One or two factual sentences describing the document"
key_topics:
  - "Important fact, figure, or process covered"
use_when: "The kinds of questions this document should answer"
---

METADATA RULES
- Use only facts supported by the document.
- Use "Unknown" when a value cannot be established.
- If a document contains historical or outdated figures, set
  contains_outdated_information to "Yes" and name the current authoritative
  document in the summary.
- Keep main_category broad enough to contain multiple related documents.
- Put granular concepts in secondary_topics, key_topics, and rag_tags.
- Use lowercase kebab-case for rag_tags.
- Keep summaries factual and neutral.

EACH CATEGORY INDEX.MD MUST CONTAIN
- Category name and plain-language description.
- Types of questions that should be routed to the category.
- A Markdown table listing every document in the folder.
- For each document: document ID, title, document type, version, status,
  authoritative flag, important topics, and a relative Markdown link.
- Useful search terms and RAG tags.
- Important overlaps with other categories, if any.
- Any version conflicts inside the category and which document wins.
- An instruction to open the underlying document before answering questions
  that need exact figures, steps, or timelines.

THE ROOT INDEX.MD MUST CONTAIN
- A short explanation of the knowledge base.
- The total document count and category count.
- A category-routing table containing the category name, purpose, example
  questions, document count, and relative link to its index.md.
- A compact document directory listing all documents and their locations.
- Cross-category routing guidance.
- A version-control section naming the authoritative source for any topic where
  documents disagree.
- The following retrieval procedure:
  1. Read the root index.md.
  2. Select the most relevant category or categories.
  3. Read the selected category index.md.
  4. Select the smallest relevant set of documents (usually 2 to 3).
  5. Prefer documents that are authoritative and current.
  6. Read the selected documents.
  7. Answer using document-supported facts and cite the document ID, filename,
     and relevant section.
  8. If the answer is not in the knowledge base, say so instead of guessing.
- A warning not to treat index summaries as a substitute for the document text.

SAFETY AND QUALITY RULES
- Never fabricate a price, date, metric, feature, or policy.
- Never present historical or outdated information as current.
- Preserve the original document body text.
- Do not delete source content.
- If classification is uncertain, choose the best-supported main category and
  record the uncertainty in the category index.
- Use relative Markdown links.
- Use deterministic, filesystem-safe folder names.
- Resolve duplicate document IDs before completing the task.
- Confirm that every inventoried document appears exactly once in the organized
  knowledge base.
- Report missing, unreadable, duplicated, or conflicting files.

FINAL RESPONSE
After completing the work, report:
- Number of documents inventoried.
- Number of documents organized.
- Categories created and their document counts.
- Version conflicts found and which document is authoritative.
- Files that need human review.
- Validation errors or unresolved uncertainties.
- Path to the root index.md.
```

## Expected result

The exact category names should be derived from the 25 documents. A typical
result will look like this:

```text
nexaflow_knowledge_base/
├── index.md
├── product/
│   ├── index.md
│   └── ...
├── pricing/
│   ├── index.md
│   └── ...
├── implementation/
│   ├── index.md
│   └── ...
├── case-studies/
│   ├── index.md
│   └── ...
└── sales/
    ├── index.md
    └── ...
```

## Test it

Start a new chat and ask a question:

```text
Using nexaflow_knowledge_base/index.md, answer: What is the onboarding process and typical timeline for an enterprise customer? Cite the files you used.
```

More questions to try:

```text
Using nexaflow_knowledge_base/index.md, answer: What does the Enterprise plan cost, and are annual discounts available? Cite the files you used.
```

```text
Using nexaflow_knowledge_base/index.md, answer: Does the platform support SSO, audit logs and role-based access? Cite the files you used.
```

```text
Using nexaflow_knowledge_base/index.md, answer: Have we helped a manufacturing company reduce manual work? Cite the files you used.
```

```text
Using nexaflow_knowledge_base/index.md, answer: How should I respond if a prospect says the solution is too expensive? Cite the files you used.
```

```text
Using nexaflow_knowledge_base/index.md, answer: A customer says Enterprise costs $85 per user per month. Are they right? Cite the files you used.
```


# Prompt for creating a user interface
```
Okay. So now I want you to create a a a user interface where I can provide this chat application to my team members as an independent web application where they can type and get responses based on the knowledge base that we have. Right? So create... can you create a a a, first of all, prototype? Quick prototype that we can use it where I can just type and get an an an an the the answer. You can also convert it into an artifact which, uh, which is, like, demo able shareable. Okay. So first, give me the plan, and then I'll approve the new create it.
```