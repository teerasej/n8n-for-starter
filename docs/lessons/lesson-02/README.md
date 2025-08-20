# Lesson 02 — Getting Started with n8n (Hello Finance Workflow)

What you will build
- Create an n8n account, explore the editor, and build a simple “Hello Finance” workflow that receives a request, validates it, and replies.
[TH] สิ่งที่จะสร้าง
- สมัครและเข้าใช้งาน n8n รู้จักหน้าตาเครื่องมือ และสร้างเวิร์กโฟลว์ “Hello Finance” รับคำขอ ตรวจสอบ และตอบกลับ

Prerequisites
- n8n account or local n8n running
- A modern browser
[TH] ข้อกำหนดก่อนเริ่ม
- มีบัญชี n8n หรือรัน n8n แบบโลคัล
- ใช้เบราว์เซอร์รุ่นใหม่

Time required
- ~75 minutes
[TH] เวลาที่ใช้
- ~75 นาที

Outcome
- You can log in, navigate the editor, use key nodes, and run a test workflow end‑to‑end.
[TH] ผลลัพธ์
- เข้าใช้งานได้ รู้จักหน้าตาเครื่องมือ ใช้โหนดหลัก และทดสอบเวิร์กโฟลว์ได้ครบ

Steps

Step 1: Register and access your n8n account
- Why: You need a workspace to build workflows.
- Do this:
    - Go to n8n.io and sign up, or use your organization’s n8n URL.
    - Verify your email if prompted.
    - Log in and create a new workflow.
- Success check: You see an empty canvas and a “Start” node on the left panel.
![Alt: n8n editor new workflow canvas](../../images/lesson-02/step-01-new-workflow.png)
Description: Capture a fresh n8n workspace showing the empty canvas ready to add nodes.

[TH] ขั้นตอนที่ 1: สมัครและเข้าใช้งาน n8n
- ทำไม: ต้องมีพื้นที่ทำงานเพื่อสร้างเวิร์กโฟลว์
- วิธีทำ:
    - เข้า [n8n.io](https://app.n8n.cloud/register) เพื่อสมัครสร้างบัญชีผู้ใช้ (ดูวิธีทำโดยละเอียด)
    - ยืนยันอีเมลถ้ามี
    - ล็อกอินและสร้างเวิร์กโฟลว์ใหม่
- ตรวจสอบความสำเร็จ: เห็นผืนงานว่างและแผงซ้ายพร้อมเพิ่มโหนด
![Alt: หน้าจอ n8n เวิร์กโฟลว์ใหม่](../../images/lesson-02/step-01-new-workflow.png)
คำอธิบาย: ถ่ายภาพหน้าจอผืนงานว่างของ n8n พร้อมใช้งาน

Step 2: Explore the editor layout
- Why: Knowing the layout helps you work faster.
- Do this:
    - Identify: Canvas, Nodes panel, Properties panel, Top bar (Execute, Save, Activate).
    - Hover a node to see its description.
- Success check: You can point to each area when asked.
![Alt: n8n editor UI areas highlighted](../../images/lesson-02/step-02-editor-layout.png)
Description: Capture the main areas of the editor with labels.

[TH] ขั้นตอนที่ 2: สำรวจหน้าจอเครื่องมือ
- ทำไม: รู้โครงสร้างช่วยทำงานเร็วขึ้น
- วิธีทำ:
    - ดูตำแหน่ง: Canvas, แถบโหนด, แถบคุณสมบัติ, แถบด้านบน (Execute, Save, Activate)
    - ชี้เมาส์ที่โหนดเพื่อดูคำอธิบาย
- ตรวจสอบความสำเร็จ: สามารถชี้ตำแหน่งส่วนต่าง ๆ ได้
![Alt: มุมมองส่วนต่าง ๆ ของเครื่องมือ n8n](../../images/lesson-02/step-02-editor-layout.png)
คำอธิบาย: ถ่ายภาพไฮไลต์ส่วนสำคัญของหน้าจอ

Step 3: Add a "Webhook" trigger
- Why: Allow external systems (or Postman) to call your workflow.
- Do this:
    - Add a "Webhook" node.
    - Set HTTP Method to "POST".
    - Copy the "Test URL".
- Success check: You see a Test URL on the "Webhook" node.
![Alt: Webhook node with Test URL visible](../../images/lesson-02/step-03-webhook-url.png)
Description: Capture the "Webhook" node on the canvas with the Test URL highlighted.

[TH] ขั้นตอนที่ 3: เพิ่มโหนด "Webhook"
- ทำไม: เปิดให้ระบบภายนอก (หรือ Postman) เรียกเวิร์กโฟลว์ได้
- วิธีทำ:
    - เพิ่มโหนด "Webhook"
    - ตั้งค่า HTTP Method เป็น "POST"
    - คัดลอก "Test URL"
- ตรวจสอบความสำเร็จ: เห็น Test URL บนโหนด "Webhook"
![Alt: โหนด Webhook แสดง Test URL](../../images/lesson-02/step-03-webhook-url.png)
คำอธิบาย: ถ่ายภาพโหนด "Webhook" โดยไฮไลต์ตำแหน่ง Test URL

Step 3.1: Test the Webhook with sample JSON
- Why: Confirm your workflow receives finance‑style payloads.
- Do this:
    - Use Postman or curl to POST JSON to the Test URL.
    - Body: use docs/snippets/lesson-02/sample-webhook-payload.json
- Success check: "Webhook" node shows one incoming execution with the same fields.
![Alt: Webhook execution showing received JSON payload](../../images/lesson-02/step-03b-webhook-test.png)
Description: Show Execution panel with the received JSON payload.

[TH] ขั้นตอนที่ 3.1: ทดสอบ Webhook ด้วย JSON ตัวอย่าง
- ทำไม: ยืนยันว่าเวิร์กโฟลว์รับ payload รูปแบบงานการเงินได้
- วิธีทำ:
    - ใช้ Postman หรือ curl เพื่อ POST JSON ไปยัง Test URL
    - เนื้อหา: ใช้ไฟล์ docs/snippets/lesson-02/sample-webhook-payload.json
- ตรวจสอบความสำเร็จ: โหนด "Webhook" แสดง Execution ที่ได้รับข้อมูลตามฟิลด์ในไฟล์
![Alt: Execution ของ Webhook แสดง JSON ที่รับมา](../../images/lesson-02/step-03b-webhook-test.png)
คำอธิบาย: แสดงหน้า Execution ที่เห็น JSON ที่รับมา

Step 4: Validate input with "IF"
- Why: Only proceed when required fields exist.
- Do this:
    - Add an "IF" node after "Webhook".
    - Condition: json.patientId exists AND json.amount > 0.
- Success check: With valid payload, the true branch is taken.
![Alt: IF node true branch when patientId and amount are valid](../../images/lesson-02/step-04-if-validate.png)
Description: Capture the IF condition and a green (true) branch.

[TH] ขั้นตอนที่ 4: ตรวจสอบข้อมูลด้วย "IF"
- ทำไม: ไปต่อเฉพาะเมื่อมีข้อมูลจำเป็น
- วิธีทำ:
    - เพิ่มโหนด "IF" ต่อจาก "Webhook"
    - ตั้งค่าเงื่อนไข: json.patientId มีอยู่ และ json.amount > 0
- ตรวจสอบความสำเร็จ: เมื่อ payload ถูกต้อง แขนง true จะทำงาน
![Alt: โหนด IF แขนง true เมื่อข้อมูลถูกต้อง](../../images/lesson-02/step-04-if-validate.png)
คำอธิบาย: ถ่ายภาพเงื่อนไขและแขนง true

Step 5: Format response with "Set"
- Why: Create a friendly confirmation message.
- Do this:
    - On the true branch, add a "Set" node.
    - Add fields: status = "received", message = "Hello Finance".
- Success check: The "Set" node output shows the fields you added.
![Alt: Set node showing formatted output fields](../../images/lesson-02/step-05-set-output.png)
Description: Capture the Set node output panel.

[TH] ขั้นตอนที่ 5: จัดรูปแบบผลลัพธ์ด้วย "Set"
- ทำไม: สร้างข้อความยืนยันที่อ่านง่าย
- วิธีทำ:
    - ในแขนง true เพิ่มโหนด "Set"
    - เพิ่มฟิลด์: status = "received", message = "Hello Finance"
- ตรวจสอบความสำเร็จ: โหนด "Set" แสดงฟิลด์ที่เพิ่มไว้
![Alt: โหนด Set แสดงฟิลด์ผลลัพธ์](../../images/lesson-02/step-05-set-output.png)
คำอธิบาย: ถ่ายภาพผลลัพธ์ของโหนด Set

Step 6: Return an HTTP response
- Why: Make the workflow reply to the caller.
- Do this:
    - Add an "HTTP Response" node after the true branch.
    - Status Code: 200. Body: Use data from "Set".
- Success check: Caller receives 200 and the JSON message.
![Alt: HTTP Response node configured with 200 status](../../images/lesson-02/step-06-http-response.png)
Description: Show HTTP Response node config with 200 and JSON body mapping.

[TH] ขั้นตอนที่ 6: ส่งคำตอบกลับด้วย "HTTP Response"
- ทำไม: ให้เวิร์กโฟลว์ตอบกลับผู้เรียก
- วิธีทำ:
    - เพิ่มโหนด "HTTP Response" หลังแขนง true
    - Status Code: 200 และ Body: ใช้ข้อมูลจาก "Set"
- ตรวจสอบความสำเร็จ: ผู้เรียกได้รับสถานะ 200 และ JSON ตามที่ตั้งค่า
![Alt: โหนด HTTP Response ตั้งค่า 200 และ Body เป็น JSON](../../images/lesson-02/step-06-http-response.png)
คำอธิบาย: แสดงหน้าต่างตั้งค่าโหนด HTTP Response

Troubleshooting
- Webhook test vs production URL: Use Test URL while testing, Production URL after activation.
- 4xx/5xx from HTTP Response: Check body mapping and headers.
[TH] แก้ปัญหา
- ความต่างระหว่าง Test URL และ Production URL: ใช้ Test ระหว่างทดสอบ และใช้ Production หลังเปิดใช้งาน
- สถานะ 4xx/5xx: ตรวจสอบการแมปข้อมูลและ headers

Next steps
- Continue to Lesson 03 to connect spreadsheets, APIs, and add logic.
[TH] ขั้นต่อไป
- ไปบทเรียน 03 เพื่อเชื่อมต่อสเปรดชีต, API และเพิ่มตรรกะ
