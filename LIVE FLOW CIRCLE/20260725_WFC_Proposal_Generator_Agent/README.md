# AI Proposal Generator Workshop

Build a multi-input AI Proposal Generator that creates a professional consulting presentation for an AI Customer Support solution.

---

# 🎯 Objective

Your objective is to design and build an AI Proposal Generator that can create a consulting-style proposal presentation for a client.

Unlike a simple prompt, this agent should combine information from multiple business documents before generating a high-quality proposal.

Think like an AI Consultant, not just an AI Prompt Engineer.

---

# 📚 Business Scenario

ABC Electronics is a rapidly growing online electronics retailer.

The company receives hundreds of customer enquiries every day through:

- WhatsApp
- Website Chat
- Email
- Phone

Their customer support team is overwhelmed with repetitive enquiries such as:

- Where is my order?
- How do I return a product?
- Warranty questions
- Product availability
- Delivery timelines

The company wants to implement an AI Customer Support Agent to improve customer experience while reducing operational costs.

Your AI Proposal Generator will prepare a consulting proposal that recommends the best solution.

---

# 🚀 Workshop Flow

## Step 1 — Understand the Problem

Read the Workshop Exercise Brief.

Discuss:

- What is the client's problem?
- What information is required?
- What should the Proposal Agent produce?
- What inputs will make the proposal better?

Do **not** start building yet.

---

## Step 2 — Review the Assets

Once your discussion is complete, you will receive the project assets.

These documents simulate the information a consulting firm would normally collect before preparing a proposal.

Review every document carefully.

---

## Step 3 — Understand the Inputs

The Proposal Agent should use all of the supplied information rather than relying on a single prompt.

Available assets include:

- Discovery Meeting Transcript
- Solution Recommendation Meeting
- Industry Research
- Pricing Rate Card
- Proposal Deck Guide

Think about:

- Which information should be extracted?
- Which sections belong in the proposal?
- How should pricing be calculated?
- What information should appear on each slide?

---

## Step 4 — Build the Proposal Generator

Using your preferred AI platform, build an agent that can:

- Read all provided documents
- Understand the client's business
- Understand the recommended solution
- Extract commercial information
- Generate a professional consulting proposal

---

## Step 5 — Generate the Presentation

The final output should be a consulting-style presentation containing approximately 10–12 slides.

Suggested sections include:

1. Title
2. Executive Summary
3. Client Overview
4. Current Challenges
5. Proposed AI Solution
6. Solution Architecture
7. Scope & Deliverables
8. Implementation Roadmap
9. Investment
10. Expected Business Benefits
11. Risks & Assumptions
12. Next Steps

---

# 📁 Project Files

```
00_Workshop_Exercise_Brief.docx

01_Discovery_Meeting.txt

02_Solution_Recommendation.txt

03_Industry_Research.pdf

04_Pricing_Rate_Card.csv

05_Proposal_Deck_Input_Guide.docx
```

---
# Prompts
Prompt #1
```
Look at the files in the folder and tell me what do you understand
```

Prompt #2
```
create a Claude.MD file, which will, take in the inputs that is the one, two, three, four, these four files as the inputs. distill the content of this into a step one underscore the content.MD. this will be the first agent that will take these four files and get the important content slide wise based on the proposal deck input guide that we have provided that is a zero five. read all the slides that are available in zero five proposal deck input and organize and a content.md and store it into the content folder which is empty currently. And then I wanted to create a step two underscore proposal.MD which is going to take the content.MD and produce a PowerPoint presentation, McKenzie style very good high-tech consulting type proposal deck and create a PowerPoint presentation in the output file. First, I want you to create all these things before you run all of these steps. First, each step should be created, Claude MD, step one and step two agents, and then we are going to execute it.
```
---

# 💡 Success Criteria

A successful Proposal Generator should:

- Read information from multiple documents
- Combine business and commercial insights
- Create a logical consulting proposal
- Produce consistent recommendations
- Calculate pricing correctly
- Present information professionally

---

# 🎯 Expected Learning Outcomes

By the end of this workshop, you will understand how to:

- Build multi-document AI workflows
- Combine structured and unstructured data
- Generate professional consulting proposals
- Design AI agents that reason across multiple inputs
- Create presentation-ready business deliverables

---

Happy Building! 🚀