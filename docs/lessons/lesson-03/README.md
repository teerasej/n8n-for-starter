# Lesson 03 — Core Nodes and Integrations (Finance Examples)

What you will build
- A finance‑oriented integration flow: read pending reimbursements from a spreadsheet, validate amounts, call a hospital finance API, and log results.
[TH] สิ่งที่จะสร้าง
- เวิร์กโฟลว์เชื่อมต่อข้อมูล: อ่านคำขอเบิกคืนจากสเปรดชีต ตรวจสอบยอด เรียก API การเงินโรงพยาบาล และบันทึกผลลัพธ์

Prerequisites
- Completed Lesson 02
- Access to a sample Google Sheet or CSV (provided) and a mock API endpoint
[TH] ข้อกำหนดก่อนเริ่ม
- ทำบทเรียน 02 แล้ว
- เข้าถึง Google Sheet หรือไฟล์ CSV ตัวอย่าง (มีให้) และปลายทาง API mock

Time required
- ~120 minutes (core focus)
[TH] เวลาที่ใช้
- ~120 นาที (หัวข้อหลัก)

Outcome
- You can use core nodes ("Spreadsheet File", "IF", "Set", "HTTP Request", "Merge") to orchestrate a real‑world flow.
[TH] ผลลัพธ์
- ใช้โหนดหลัก ("Spreadsheet File", "IF", "Set", "HTTP Request", "Merge") เพื่อควบคุมเวิร์กโฟลว์จริงได้

Steps

Step 1: Import reimbursement data
- Why: We need input data to process.
- Do this:
    - Add a "Spreadsheet File" node (or "Google Sheets" if preferred).
    - Load sample file with columns: requestId, patientId, amount, description.
- Success check: Node output shows rows with those fields.
![Alt: Spreadsheet File node preview with columns](../../images/lesson-03/step-01-spreadsheet-preview.png)
Description: Show rows preview from the spreadsheet in n8n.

[TH] ขั้นตอนที่ 1: นำเข้าข้อมูลเบิกคืน
- ทำไม: ต้องมีข้อมูลตั้งต้นเพื่อประมวลผล
- วิธีทำ:
    - เพิ่มโหนด "Spreadsheet File" (หรือ "Google Sheets")
    - โหลดไฟล์ตัวอย่างที่มีคอลัมน์: requestId, patientId, amount, description
- ตรวจสอบความสำเร็จ: เห็นข้อมูลแถวต่าง ๆ พร้อมคอลัมน์ตามที่กำหนด
![Alt: พรีวิวข้อมูลจาก Spreadsheet File ใน n8n](../../images/lesson-03/step-01-spreadsheet-preview.png)
คำอธิบาย: แสดงตัวอย่างข้อมูลจากสเปรดชีตใน n8n

Step 2: Validate and branch with "IF"
- Why: Filter out invalid or suspicious entries.
- Do this:
    - Add an "IF" node. Conditions: amount > 0 AND patientId exists.
    - Optional: Add a high‑amount threshold branch (e.g., amount >= 5000) for manual review.
- Success check: Valid rows flow to the true branch; invalid to false.
![Alt: IF node branching valid vs invalid rows](../../images/lesson-03/step-02-if-branch.png)
Description: Show IF conditions and both branches.

[TH] ขั้นตอนที่ 2: ตรวจสอบและแยกแขนงด้วย "IF"
- ทำไม: ตัดข้อมูลที่ไม่ถูกต้องหรือเสี่ยง
- วิธีทำ:
    - เพิ่มโหนด "IF" ตั้งเงื่อนไข: amount > 0 และมี patientId
    - ตัวเลือก: เพิ่มเงื่อนไขยอดสูง (เช่น amount >= 5000) เพื่อให้ตรวจสอบด้วยมือ
- ตรวจสอบความสำเร็จ: แถวที่ถูกต้องไปแขนง true ส่วนที่ไม่ถูกต้องไปแขนง false
![Alt: โหนด IF แยกข้อมูลถูกต้อง/ผิดพลาด](../../images/lesson-03/step-02-if-branch.png)
คำอธิบาย: แสดงเงื่อนไข IF และทั้งสองแขนง

Step 3: Call finance API with "HTTP Request"
- Why: Push approved items to the finance system.
- Do this:
    - Add an "HTTP Request" node on the true branch.
    - Method: "POST", URL: <mock endpoint>.
    - Send JSON: { requestId, patientId, amount } from previous item.
- Success check: Node shows 200 OK and an acknowledgment ID.
![Alt: HTTP Request node successful run with 200 status](../../images/lesson-03/step-03-http-200.png)
Description: Show execution with Status 200 and response body.

[TH] ขั้นตอนที่ 3: เรียก Finance API ด้วย "HTTP Request"
- ทำไม: ส่งรายการที่อนุมัติไปยังระบบการเงิน
- วิธีทำ:
    - เพิ่มโหนด "HTTP Request" ในแขนง true
    - Method: "POST", URL: <ปลายทาง mock>
    - ส่ง JSON: { requestId, patientId, amount } จากรายการก่อนหน้า
- ตรวจสอบความสำเร็จ: แสดงผล 200 OK และมีรหัสตอบรับ
![Alt: โหนด HTTP Request แสดงผลลัพธ์ 200](../../images/lesson-03/step-03-http-200.png)
คำอธิบาย: แสดงหน้าจอ Execution สถานะ 200 และ response

Step 4: Combine results with "Merge"
- Why: Create a unified list of processed and skipped items.
- Do this:
    - Add a "Merge" node to combine true (processed) and false (skipped) branches.
    - Mode: Keep Key Matches or Append.
- Success check: Output shows both categories with a status field.
![Alt: Merge node output combining two branches](../../images/lesson-03/step-04-merge-output.png)
Description: Show Merge node config and output preview.

[TH] ขั้นตอนที่ 4: รวมผลลัพธ์ด้วย "Merge"
- ทำไม: รวมรายการที่ประมวลผลและข้ามไว้เป็นชุดเดียว
- วิธีทำ:
    - เพิ่มโหนด "Merge" เพื่อรวมแขนง true (processed) และ false (skipped)
    - Mode: เลือก Keep Key Matches หรือ Append
- ตรวจสอบความสำเร็จ: เห็นผลลัพธ์รวมทั้งสองประเภท พร้อมฟิลด์สถานะ
![Alt: โหนด Merge รวมผลสองแขนง](../../images/lesson-03/step-04-merge-output.png)
คำอธิบาย: แสดงการตั้งค่าและตัวอย่างผลลัพธ์ของ Merge

Step 5: Create a summary with "Set"
- Why: Make a clear report for the team.
- Do this:
    - Add a "Set" node to add fields: processedCount, skippedCount.
    - Optionally, format a human‑friendly message.
- Success check: The output shows counts matching your data.
![Alt: Set node showing summary counts](../../images/lesson-03/step-05-set-summary.png)
Description: Show Set node output with counts.

[TH] ขั้นตอนที่ 5: สร้างสรุปผลด้วย "Set"
- ทำไม: รายงานผลให้ทีมอ่านง่าย
- วิธีทำ:
    - เพิ่มโหนด "Set" เพื่อเพิ่มฟิลด์: processedCount, skippedCount
    - ทางเลือก: จัดข้อความให้อ่านง่าย
- ตรวจสอบความสำเร็จ: จำนวนตรงกับข้อมูลที่ประมวลผล
![Alt: โหนด Set แสดงจำนวนสรุป](../../images/lesson-03/step-05-set-summary.png)
คำอธิบาย: แสดงผลลัพธ์ของ Set ที่มีจำนวนรวม

Troubleshooting
- API errors: Check URL, method, and JSON mapping. Retry with a single row.
- Spreadsheet parsing: Ensure headers match exactly.
[TH] แก้ปัญหา
- ข้อผิดพลาดจาก API: ตรวจสอบ URL, method และการแมป JSON ลองด้วยแถวเดียวก่อน
- อ่านสเปรดชีตไม่ได้: ตรวจสอบชื่อคอลัมน์ให้ตรงกัน

Next steps
- Proceed to Lesson 04 to activate and monitor this workflow in production.
[TH] ขั้นต่อไป
- ไปบทเรียน 04 เพื่อเปิดใช้งานและติดตามเวิร์กโฟลว์นี้ในงานจริง
