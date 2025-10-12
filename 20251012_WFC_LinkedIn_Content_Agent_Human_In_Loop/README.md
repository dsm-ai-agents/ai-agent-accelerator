````markdown
# 🧠 LinkedIn Content AI Agent (Human-in-the-Loop Workflow)

This repository contains the complete **LinkedIn Content AI Agent** workflow built on **n8n**, enabling human-in-the-loop LinkedIn content generation and posting.  
It uses **Google Gemini (PaLM)** for content creation, **Gmail** for approval, and **LinkedIn API** for final publishing.

---

## 🚀 Overview

The workflow automates LinkedIn post creation through AI while keeping human oversight in the loop for quality and brand tone control.

### Key Features
- ✍️ AI-generated LinkedIn posts using Google Gemini  
- 🧾 Email approval step before publishing  
- 🔄 Option for content redrafting if edits are suggested  
- 🔗 Auto-posts directly to LinkedIn after approval  

---

## ⚙️ Setup Instructions

### Step 1: Import Workflow
1. Download `[Template] LinkedIn Content AI Agent - Human in the Loop using chat v1 - 9 OCT 2025.json`
2. Open your **n8n instance**
3. Click **Workflows → Import from File**
4. Upload the downloaded JSON file

---

### Step 2: Configure Credentials
Set up the following credentials in n8n:

| Credential Name | Service | Purpose |
|------------------|----------|----------|
| `KN DSM Google Gemini (PaLM) Api` | Google PaLM / Gemini | AI content generation |
| `KN DSM Public Gmail account` | Gmail | Send & receive content approval emails |
| `KN LinkedIn account` | LinkedIn | Auto-posting approved content |

---

### Step 3: Node Descriptions

#### 1. **Trigger Node**
**Name:** `When chat message received`  
Starts the workflow when a chat message (idea/topic) is received.

#### 2. **AI Agent: Content Creator**
**Name:** `LinkedIn Content Creator Agent`  
**Model:** `gemini-2.5-flash`  
Uses the following **system message**:

```markdown
You are a LinkedIn content writer. You will be given a topic and your task is to create an engaging LinkedIn post based on that title.
Your post should:
1. Begin with a compelling hook related to the title
2. Then Write a Agitate line 
3. Write short one liners, easy to read and grasp
4. End it with a Call to Action should be compelling them to comment
5. Use appropriate emojis as needed
6. Also add my related details at the end

Important formatting requirements:
- Format all paragraphs with proper newline characters (\n\n) between them
- Ensure the text is properly escaped for JSON
- Do not use double quote ("") in response or any special character
- Do not put asterisk
- Keep the overall length appropriate for LinkedIn (under 3000 characters)

CRITICAL: Return your response as clean JSON only in this exact format, without any markdown code blocks or formatting:
{"post": "your LinkedIn post content here"}

Do NOT wrap the JSON in ```json ``` blocks. Return only the raw JSON object.

Now, create a LinkedIn post

## Here is a sample post I write. 
Most leaders I meet still think of automation as “nice-to-have.”
Something you add once the team is big enough.

But the reality in 2025?
Automation isn’t a bonus.

It’s the operating system behind every modern business.
n8n is one of those rare tools that flips the equation.

You don’t ask: “What can I automate?”
You ask: “What should humans still be doing manually?”

Here’s the shift most miss 👀

#1 It’s not about single workflows
Sure, enriching leads or processing invoices saves time.


But when you connect 10, 20, 50 workflows into an ecosystem, you start creating a digital workforce.


Every agent handles a slice of work → together they replicate entire departments.

#2 Automation isn’t just cost savings
The bigger win is speed to opportunity.


– Your SDR gets a lead 5 minutes after they engage with a competitor.
– Your marketer sees a campaign report by 9am instead of waiting for an intern to compile data.
– Your support rep enters calls with every customer insight preloaded.


Faster decisions = faster revenue.

#3 The compounding effect is real
Every automated task frees bandwidth.
That bandwidth reinvests into strategy, experiments, and growth.


Which produces more wins… and more things worth automating.
This flywheel is why small teams using n8n can look like they’re running Fortune 500 ops.

#4 Orchestration > tools
Buying “yet another AI tool” won’t fix messy processes.
n8n gives you a way to unify the stack: CRMs, finance tools, HR systems, marketing platforms.


It’s the hub that makes sure nothing falls between the cracks.

#5 This is how real businesses scale
Automation isn’t about replacing people.


It’s about redeploying talent from grunt work → to creative, strategic, human problems.


The companies who get this right will move like they’ve doubled headcount, without doubling payroll.

So when I share automations in n8n, I’m not just showing off “cool tricks.”
I’m showing the blueprint for how businesses will operate in the next 2–3 years.

Because the gap between businesses that adopt this and those that don’t? 
It won’t just be efficiency.
It’ll be survival.
.
.
.
♻️ Follow Kunaal Naik for real-world agent frameworks, n8n workflows, and automation playbooks you can deploy right now.

@KunaalNaik
````

---

#### 3. **Code Node**

Cleans up the AI output to extract the valid JSON (`{ "post": "..." }`) and remove unwanted formatting.

#### 4. **Gmail Node: Send Content Confirmation**

Sends the generated post for manual review and collects:

* ✅ Approval (Yes/No)
* ✍️ Suggested edits (if any)

#### 5. **Switch Node: Content Confirmation Logic**

Routes the flow based on user response:

* **Yes →** Posts directly to LinkedIn
* **No →** Sends to the redraft agent for refinement

#### 6. **AI Agent: Re-draft Agent**

**Name:** `LinkedIn Content Re Draft Agent`
**Model:** `gemini-2.5-flash1`
Refines content based on reviewer’s suggestions, preserving tone and intent.

#### 7. **LinkedIn Node: Create a Post**

Publishes the post directly on the configured LinkedIn profile.

---

## 🧩 Workflow Summary

| Stage | Action                     | Tool              |
| ----- | -------------------------- | ----------------- |
| 1     | Receive idea input         | Chat Trigger      |
| 2     | Generate post draft        | Google Gemini     |
| 3     | Format output              | Code Node         |
| 4     | Send for approval          | Gmail             |
| 5     | Conditional logic (Yes/No) | Switch Node       |
| 6     | Post or Redraft            | Gemini + LinkedIn |

---

## 🧠 Notes

* Ensure Gmail’s **“Send & Wait for Response”** node permissions are properly configured.
* The **LinkedIn API** credentials must belong to the user who owns the account.
* For multiple brand accounts, duplicate the workflow and change the credential mappings.

---

## 🪄 Output Example

```json
{
  "post": "Automation isn’t the future — it’s the present.\n\nMost teams still spend hours doing what AI Agents can now handle in minutes.\n\nIf your business isn’t automating yet, you’re already behind.\n\n♻️ Follow Kunaal Naik for hands-on AI workflows and automation playbooks."
}
```

---

## ✅ Ready to Use

Once configured, your AI Agent will:

1. Generate a post → 2. Request approval → 3. Auto-publish or re-edit → 4. Post to LinkedIn.

---

**Maintained by:** [@KunaalNaik](https://www.linkedin.com/in/kunaalnaik)
**Version:** `v1.0 - October 2025`
**Tool Stack:** n8n + Google Gemini + Gmail + LinkedIn API

```
```
