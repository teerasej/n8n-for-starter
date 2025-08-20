# Copilot instructions for this repo (n8n workshop for non‑technical learners)

Purpose
- Generate step‑by‑step workshop docs that teach n8n using plain language.
- Minimize tech jargon. Always use exact n8n feature/node names to avoid confusion.
- Every important/complex step includes a screenshot markdown with a descriptive caption.
- Provide Thai translation for all English content. Keep n8n node/feature names in English.

Audience
- New to automation and n8n. No coding background expected.

Writing principles
- Use short sentences, active voice, present tense.
- Explain “why” before “how”. One action per step.
- Use exact n8n node names in quotes (e.g., "Webhook", "HTTP Request", "IF", "Set").
- Prefer nodes over custom code. If code is needed, keep it minimal and explain purpose.

File and folder structure
- README.md: overview and syllabus.
- docs/lessons/lesson-XX/README.md: one lesson per folder.
- docs/images/lesson-XX/step-YY-slug.png: screenshots per step.
- docs/snippets/lesson-XX/: optional small JSON exports or text snippets.

Screenshot rules
- Include a screenshot for any step that is important or complex.
- Always include:
    - Alt text: what the image shows.
    - Caption/description: what to capture and why it matters.
- Use this relative path pattern:
    - docs/images/lesson-XX/step-YY-slug.png
- If the image is not ready, keep the image markdown with a clear description so a human can capture it later.

Bilingual rule (English + Thai)
- Write English first, then a Thai translation block tagged with [TH].
- Keep n8n node/feature names in English inside quotes.
- Use simple Thai. Do not translate brand/product/node names.
- Example pattern:
    - English paragraph
    - [TH] Thai translation of the same paragraph

Common n8n building blocks to prefer
- Triggers: "Webhook", "Schedule Trigger".
- Logic: "IF", "Merge", "Split In Batches", "Wait".
- Data: "Set", "Move Binary Data".
- Integrations: "HTTP Request".
- Orchestration: "Execute Workflow".
- Code only when necessary: "Code" (JavaScript), keep it short and explained.

Lesson structure (apply to every docs/lessons/lesson-XX/README.md)
- Title
- What you will build (1–3 sentences)
- Prerequisites (accounts, access, n8n version)
- Time required
- Outcome (what the user can do at the end)
- Steps (numbered)
- Troubleshooting
- Next steps

Step format (repeat for each step)
- Step N: Short action title
    - Why: brief reason
    - Do this:
        - Clear, ordered actions in n8n
        - Use exact node names and key fields users will click/fill
    - Success check: what the user should see or get
    - Important/complex? Add a screenshot under the step:

        ![Alt: <what this screenshot shows>](../../images/lesson-XX/step-NN-slug.png)
        Description: <what to capture and what to highlight (e.g., field names, toggles, run result)>

    - [TH] Thai translation of the whole step above, preserving node names in English.
        - Include the same screenshot (no need to duplicate the file), and Thai caption/description.

Quality checklist (for every lesson)
- Steps are numbered and start with a verb.
- Each step has a “Why” and a “Success check”.
- Important/complex steps include a screenshot with a clear description.
- All English content has a [TH] translation block.
- Node names match n8n exactly (case and spacing).
- Avoid unexplained jargon. Define terms in simple words if used once.
- Prefer node configurations to code. If code exists, explain in one sentence.

Template: lesson README.md (copy and fill)
# Lesson XX — <short, outcome-focused title>

What you will build
- <1–3 sentences in plain language explaining the automation outcome>
[TH] <Thai translation>

Prerequisites
- n8n account or local n8n running
- <any required service/account>
[TH] <Thai translation>

Time required
- ~<minutes>
[TH] <Thai translation>

Outcome
- <clear statement of what learners can do after this lesson>
[TH] <Thai translation>

Steps

Step 1: <create or configure something in n8n>
- Why: <reason in one sentence>
- Do this:
    - Open n8n and create a new workflow.
    - Add a "Webhook" node. Copy the "Test URL".
    - Set HTTP Method to "POST".
- Success check: You see a Test URL on the "Webhook" node.
![Alt: Webhook node with Test URL visible](../../images/lesson-XX/step-01-webhook-url.png)
Description: Capture the "Webhook" node on the canvas with the Test URL highlighted.

[TH] ขั้นตอนที่ 1: <หัวข้อการกระทำ>
- ทำไม: <เหตุผลแบบสั้น>
- วิธีทำ:
    - เปิด n8n และสร้างเวิร์กโฟลว์ใหม่
    - เพิ่มโหนด "Webhook" และคัดลอก "Test URL"
    - ตั้งค่า HTTP Method เป็น "POST"
- ตรวจสอบความสำเร็จ: เห็น Test URL บนโหนด "Webhook"
![Alt: โหนด Webhook แสดง Test URL](../../images/lesson-XX/step-01-webhook-url.png)
คำอธิบาย: ถ่ายภาพโหนด "Webhook" บนผืนงาน โดยไฮไลต์ตำแหน่ง Test URL

Step 2: <send or receive data>
- Why: <reason>
- Do this:
    - Add an "HTTP Request" node connected after "Webhook".
    - Method: "POST", URL: <sample endpoint or mock>
    - Send JSON from previous node.
- Success check: The "HTTP Request" node shows a 200 OK in the Execution.
![Alt: HTTP Request node successful run with 200 status](../../images/lesson-XX/step-02-http-200.png)
Description: Capture the Execution view with the "HTTP Request" node expanded, showing Status 200 and response body.

[TH] ขั้นตอนที่ 2: <ส่งหรือรับข้อมูล>
- ทำไม: <เหตุผล>
- วิธีทำ:
    - เพิ่มโหนด "HTTP Request" ต่อจาก "Webhook"
    - Method: "POST", URL: <ปลายทางตัวอย่างหรือ mock>
    - ส่ง JSON จากโหนดก่อนหน้า
- ตรวจสอบความสำเร็จ: โหนด "HTTP Request" แสดงสถานะ 200 OK ใน Execution
![Alt: โหนด HTTP Request แสดงผลลัพธ์ 200](../../images/lesson-XX/step-02-http-200.png)
คำอธิบาย: ถ่ายภาพมุมมอง Execution โดยขยายโหนด "HTTP Request" ให้เห็น Status 200 และเนื้อหาคำตอบ

Step 3: <add simple logic with "IF">
- Why: <reason>
- Do this:
    - Add an "IF" node. Condition: response.status equals 200.
    - On "true", add a "Set" node to format a success message.
- Success check: On test run, the "true" branch is taken and the "Set" node shows your message.
![Alt: IF node true branch with Set node output](../../images/lesson-XX/step-03-if-true.png)
Description: Capture the "IF" condition and the green (true) connection to the "Set" node with output preview.

[TH] ขั้นตอนที่ 3: <เพิ่มเงื่อนไขด้วย "IF">
- ทำไม: <เหตุผล>
- วิธีทำ:
    - เพิ่มโหนด "IF" ตั้งค่าเงื่อนไข: response.status เท่ากับ 200
    - ในแขนง "true" เพิ่มโหนด "Set" เพื่อสร้างข้อความสำเร็จ
- ตรวจสอบความสำเร็จ: เมื่อลองรัน แขนง "true" ทำงาน และโหนด "Set" แสดงข้อความของคุณ
![Alt: โหนด IF แขนง true และผลลัพธ์ของ Set](../../images/lesson-XX/step-03-if-true.png)
คำอธิบาย: ถ่ายภาพเงื่อนไขของ "IF" และสายเชื่อมสีเขียว (true) ไปยังโหนด "Set" พร้อมตัวอย่างผลลัพธ์

Troubleshooting
- Webhook not receiving data: Ensure you use the "Test URL" while testing and the "Production URL" after publishing.
- HTTP 4xx/5xx: Check URL, method, headers, and body format. Try with sample payload first.
[TH] แก้ปัญหา
- Webhook ไม่ได้รับข้อมูล: ใช้ "Test URL" ระหว่างทดสอบ และใช้ "Production URL" หลังเผยแพร่
- HTTP 4xx/5xx: ตรวจสอบ URL, method, headers และรูปแบบข้อมูล ลองด้วย payload ตัวอย่างก่อน

Next steps
- Add "Wait" to delay actions.
- Use "Merge" to combine data from two branches.
- Export the workflow and share.
[TH] ขั้นต่อไป
- เพิ่ม "Wait" เพื่อหน่วงเวลา
- ใช้ "Merge" เพื่อรวมข้อมูลจากสองแขนง
- ส่งออกเวิร์กโฟลว์และแชร์

Submission checklist (per lesson)
- All steps include Why, Do this, Success check.
- Important/complex steps have screenshots and captions.
- English + [TH] translation present for all content.
- Filenames and paths follow the patterns above.
- Tested the workflow end‑to‑end at least once.
