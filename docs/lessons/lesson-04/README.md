# Lesson 04 — Activate, Monitor, and Handle Errors

What you will build
- Enable production execution, add monitoring, and handle common errors for finance workflows.
[TH] สิ่งที่จะสร้าง
- เปิดใช้งานสำหรับงานจริง เพิ่มการติดตาม และจัดการข้อผิดพลาดสำหรับเวิร์กโฟลว์การเงิน

Prerequisites
- Completed Lessons 02 and 03
[TH] ข้อกำหนดก่อนเริ่ม
- ทำบทเรียน 02 และ 03 แล้ว

Time required
- ~60 minutes
[TH] เวลาที่ใช้
- ~60 นาที

Outcome
- You can activate workflows, switch Webhook to Production URL, inspect executions, and add basic retries/alerts.
[TH] ผลลัพธ์
- เปิดใช้งานเวิร์กโฟลว์ เปลี่ยน Webhook ไปใช้ Production URL ดู Execution และเพิ่มการ retry/แจ้งเตือนพื้นฐานได้

Steps

Step 1: Activate the workflow
- Why: Make it run automatically when requests arrive.
- Do this:
    - Open your workflow.
    - Click Activate. Confirm any prompts.
    - On the "Webhook" node, switch to the "Production URL".
- Success check: Status shows Active and you can access the Production URL.
![Alt: Workflow activation with Production URL highlighted](../../images/lesson-04/step-01-activate.png)
Description: Show Activate toggle on and Production URL visible.

[TH] ขั้นตอนที่ 1: เปิดใช้งานเวิร์กโฟลว์
- ทำไม: ให้เวิร์กโฟลว์ทำงานอัตโนมัติเมื่อมีคำขอเข้า
- วิธีทำ:
    - เปิดเวิร์กโฟลว์ของคุณ
    - คลิก Activate และยืนยัน
    - ที่โหนด "Webhook" เปลี่ยนไปใช้ "Production URL"
- ตรวจสอบความสำเร็จ: สถานะแสดง Active และเห็น Production URL
![Alt: เปิดใช้งานเวิร์กโฟลว์พร้อม Production URL](../../images/lesson-04/step-01-activate.png)
คำอธิบาย: แสดงปุ่ม Activate เปิดอยู่ และเห็น Production URL

Step 2: Inspect Executions
- Why: Troubleshoot and verify real runs.
- Do this:
    - Open Executions view from the top bar.
    - Filter by status (Success/Failed).
    - Click into a failed run to see node‑level data.
- Success check: You can identify which node failed and why.
![Alt: Executions view showing a failed and a successful run](../../images/lesson-04/step-02-executions.png)
Description: Show Executions list and one expanded run.

[TH] ขั้นตอนที่ 2: ตรวจสอบ Executions
- ทำไม: แก้ปัญหาและตรวจสอบการทำงานจริง
- วิธีทำ:
    - เปิดหน้าต่าง Executions จากแถบด้านบน
    - กรองตามสถานะ (Success/Failed)
    - คลิกที่รายการที่ล้มเหลวเพื่อดูข้อมูลระดับโหนด
- ตรวจสอบความสำเร็จ: ระบุได้ว่าโหนดใดล้มเหลวและสาเหตุคืออะไร
![Alt: มุมมอง Executions แสดงงานสำเร็จและล้มเหลว](../../images/lesson-04/step-02-executions.png)
คำอธิบาย: แสดงรายการ Executions และขยายดูหนึ่งรายการ

Step 3: Add simple retries with "HTTP Request"
- Why: Temporary API issues can resolve on retry.
- Do this:
    - In "HTTP Request" node, enable retry on failure (Max attempts 3, Backoff e.g., exponential).
    - Optionally add "Wait" between retries.
- Success check: Intermittent failures recover on retry.
![Alt: HTTP Request retry settings configured](../../images/lesson-04/step-03-retry.png)
Description: Show HTTP Request node settings with retry enabled.

[TH] ขั้นตอนที่ 3: เพิ่มการลองใหม่ (retry) แบบง่าย
- ทำไม: ปัญหา API ชั่วคราวมักหายเมื่อลองใหม่
- วิธีทำ:
    - ในโหนด "HTTP Request" เปิดการ retry เมื่อเกิดข้อผิดพลาด (เช่น 3 ครั้ง แบบ exponential)
    - ตัวเลือก: เพิ่มโหนด "Wait" ระหว่างการลองใหม่
- ตรวจสอบความสำเร็จ: ความล้มเหลวชั่วคราวกลับมาสำเร็จได้เมื่อ retry
![Alt: ตั้งค่า retry ในโหนด HTTP Request](../../images/lesson-04/step-03-retry.png)
คำอธิบาย: แสดงการตั้งค่า retry ของ HTTP Request

Step 4: Notify on failures (optional)
- Why: Keep the team informed.
- Do this:
    - Add an "IF" node after critical steps to detect non‑200 status.
    - On false branch, add a notification node (e.g., Email via "SMTP" or chat via "Slack").
- Success check: A test failure triggers a message.
![Alt: Notification branch sending email on failure](../../images/lesson-04/step-04-notify.png)
Description: Show IF false branch to an email/slack node with sample message.

[TH] ขั้นตอนที่ 4: แจ้งเตือนเมื่อเกิดข้อผิดพลาด (ตัวเลือก)
- ทำไม: ให้ทีมรับรู้ทันที
- วิธีทำ:
    - เพิ่มโหนด "IF" หลังขั้นตอนสำคัญเพื่อตรวจจับสถานะที่ไม่ใช่ 200
    - ในแขนง false เพิ่มโหนดแจ้งเตือน (อีเมลผ่าน "SMTP" หรือแชทผ่าน "Slack")
- ตรวจสอบความสำเร็จ: เมื่อจำลองความผิดพลาด ระบบส่งข้อความแจ้งเตือน
![Alt: แขนงแจ้งเตือนเมื่อเกิดข้อผิดพลาด](../../images/lesson-04/step-04-notify.png)
คำอธิบาย: แสดงแขนง false ต่อกับโหนดอีเมล/แชทพร้อมข้อความตัวอย่าง

Troubleshooting
- No executions: Ensure workflow is Active and using Production URL.
- Too many retries: Cap attempts and add delay.
[TH] แก้ปัญหา
- ไม่มีการรัน: ตรวจสอบว่า Active แล้วและใช้ Production URL
- retry มากเกินไป: จำกัดจำนวนครั้งและเพิ่มการหน่วงเวลา

Next steps
- Review Lesson 05 for privacy/security guidelines before going live.
[TH] ขั้นต่อไป
- อ่านบทเรียน 05 เรื่องความเป็นส่วนตัว/ความปลอดภัย ก่อนใช้งานจริง
