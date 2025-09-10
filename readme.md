# Welcome to Workshop EP3

Boost your QA Workflow with GitHub Copilot

## Objective

- เชื่อมต่อกับ Jira & Figma Mcp server
- สร้าง test case จาก jira Epic/Story ด้วย Copilot
- สร้าง test case จาก Confluence ด้วย Copilot
- สร้าง test case จาก UI Figma ด้วย Copilot


## Figma

<https://www.figma.com/design/pkCT6YDfcnEVOOTS2HIDOg/POC-FIGMA-MCP?node-id=0-1&p=f&t=V7WJzJD6AibkXFXE-0>

# 01-Preparation

## ตัวอย่างคำสั่งเบื้องต้น
1 จาก readme.md ช่วยสร้าง jira confluence ให้หน่อย
2 จาก jira confluence ช่วยสร้าง Epic ให้หน่อย
3 จาก Epic, jira confluence และ <figma link> สร้าง story ให้หน่อย
4 จาก jira story <story-no> สร้าง subtask ให้หน่อย
5 จากไฟล์ KrungThai_TQA_TestCase_Template_Structure อยากให้สร้าง csv จาก jira story <story-no> ให้หน่อย

---

### Confluence (Spec/Requirement)

**ชื่อหน้า:** Dashboard

**วัตถุประสงค์:**  

- เพื่อให้ผู้ใช้งานสามารถดูข้อมูลสรุปภาพรวมของระบบได้อย่างรวดเร็ว
- รองรับการค้นหาและกรองข้อมูลตามเงื่อนไขที่ต้องการ
- สามารถเข้าถึงรายละเอียดของแต่ละรายการได้สะดวก

**รายละเอียดฟีเจอร์:**  

- Header: แสดงชื่อหน้า, ปุ่ม Refresh, ปุ่ม Export ข้อมูล
- Search Bar: ช่องกรอกคำค้นหา, Dropdown เลือกประเภทข้อมูล, ปุ่มค้นหา, ปุ่ม Reset
- Data Table:
  - แสดงข้อมูลหลัก เช่น ชื่อ, สถานะ, วันที่สร้าง, ผู้รับผิดชอบ
  - รองรับการ sort, filter, pagination
  - มีปุ่มดูรายละเอียด (View Detail) ในแต่ละแถว
- Loading/Error State:
  - แสดง progress bar หรือ spinner ระหว่างโหลดข้อมูล
  - แสดงข้อความ error เมื่อดึงข้อมูลไม่สำเร็จ
- Empty State:
  - แสดงข้อความหรือภาพประกอบเมื่อไม่มีข้อมูลแสดงผล

**Flow การใช้งาน:**  

1. ผู้ใช้เข้าหน้า Dashboard
2. ระบบโหลดข้อมูลและแสดงในตาราง
3. ผู้ใช้กรอกคำค้นหา/เลือก filter แล้วกดค้นหา
4. ระบบแสดงผลลัพธ์ที่ตรงกับเงื่อนไข
5. ผู้ใช้กดปุ่มดูรายละเอียดเพื่อเข้าหน้ารายละเอียด
6. หากเกิด error หรือไม่มีข้อมูล ระบบแสดงข้อความแจ้งเตือน

**Validation/เงื่อนไข:**  

- ช่องค้นหาต้องไม่รับอักขระพิเศษที่ไม่รองรับ
- หากค้นหาแล้วไม่พบข้อมูล ต้องแสดงข้อความ “ไม่พบข้อมูลที่ต้องการ”
- ปุ่ม Export ต้องใช้งานได้เฉพาะกรณีมีข้อมูลในตาราง

---

### Epic (Jira)

**ชื่อ Epic:** พัฒนา Dashboard UI สำหรับสรุปข้อมูลระบบ

**คำอธิบาย:**  

- พัฒนา Dashboard UI ตามแบบ Figma node-id=12-488
- รองรับการค้นหา กรองข้อมูล และดูรายละเอียด
- เชื่อมต่อ API สำหรับดึงข้อมูลจริง
- จัดการสถานะ loading, error, empty state
- รองรับการ export ข้อมูล
- ทดสอบการใช้งานและตรวจสอบความถูกต้องตาม requirement

**Business Value:**  

- เพิ่มประสิทธิภาพการทำงานของผู้ใช้
- ลดเวลาในการค้นหาข้อมูลสำคัญ
- รองรับการขยายฟีเจอร์ในอนาคต

**Deliverables:**  

- หน้า Dashboard UI พร้อมใช้งาน
- เอกสารคู่มือการใช้งานเบื้องต้น
- Test case ครบถ้วน

---

### Story (Jira)

**ชื่อ Story:** พัฒนา Dashboard UI และฟีเจอร์ค้นหา

**Acceptance Criteria (Given-When-Then):**

1.

- Given: ผู้ใช้เข้าสู่หน้า Dashboard
- When: ระบบโหลดข้อมูลสำเร็จ
- Then: ผู้ใช้จะเห็นข้อมูลแสดงในตาราง

2.

- Given: ผู้ใช้กรอกคำค้นหาและกดปุ่มค้นหา
- When: ระบบประมวลผลคำค้นหา
- Then: ระบบแสดงผลลัพธ์ที่ตรงกับเงื่อนไขในตาราง

3.

- Given: ไม่มีข้อมูลตรงกับเงื่อนไขที่ค้นหา
- When: ระบบค้นหาข้อมูลเสร็จสิ้น
- Then: ระบบแสดงข้อความ “ไม่พบข้อมูลที่ต้องการ”

4.

- Given: มีข้อมูลแสดงในตาราง
- When: ผู้ใช้กดปุ่มดูรายละเอียดในแต่ละแถว
- Then: ระบบแสดงหน้ารายละเอียดของรายการนั้น

5.

- Given: ระบบกำลังดึงข้อมูลจาก API
- When: ข้อมูลยังไม่โหลดเสร็จ
- Then: ระบบแสดง loading indicator

6.

- Given: เกิดข้อผิดพลาดขณะโหลดข้อมูล
- When: ระบบไม่สามารถดึงข้อมูลได้
- Then: ระบบแสดงข้อความ error

7.

- Given: มีข้อมูลในตาราง
- When: ผู้ใช้กดปุ่ม Export
- Then: ระบบดาวน์โหลดไฟล์ข้อมูลสำเร็จ
