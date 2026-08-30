# Prompt 1
```
Create a B2B LinkedIn content creator agent pipeline from scratch. Do not run or execute any agent — only create the files and folders.

First create `CLAUDE.md` with project goal, workflow, folders, inputs, outputs, tools, and agent roles.

Folders:
- inputs/
- outputs/
- outputs/posts/
- outputs/images/
- agents/

Agents:

`agent_1_intake.md` — asks the user exactly 5 questions. Every question must be multiple-select (buttons, not free text), and every question must include an "Other" option so the user can type their own answer. Questions should be simple and cover: who they are, their title/role, their objective on LinkedIn, their experience level, and their preferred tone. Save all answers to `inputs/user_profile.md` as a plain Markdown file (not JSON).

`agent_2_research_calendar.md` — reads `inputs/user_profile.md`. Asks the user "How many pieces of content?" with options 3, 5, 7, and "Other" — default scope is 7 days. Does industry research and generates a content calendar. Output includes:
- Viral hooks
- Industry research notes saved to `outputs/research_notes.md`
- A content calendar saved to `outputs/content_calendar.md`
- Each individual post saved as its own file in `outputs/posts/` (e.g. `post_01.md`, `post_02.md`, etc.)

`agent_3_image_gen.md` — optional. By default, builds a simple HTML template per post and exports it to PNG (no API keys required), saved to `outputs/images/`. Must clearly tell the user that if they want higher-quality/branded images, they need to supply their own image-generation API key.

`agent_4_post_test.md` — picks one post from the generated batch and runs a test pass on it (checks hook strength, formatting, length), logs the result to `outputs/test_log.md`.

Before creating any files, show the proposed architecture, workflow, folders, and outputs for approval. Do not execute any agent — only scaffold the files and folder structure. Do it in the local folder.

Keep it as crisp as this brief, without overcomplicating it.
```

# Prompt 1b
```
Two additions to the scaffold:

1. Update `agent_3_image_gen.md`: before generating, ask the user their image style (background/text color, bottom-left and bottom-right text) as button options with "Other". Render PNGs using whatever the environment supports — HTML→PNG if a headless browser exists, otherwise draw directly with PIL. Never attempt to install a browser.

2. Create `agent_5_publish.md` and `outputs/posts/completed/`: publishes one post to LinkedIn via the Composio connector, then moves it to completed/. For images, generate the image inside Composio's remote sandbox (Python/PIL available there) and upload with `upload_local_file` to get an s3key — never relay base64 image bytes from the local sandbox into Composio, it corrupts. Confirm post text with the user once before publishing.

Update CLAUDE.md to reflect both. Scaffold only — do not run any agent.
```

# Prompt 2
```
Activate Agent 1
```

# Prompt 3
```
Activate Agent 2
```

# Prompt 4
```
Activate Agent 3
```

# Prompt 5
```
Activate Agent 4
```

# Prompt 6
```
Schedule agent_5 to publish one post every day at 11AM and move it to the completed folder
```
