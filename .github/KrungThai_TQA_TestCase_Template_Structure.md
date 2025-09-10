# โครงสร้าง Krungthai Bank TQA Test Case Template

## ภาพรวมของ Template

ไฟล์ Excel Template นี้เป็นมาตรฐานสำหรับการสร้าง Test Case ของธนาคารกรุงไทย ประกอบด้วย 2 Sheet หลัก:

1. **LOV (List of Values)** - สำหรับเก็บค่าที่ใช้ในการเลือก (Drop-down values)
2. **TC_Draft** - สำหรับเขียน Test Case ตัวจริง

---

## Sheet 1: LOV (List of Values)

### วัตถุประสงค์
Sheet นี้ใช้สำหรับกำหนดค่าที่สามารถเลือกได้ในแต่ละฟิลด์ของ Test Case เพื่อให้เกิดความสม่ำเสมอในการตั้งค่า

### โครงสร้างคอลัมน์

| คอลัมน์ | ชื่อฟิลด์ | คำอธิบาย | ค่าที่เป็นไปได้ |
|---------|-----------|----------|-----------------|
| A | Priority | ระดับความสำคัญของ Test Case | High, Normal, Low |
| B | Positive/Negative | ประเภทของการทดสอบ | Positive, Negative |
| C | Regression Flag | การใช้ในการทดสอบย้อนหลัง | Yes, No |
| D | Testing Type | ประเภทการทดสอบ | GUI, API, SQL, Batch |
| E | Automation | สถานะการทำ Automation | Manual, Automatable, Automated |
| F | Status | สถานะของ Test Case | Draft, Deprecated, Approved |

### รายละเอียดการจัดรูปแบบ (Styling)

#### Header Row (แถวที่ 1)
- **สีพื้นหลัง**: #B4C7E7 (สีฟ้าอ่อน)
- **ฟอนต์**: Bold, ขนาด 11pt
- **เส้นขอบ**: มีเส้นขอบรอบทุกเซลล์ (สีดำ, แบบต่อเนื่อง)

#### Data Rows (แถวที่ 2-5)
- **ฟอนต์**: ปกติ ขนาด 11pt (คอลัมน์ A-E), ขนาด 12pt (คอลัมน์ F)
- **เส้นขอบ**: มีเส้นขอบรอบทุกเซลล์
- **สีฟอนต์ คอลัมน์ F**: #000000 (สีดำ)

---

## Sheet 2: TC_Draft (Test Case Draft)

### วัตถุประสงค์
Sheet หลักสำหรับเขียนรายละเอียด Test Case ทั้งหมด รวมถึงขั้นตอนการทดสอบ ข้อมูลที่ใช้ และผลลัพธ์ที่คาดหวัง

### โครงสร้างคอลัมน์ (A-V)

#### กลุมข้อมูลพื้นฐาน Test Case
| คอลัมน์ | ชื่อฟิลด์ | คำอธิบาย | ตัวอย่าง |
|---------|-----------|----------|---------|
| A | Name | ชื่อ Test Case (รหัส + คำอธิบาย) **เขียนเป็นภาษาอังกฤษเท่านั้น** | BU_Pre-Registered_EN_TC001: Verify that the Super user is successful in bulk uploading the pre-registered list |
| B | Objective | วัตถุประสงค์ของการทดสอบ **เขียนเป็นภาษาอังกฤษเท่านั้น** | Verify that the Super user is successful in bulk uploading the pre-registered list |
| C | Precondition | เงื่อนไขเริ่มต้นก่อนทดสอบ **เขียนเป็นภาษาอังกฤษเท่านั้น** | Within a day, the data in the file must not be the same as a previous upload. Change the data in the first row and column c (batch no.) |

#### กลุ่มขั้นตอนการทดสอบ
| คอลัมน์ | ชื่อฟิลด์ | คำอธิบาย | ตัวอย่าง |
|---------|-----------|----------|---------|
| D | Test Script (Step-by-Step) - Step | ขั้นตอนการทดสอบแบบละเอียด **เขียนเป็นภาษาอังกฤษเท่านั้น** | #Super user<br>1. Call API Upload (pre-registered-list/files)<br>2. Call API Check upload status (bulkPreRegId)<br>3. Call API Review & Confirm (verification)<br>4. Call API Pre Get OTP (pre-confirmation)<br>5. Call API Get OTP (mfa/challenge)<br>6. Call API Send Authen (mfa/authentication)<br>7. Call API Sumit Txn (confirmation)<br>8. Call API Get Txn Status<br>9. Call API Get Txn Summary<br>10. Call API Get Txn Details<br>11. Call API Get Tracking Progress (activity-log)<br>12. Call API Get PreRegist Lists |
| E | Test Script (Step-by-Step) - Test Data | ข้อมูลที่ใช้ในการทดสอบ | BU_PreRegist_TC001_2Payee_Add.csv |
| F | Test Script (Step-by-Step) - Expected Result | ผลลัพธ์ที่คาดหวัง **เขียนเป็นภาษาอังกฤษเท่านั้น** | 1. Verify All API - HTTP status 200<br>2. Verify Transacton Status (Step#8) - Successful<br>3. Verify Transacton Summary (Step#9)<br>4. Verify Transacton Details (Step#10)<br>5. Verify Tracking Progress (Step#11)<br>6. Verify PreRegist Lists (Step#12) |
| G | Post Step | ขั้นตอนหลังการทดสอบ **เขียนเป็นภาษาอังกฤษเท่านั้น** | The Super User upload file to remove pre-registed lists. |

#### กลุ่มข้อมูลการจัดการ
| คอลัมน์ | ชื่อฟิลด์ | คำอธิบาย | ตัวอย่าง |
|---------|-----------|----------|---------|
| H | Component | ส่วนงานที่เกี่ยวข้อง | Krungthai Biz |
| I | Sprint | Sprint ที่เกี่ยวข้อง | MVP1 Drop1 |
| J | Folder | โฟลเดอร์ที่เก็บ Test Case | /BU_Pre-Registered/Bulk transaction |
| K | Coverage (Issues) | Story หรือ Issue ที่เกี่ยวข้อง | T10AUTO-3, T10AUTO-9 |

#### กลุ่มคุณสมบัติ Test Case
| คอลัมน์ | ชื่อฟิลด์ | คำอธิบาย | ค่าที่เป็นไปได้ (จาก LOV) |
|---------|-----------|----------|-------------------------|
| L | Priority | ระดับความสำคัญ | High, Normal, Low |
| M | Positive/Negative | ประเภทการทดสอบ | Positive, Negative |
| N | Regression Flag | การใช้ในการทดสอบย้อนหลัง | Yes, No |
| O | Testing Type | ประเภทการทดสอบ | GUI, API, SQL, Batch |
| P | Automation | สถานะ Automation | Manual, Automatable, Automated |

#### กลุ่มข้อมูลการบริหารจัดการ
| คอลัมน์ | ชื่อฟิลด์ | คำอธิบาย | รูปแบบ |
|---------|-----------|----------|---------|
| Q | Estimated Time | เวลาที่คาดว่าใช้ในการทดสอบ | HH:MM (เช่น 00:02) |
| R | Owner | ผู้เป็นเจ้าของ Test Case | User ID (เช่น 5c22f881a217aa69bce51e01) |
| S | Reviewed By | ผู้ตรวจสอบ | User ID |
| T | Date of Review | วันที่ตรวจสอบ | MM-DD-YY (เช่น 06-13-25) |
| U | Status | สถานะปัจจุบัน | Draft, Deprecated, Approved |
| V | Labels | ป้ายกำกับ | รหัสภาษา,ระดับ (เช่น 1L,EN) |

### รายละเอียดการจัดรูปแบบ (Styling)

#### Header Row (แถวที่ 1)
- **สีพื้นหลัง**: 
  - คอลัมน์ A,B,C,D,E,F,H,J,K,L,Q,R,U,V: #C5E0B4 (สีเขียวอ่อน)
  - คอลัมน์ G,I,M,N,O,P,S,T: #BDD7EE (สีฟ้าอ่อน)
- **ฟอนต์**: Bold, ขนาด 11pt
- **เส้นขอบ**: มีเส้นขอบรอบทุกเซลล์ (สีดำ, แบบต่อเนื่อง)

#### Data Rows (แถวที่ 2 เป็นต้นไป)
- **ฟอนต์**: ปกติ ขนาด 11pt
- **เส้นขอบ**: แถวที่ 2 มีเส้นขอบ, แถวที่ 3-4 ไม่มีเส้นขอบ

#### หมายเหตุพิเศษ (แถวที่ 4)
- คอลัมน์ J: "ระบุ Folder Path"
- คอลัมน์ K: "ควร Link เฉพาะ Story เท่านั้น เนื่องจากจะมีผลกับการออก Reports"

---

## แนวทางการใช้งาน Template

### 1. การเตรียมข้อมูล
- ศึกษาค่าต่างๆ ใน LOV Sheet ให้เข้าใจก่อน
- เตรียมข้อมูล Test Case ให้ครบถ้วนตามคอลัมน์ที่กำหนด

### 2. การเขียน Test Case
- เริ่มต้นจากคอลัมน์ A (Name) โดยใช้รูปแบบ: `[Component]_[Feature]_[Language]_TC[Number]: [Description]`
- เขียน Objective ให้ชัดเจนว่าต้องการทดสอบอะไร **ใช้ภาษาอังกฤษเท่านั้น**
- ระบุ Precondition หากมีเงื่อนไขพิเศษ **ใช้ภาษาอังกฤษเท่านั้น**
- เขียนขั้นตอนการทดสอบอย่างละเอียดในคอลัมน์ D **ใช้ภาษาอังกฤษเท่านั้น**
- ระบุข้อมูลทดสอบและผลลัพธ์ที่คาดหวัง **ใช้ภาษาอังกฤษเท่านั้น**

### 3. การกำหนดคุณสมบัติ
- เลือกค่าจาก LOV Sheet สำหรับคอลัมน์ L,M,N,O,P,U
- กำหนด Priority ตามความสำคัญ
- ระบุ Testing Type ตามลักษณะการทดสอบ
- กำหนด Automation status ตามความเป็นไปได้

### 4. การบริหารจัดการ
- ระบุ Owner และ Reviewer
- กำหนด Estimated Time ที่สมเหตุสมผล
- Update Status ตามความคืบหน้า
- ใส่ Labels เพื่อการจัดหมวดหมู่

---

## ข้อแนะนำสำหรับ AI/Copilot

เมื่อสร้าง Test Case ใหม่ควรคำนึงถึง:

1. **ความสม่ำเสมอ**: ใช้ค่าจาก LOV Sheet เท่านั้น
2. **ความครบถ้วน**: กรอกข้อมูลให้ครบทุกคอลัมน์ที่จำเป็น
3. **ความชัดเจน**: เขียนขั้นตอนการทดสอบให้เข้าใจง่าย
4. **การจัดรูปแบบ**: รักษาสีและรูปแบบตาม Template เดิม
5. **การตั้งชื่อ**: ใช้รูปแบบการตั้งชื่อให้สอดคล้องกับตัวอย่าง
6. **ภาษา**: เขียน Test Case เป็นภาษาอังกฤษเท่านั้น สำหรับคอลัมน์ Name, Objective, Precondition, Test Script Steps, Expected Result, และ Post Step

Template นี้เป็นมาตรฐานที่ช่วยให้การสร้างและจัดการ Test Case เป็นระบบและสามารถติดตามได้อย่างมีประสิทธิภาพ
