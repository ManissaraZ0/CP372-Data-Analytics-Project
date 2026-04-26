# Channel Profitability Optimization for Azure Stay 

โครงการนี้เป็นส่วนหนึ่งของรายวิชา CP372 Data Analytics and Business Intelligence โดยมีวัตถุประสงค์เพื่อประยุกต์ใช้เครื่องมือและกระบวนการวิเคราะห์ข้อมูลเพื่อแก้ไขปัญหาทางธุรกิจจริง

เนื้อหาหลักมุ่งเน้นไปที่การแก้ปัญหา ค่าใช้จ่ายในการจัดจำหน่ายสูง (High Distribution Costs) ของโรงแรม Azure Stay ซึ่งเกิดจากการพึ่งพาช่องทาง Online Travel Agency (OTA) มากเกินไป จนส่งผลกระทบต่อกำไรสุทธิ (Net Profit) แม้จะมีอัตราการจองสูงก็ตาม

# Members
1. นางสาวมณิสรา	แซ่จัน รหัสนิสิต 66102010151
2. นายฐิติวัฒน์	ฮาบสุวรรณ		รหัสนิสิต 66102010238
3. นางสาวเอมี่หลุยส์	บราวน์		รหัสนิสิต 66102010572

# Project Canvas
แปะภาพ canvas

# 1. Background & Pain Points
Azure Stay เป็นโรงแรมขนาดกลางที่จำหน่ายห้องพักผ่านหลายช่องทาง ได้แก่ Direct Website, Walk-in และ OTA เช่น Booking.com, Expedia และ Agoda ซึ่งกำลังประสบปัญหาด้านกำไร

แม้ OTA จะช่วยเพิ่มยอดการจองและ occupancy แต่กลับก่อให้เกิด High Distribution Costs เนื่องจากมีค่าคอมมิชชันในอัตราสูง

ผลกระทบทางธุรกิจ:
* Gross Revenue สูง แต่ Net Revenue ต่ำ
* Cost of Acquisition (COA) สูงเกินไป
* Net RevPAR ต่ำกว่าศักยภาพที่ควรเป็น
* Channel Mix ไม่มีประสิทธิภาพ

ดังนั้น การวัดผลจากเพียงยอดจองไม่เพียงพอ จำเป็นต้องวิเคราะห์ profitability ในระดับ channel

# 2. SMART Objectives
เพิ่มรายได้สุทธิหลังหักค่าคอมมิชชั่นของโรงแรมให้ได้ 15% ภายใน 12 เดือน โดยการปรับสัดส่วนของช่องทางการจอง เพิ่มการจองโดยตรง และลดการพึ่งพาช่องทางการจองผ่านตัวแทนจำหน่ายออนไลน์ (OTA) ที่มีค่าคอมมิชชั่นสูง

**SMART Breakdown:**
* Specific: เพิ่มรายได้สุทธิหลังหักค่าคอมมิชชั่น
* Measurable: +15%
* Achievable: ผ่านการปรับสัดส่วนของช่องทางการจอง
* Relevant: แก้ปัญหา profitability โดยตรง
* Time-bound: 12 เดือน

# 3. Hypothesis & Method

## 3.1 Hypothesis
### **Hypothesis 1**: ช่องทาง OTA (Online Travel Agency) สร้างปริมาณยอดจองสูง แต่มี Net ADR ต่ำที่สุด
* **ประเด็นการพิสูจน์ (Key Questions)**:
   * 1.1. Gross ADR ของช่องทาง OTA แตกต่างจาก Direct Website หรือไม่?
   * 1.2. ช่องทาง OTA มี Net ADR ต่ำกว่า Direct Website ตั้งแต่ 15% ขึ้นไปจริงหรือไม่?
   * 1.3. แม้ OTA จะมี Volume สูง แต่ค่า Net Revenue ต่อการจอง (Profit Efficiency) ต่ำกว่าช่องทาง Direct หรือไม่?

### **Hypothesis 2**: ช่องทาง OTA ในวันธรรมดา (วันจันทร์–ศุกร์) จะมีค่า Net RevPAR ต่ำกว่าช่องทาง Walk-in และ Corporate มากกว่า 20% เนื่องจากต้องใช้ส่วนลดราคาและมีค่าคอมมิชชันสูง ในขณะที่ demand โดยรวมต่
* **ประเด็นการพิสูจน์ (Key Questions)**:
   * 2.1. OTA มี ADR ต่ำกว่าช่องทางอื่นในวันธรรมดาจริงหรือไม่?
   * 2.2. OTA มี COA% สูงกว่าช่องทางอื่นหรือไม่?
   * 2.3. Occupancy ของ OTA สามารถชดเชย Net RevPAR ที่ต่ำได้หรือไม่?

### **Hypothesis 3**: การจองที่ใช้ Promo Rate ผ่านช่องทาง OTA จะมีค่า Cost of Acquisition (COA%) สูงกว่าการจองกลุ่มอื่น เนื่องจากรายได้ต่อการจองลดลงจากโปรโมชั่น แต่ยังคงถูกหักค่าคอมมิชชันจาก OTA
* **ประเด็นการพิสูจน์ (Key Questions)**:
   * 3.1. OTA มีค่าเฉลี่ย COA% สูงกว่าช่องทางอื่นหรือไม่?
   * 3.2. Commission Rate มีความสัมพันธ์กับ COA% หรือไม่?
   * 3.3. Promo Rate ทำให้ COA% สูงขึ้นหรือไม่?
 
### **Hypothesis 4**: โครงสร้างอัตราราคา Rate มีผลต่อ Net Revenue ของโรงแรม
* **ประเด็นการพิสูจน์ (Key Questions)**:
   * 4.1. Rate Code ที่มี Net RevPAR สูง จะสร้าง Net Revenue ได้ดีกว่า Rate อื่นหรือไม่?
   * 4.2. Rate Code ที่มี Cancellation Rate ต่ำ จะมีคุณภาพ booking ดีกว่าหรือไม่?
   * 4.3. Rate Code ที่มี Commission ต่ำ จะสร้าง margin ได้ดีกว่าหรือไม่?
   * 4.4. Promotional Rate ช่วยเพิ่มยอดขายแต่ลด Net RevPAR หรือไม่?

## 3.2 Methodology
### 3.2.1. Data Quality Assessment
จากการตรวจสอบคุณภาพข้อมูลเพื่อประเมินความสมบูรณ์และความถูกต้องของชุดข้อมูลก่อนนำไปใช้ในการวิเคราะห์ มีผลการตรวจสอบดังนี้
* ไม่พบค่าที่หายไป (Missing Values) ในทุกตารางข้อมูล
* ไม่พบข้อมูลซ้ำ (Duplicate Records)
* ได้ทำการตรวจสอบและปรับปรุงชนิดข้อมูลของแต่ละตัวแปร (Data Types) ให้เหมาะสมต่อการวิเคราะห์ 

### 3.2.2. Data Preparation
จัดการ Data Modeling และเตรียมความพร้อมข้อมูลบน Tableau เพื่อให้ข้อมูลพร้อมสำหรับวิเคราะห์ KPIs ของโรงแรม เราจำเป็นต้องปรับเปลี่ยนโครงสร้างข้อมูลจาก Booking-level ไปสู่ Daily Stay-level โดยแบ่งการทำงานออกเป็น 2 ส่วนดังนี้

**1. การทำ Physical Join (ภายใน Logical Table: dim_calendar)**
* จุดประสงค์: เพื่อสร้างมิติของข้อมูลรายวัน (Daily Grain) สำหรับคำนวณ Metrics
* `dim_calendar` (Base Table): ใช้เป็นตารางหลักในการกระจายข้อมูล
* `dim_room_inventory` (Left Join): เชื่อมด้วย `Date Key = Date` เพื่อระบุจำนวนห้องว่างรายวัน
* `fact_bookings` (Left Join): ใช้เงื่อนไข Non-equi Join `(Check In Date <= Date Key < Check Out Date)` เพื่อทำ Data Densification (หรือการแปลงจาก Booking-level เป็น Daily Stay-level/Room-night) ช่วยให้ 1 การจองที่พักหลายวัน ถูกขยายออกเป็นแถวรายวันตามจำนวนคืนที่เข้าพักจริง
* `dim_channels` & `dim_rate_codes` (Inner Join): เชื่อมด้วย `Channel Id` และ `Rate Code Id` เพื่อเพิ่มมิติการวิเคราะห์ (Context) ให้กับข้อมูลการจอง

**2. การสร้าง Relationship (Logical Layer)**
* จุดประสงค์: เพื่อเชื่อมโยงข้อมูลฝั่ง Marketing Spend โดยรักษาความถูกต้องของข้อมูลรายวัน
* `fact_marketing_spend`: เชื่อมต่อกับ `dim_calendar` และ `dim_channels` ผ่าน Relationship แทนการทำ Physical Join
* เหตุผล
   * เพื่อหลีกเลี่ยง Data Duplication การทำ Join กับ fact_marketing_spend ในระดับ Physical Layer จะทำให้ค่า Metrics ในตาราง fact_bookings เกิดการซ้ำซ้อน (Fan-out) เมื่อมีการกระจายข้อมูลรายวัน (Daily Grain)
   * เพื่อให้ Data Integrity การใช้ Relationship ช่วยให้ Tableau คำนวณค่า Aggregated Metrics (เช่น ผลรวมของ Marketing Spend หรือ Revenue) ได้อย่างถูกต้องตาม Context ของวันที่และช่องทาง โดยไม่ทำให้ตัวเลขในระดับ Stay-level เกิดการคำนวณที่ผิดพลาดหรือข้อมูลเพี้ยน

### 3.2.3. การสร้าง Calculated Field สำหรับ Measures & Dimensions
**1. Average Daily Rate (ADR)**
   * ราคาขายเฉลี่ยต่อห้องที่ขายได้จริง ไม่รวมภาษีและค่าบริการอื่นๆ
   * สูตร: `Total Gross Room Revenue / Number of Rooms Sold`
   * คำอธิบาย: เป็นตัวชี้วัดประสิทธิภาพในการตั้งราคาห้องพัก โดยวัดจากรายได้ส่วนที่เป็นค่าห้องพักโดยตรง หารด้วยจำนวนคืนที่ขายได้ (Room Nights)
   * สูตรสำหรับ Tableau Calculated Fields:
```
SUM(
 IF [Status] IN ("Confirmed","Checked-Out") THEN [Gross Room Revenue]
 ELSEIF [Status] = "Cancelled" AND [Rate Code Id] = "RT_02" THEN [Gross Room Revenue]
 END
)
/
COUNT( IF [Status] IN ("Confirmed","Checked-Out") THEN [Date Key] END )
```

**2. Occupancy Rate (OCC %)**
   * สัดส่วนของห้องที่ถูกจองเทียบกับจำนวนห้องทั้งหมดที่มีให้บริการ
   * สูตร: `(Number of Rooms Sold / Total Rooms Available) * 100`
   * คำอธิบาย: วัดประสิทธิภาพการบริหารจัดการห้องพัก (Utilization Rate) โดยใช้ FIXED เพื่อล็อค Grain ของ Capacity ในระดับวัน เพื่อป้องกันการนับซ้ำเมื่อข้อมูลถูกขยาย (Densified) ในระดับรายวัน
   * สูตรสำหรับ Tableau Calculated Fields:
```
COUNT(IF [Status] IN ("Confirmed","Checked-Out") THEN [Booking Id] END) /
SUM({ FIXED [Date Key] : MAX([Rooms Available For Sale]) })
```

**3. Net ADR**
   * ราคาขายเฉลี่ยต่อห้องหลังจากหักค่าใช้จ่ายทางการขาย (เช่น ค่าคอมมิชชั่น)
   * สูตร: `Net Revenue / Number of Rooms Sold`
   * คำอธิบาย: ช่วยให้ทราบราคาขายที่แท้จริงหลังจากหักต้นทุนการขาย (Acquisition Cost) เพื่อให้เห็นผลกำไรที่ได้รับจริงต่อการเข้าพัก 1 คืน
   * สูตรสำหรับ Tableau Calculated Fields:
```
SUM(
 IF [Status] IN ("Confirmed","Checked-Out") THEN [Net Room Revenue]

 ELSEIF [Status] = "Cancelled"
 AND [Rate Code Id] = "RT_02"
 THEN [Net Room Revenue]
 END
)
/
COUNT(
 IF [Status] IN ("Confirmed","Checked-Out") THEN [Date Key] END
)
```

**4. Net Revenue per Available Room (Net RevPAR)**
   * รายได้สุทธิที่เกิดขึ้นจริงต่อห้องพักทั้งหมดที่มีให้บริการ (รวมห้องที่ขายไม่ออกด้วย)
   * สูตร: `(Gross Revenue - Commission Cost) / Total Rooms Available`
   * คำอธิบาย: เป็น KPI ที่สำคัญที่สุดตัวหนึ่ง เพราะสะท้อนถึงทั้ง "ความสามารถในการขาย" (Occupancy) และ "ความสามารถในการทำกำไร" (Net Rate) ในคราวเดียว
   * สูตรสำหรับ Tableau Calculated Fields:
```
SUM(
 IF [Status] IN ("Confirmed","Checked-Out") THEN [Net Room Revenue]

 ELSEIF [Status] = "Cancelled"
 AND [Rate Code Id] = "RT_02"
 THEN [Net Room Revenue]
 END
)
/
SUM({ FIXED [Date Key] : MAX([Rooms Available For Sale]) })
```

**5. Cost of Acquisition (COA %)**
   * สัดส่วนต้นทุนที่ใช้ในการได้มาซึ่งการจองเทียบกับรายได้รวม
   * สูตร: `(Total Commission + Marketing Spend) / Total Revenue`
   * คำอธิบาย: วัดความคุ้มค่าของการตลาดและช่องทางการขาย หากค่านี้สูงเกินไปอาจหมายถึงการจ่ายค่าคอมมิชชั่นหรือใช้งบการตลาดสูงเกินกว่ารายได้ที่ได้รับ
   * สูตรสำหรับ Tableau Calculated Fields:
```
(IFNULL(SUM([Commission Amount]), 0) + IFNULL(SUM([Cost Amount]), 0)) /
SUM([Net Room Revenue])
```

**6. Cancellation Rate**
   * อัตราการยกเลิกการจอง
   * สูตร: `Total Cancelled Bookings / Total Bookings`
   * คำอธิบาย: วัดความเสี่ยงหรือความไม่แน่นอนของการจอง (Booking Volatility) ยิ่งค่าสูงยิ่งส่งผลกระทบต่อการวางแผนบริหารจำนวนห้องว่าง (Inventory Management)
   * สูตรสำหรับ Tableau Calculated Fields:
```
COUNTD(IF [Status] = "Cancelled" THEN [Booking Id] END) /
COUNTD([Booking Id])
```

### 3.2.4. Hypothesis Testing & Analysis

#### ขั้นตอนการพิสูจน์ Hypothesis 1: ช่องทาง OTA สร้างยอดจองสูง แต่มี Net ADR ต่ำที่สุด

**1. Hypothesis Statement**

ช่องทาง OTA เช่น Booking.com, Agoda และ Expedia สามารถสร้างจำนวนการจองได้สูงกว่าช่องทางอื่น แต่มีค่า Net ADR ต่ำกว่าช่องทาง Direct อย่างน้อย 15% เนื่องจาก OTA มีต้นทุนค่าคอมมิชชันสูง แม้ว่า Gross ADR หรือราคาขายก่อนหักต้นทุนอาจใกล้เคียงกับ Direct

**2. Research Objective**

วัตถุประสงค์ของสมมติฐานนี้คือ เพื่อวิเคราะห์ว่า OTA เป็นช่องทางที่สร้างยอดขายจำนวนมากจริงหรือไม่ และยอดขายที่เกิดขึ้นนั้นสามารถแปลงเป็นรายได้สุทธิต่อห้องได้ดีเท่ากับช่องทาง Direct หรือไม่
กล่าวอีกแบบคือ ต้องการตรวจสอบว่า OTA เป็นช่องทางที่ดีในเชิง Volume Strategy แต่ด้อยกว่า Direct ในเชิง Profitability Efficiency หรือไม่

**3. Sub-Hypotheses / Research Questions**
* H1.1 OTA มี Gross ADR ใกล้เคียงกับ Direct หรือไม่ : เพื่อตรวจสอบว่าโรงแรมตั้งราคาขายบน OTA ต่ำกว่า Direct มากหรือไม่
* H1.2 OTA มี Net ADR ต่ำกว่า Direct อย่างน้อย 15% หรือไม่ : เพื่อตรวจสอบผลกระทบจาก commission และต้นทุน acquisition
* H1.3 OTA แม้มี booking volume สูง แต่ profit efficiency ต่ำกว่า Direct หรือไม่ : เพื่อตรวจสอบว่า OTA สร้างรายได้มากจากจำนวน booking หรือจากคุณภาพของ booking

**4. Methodology**

การวิเคราะห์ใช้ข้อมูลการจองโรงแรมแยกตาม Channel Type โดยเปรียบเทียบช่องทางหลัก ได้แก่
* OTA
* Direct
* Corporate
* Wholesale

จากนั้นนำข้อมูลมาวิเคราะห์ใน 3 มิติหลัก ได้แก่
1. Volume Performance ดูว่าช่องทางใดสร้างจำนวน booking สูงที่สุด
2. Price Performance เปรียบเทียบ ADR และ Net ADR ของแต่ละช่องทาง
3. Profit Efficiency วิเคราะห์ว่าแต่ละช่องทางสามารถเปลี่ยน booking ให้เป็นรายได้สุทธิได้ดีเพียงใด

**5. Data Visualization**

**Graph 1: Bubble Chart**
* **ชื่อกราฟ:** Total Net Revenue vs Net ADR vs Number of Bookings by Channel
* **การแสดงผล**
   * X-axis = Number of Bookings
   * Y-axis = Net ADR
   * Bubble Size = Total Net Revenue
   * Color = Channel Type
* **เหตุผลที่เลือกใช้**
Bubble Chart เหมาะสำหรับการวิเคราะห์ข้อมูลหลายมิติพร้อมกัน เพราะสามารถแสดงทั้งจำนวน booking, รายได้สุทธิต่อห้อง และรายได้สุทธิรวมในกราฟเดียว
* **กราฟนี้ช่วยตอบคำถามว่า**
   * ช่องทางใดมี volume สูงที่สุด
   * ช่องทางใดมี Net ADR สูงที่สุด
   * ช่องทางใดสร้างรายได้สุทธิรวมมากที่สุด
   * OTA มี volume สูงแต่ Net ADR ต่ำจริงหรือไม่

**Graph 2: Side-by-Side Bar Chart**
* **ชื่อกราฟ:** ADR vs Net ADR by Channel
* **การแสดงผล**
   * Columns = Channel Type
   * Rows = ADR และ Net ADR
   * Color = Measure Name
   * Label = ค่า ADR และ Net ADR
* **เหตุผลที่เลือกใช้**
Side-by-Side Bar Chart เหมาะสำหรับเปรียบเทียบ 2 metrics ภายในหมวดหมู่เดียวกัน ทำให้เห็นความต่างระหว่างรายได้ก่อนและหลังหักค่าคอมมิชชันได้ชัดเจน
* **กราฟนี้ช่วยตอบว่า**
   * ช่องทางใดถูกหักต้นทุนมากที่สุด
   * ช่องทางใดรักษา Net ADR ได้ดีที่สุด
   * OTA สูญเสียรายได้จาก commission มากกว่า Direct หรือไม่


**6. Hypothesis Testing Criteria**

สมมติฐานนี้จะถือว่า Supported หากพบว่า
1. OTA มีจำนวน booking สูงที่สุด
2. OTA มี Gross ADR ใกล้เคียงกับ Direct
3. OTA มี Net ADR ต่ำกว่า Direct อย่างน้อย 15%
4. OTA มีรายได้ต่อ booking ต่ำกว่า Direct แม้จะสร้างรายได้รวมสูง

**7. Analysis Results**

ผลการวิเคราะห์พบว่า สมมติฐานนี้ Partially Supported
* OTA เป็นช่องทางที่สร้างจำนวน booking สูงที่สุด ประมาณ 23,000 รายการ แสดงให้เห็นว่า OTA มีบทบาทสำคัญในการสร้าง demand และดึงลูกค้าเข้าสู่โรงแรม
* อย่างไรก็ตาม OTA ไม่ได้มี Net ADR ต่ำที่สุด เพราะช่องทาง Wholesale มี Net ADR ต่ำกว่า OTA แต่ OTA มี Net ADR ต่ำกว่า Direct อย่างชัดเจน

**8. Sub-Hypothesis Findings**
##### H1.1 OTA มี Gross ADR ใกล้เคียง Direct หรือไม่

ผลลัพธ์พบว่า

| Channel                  | ADR โดยประมาณ                    |
|--------------------------|-----------------------------------|
| Direct                   | ≈ 530                             |
| OTA                      | ≈ 500                             | 

* ความแตกต่างอยู่ที่ประมาณ 5–6% จึงถือว่า Gross ADR ของ OTA ใกล้เคียงกับ Direct
* **Conclusion:** Supported

##### H1.2 OTA มี Net ADR ต่ำกว่า Direct อย่างน้อย 15% หรือไม่
  
ผลลัพธ์พบว่า

| Channel                  | ADR โดยประมาณ                    |
|--------------------------|-----------------------------------|
| Direct                   | ≈ 550                             |
| OTA                      | ≈ 420                             |

* OTA มี Net ADR ต่ำกว่า Direct ประมาณ 23.6% ซึ่งมากกว่าเกณฑ์ 15%
* **Conclusion:** Supported

##### H1.3 OTA มี booking volume สูง แต่ profit efficiency ต่ำหรือไม่
* OTA สร้าง Net Revenue รวมสูง เนื่องจากมีจำนวน booking มาก แต่เมื่อพิจารณารายได้สุทธิต่อ booking พบว่า Direct มีประสิทธิภาพดีกว่า
* **Conclusion:** Supported

**9. Key Insights**
1. OTA เป็นช่องทางหลักในการสร้าง booking volume
2. OTA ไม่ได้ขายราคาถูกกว่า Direct มากในระดับ Gross ADR
3. รายได้สุทธิลดลงหลังหัก commission
4. Direct มี margin ต่อ booking ดีกว่า OTA
5. OTA เหมาะกับการสร้าง demand แต่ไม่ควรเป็นช่องทางหลักเพียงอย่างเดียว

**10. Business Implications / Recommendations**
1. ใช้ OTA เป็น Customer Acquisition Channel
   * OTA ควรถูกใช้เพื่อดึงลูกค้าใหม่ โดยเฉพาะลูกค้าต่างชาติหรือลูกค้าที่เริ่มค้นหาโรงแรมผ่าน platform เปรียบเทียบราคา
2. เปลี่ยนลูกค้า OTA ให้กลับมาจองตรง
   * โรงแรมควรมี strategy เพื่อเปลี่ยนลูกค้า OTA ให้กลับมาจองผ่าน Direct ในครั้งถัดไป เช่น
      * ส่วนลดสำหรับการจองตรงครั้งถัดไป
      * Member loyalty program
      * Free upgrade
      * Late check-out
      * Email remarketing หลัง check-out
3. จำกัด OTA ในช่วง High Demand
   * ในช่วงที่ demand สูง เช่น weekend, holiday หรือ event period ควรลด allocation บน OTA และผลักดัน booking ผ่าน Direct เพื่อรักษา margin

#### ขั้นตอนการพิสูจน์ Hypothesis 2:

# Logical folder structure
```
project-root/
│
├── data/
│   ├── dim_calendar.csv
│   ├── dim_channels.csv
│   ├── dim_rate_codes.csv
│   ├── dim_room_inventory.csv
│   ├── fact_bookings.csv
│   └── fact_marketing_spend.csv
│
├── notebooks/
│   └── (Jupyter / Python notebooks)
│
├── dashboards/
│   └── Hotel_Performance_Dashboard.twb
│
├── docs/
│   ├── presentation_slides/
│   └── images/
│
└── README.md
```


# AI-generated dataset
* fact_bookings 
* dim_room_inventory 
* dim_channels 
* dim_rate_codes 
* fact_marketing_spend 
* dim_calendar


# prompt that is used for generating data
```
Generate a clean, realistic synthetic hotel dataset for business intelligence analysis in CSV format (separate CSV file for each table).

Hotel Profile:
“The Azure Stay” – a mid-sized independent hotel with 120 rooms and there were profitability is stagnant issues.

-----------------------------------
BUSINESS SCENARIO
-----------------------------------
High Distribution Costs (Channel Profitability)

The hotel generates strong booking volume, primarily from OTA channels (e.g., Booking.com, Expedia), but pays high commissions. The objective is to analyze true profitability by channel, not just booking volume.

-----------------------------------
DATA REQUIREMENTS
-----------------------------------
- Clean and analysis-ready data
- No null values unless logically required
- No duplicate primary keys
- Valid foreign key relationships
- Realistic dates and values
- Consistent naming conventions
- Logical revenue calculations
- Suitable for SQL / Power BI / Tableau

Date Range:
2025-01-01 to 2025-12-31

-----------------------------------
BUSINESS CONSTRAINTS (HARD RULES)
-----------------------------------
- Daily occupied rooms must NOT exceed rooms_available_for_sale
- Overbooking is allowed ONLY:
  - During High Season or Holidays
  - Maximum 105% of available rooms
  - Occurs on less than 3% of total days
- Booking date must be before check-in date
- Length of stay must be between 1–7 nights
- Cancelled bookings must have zero revenue
- Net revenue = Gross revenue – Commission

-----------------------------------
GENERATION LOGIC (CRITICAL)
-----------------------------------
The dataset MUST be generated using day-level inventory control.

1. For each date:
   - Calculate rooms_available_for_sale from inventory
   - Assign a target occupancy based on season and weekday/weekend

2. Generate bookings from occupancy:
   - Each booking represents 1 room per night
   - Each booking spans from check-in to check-out (multi-night stays)

3. Capacity enforcement:
   - For every date, total occupied rooms (from all active bookings)
     MUST NOT exceed rooms_available_for_sale (except allowed overbooking cases)

4. Overbooking:
   - Only in High Season or holidays
   - Max 105% occupancy
   - Rare occurrence (<3% of days)

5. DO NOT generate bookings independently.
   Bookings must be derived from daily occupancy allocation.

-----------------------------------
SEASON & DEMAND STRUCTURE
-----------------------------------
Season Mapping:
- Jan–Apr: High Season
- May–Jun: Low Season
- Jul–Oct: Shoulder Season
- Nov–Dec: High Season

Occupancy Targets:
- Low Season: 55%–70%
- Shoulder Season: 70%–85%
- High Season: 85%–98%

Demand Behavior:
- Weekends have higher occupancy than weekdays
- December has peak demand (highest occupancy)
- Corporate/GDS perform stronger on weekdays

-----------------------------------
PRICING & REVENUE LOGIC
-----------------------------------
ADR Guidelines (per night):
- High Season: 120–220 USD
- Shoulder Season: 90–160 USD
- Low Season: 70–120 USD

Rate Behavior:
- Corporate Flat Rate: lower but stable ADR (80–110 USD)
- Seasonal Promo: 10–25% discount from base rate
- Direct channels tend to have higher net ADR

Commission Rules:
- Apply commission only if rate is commissionable
- Commission = gross_room_revenue × channel commission rate

-----------------------------------
CHANNEL PERFORMANCE LOGIC
-----------------------------------
- OTA channels:
  - Highest booking volume
  - High commission → lower net profitability
- Direct Website:
  - Lower booking volume
  - Lowest commission → highest net profitability
- Corporate / GDS:
  - Moderate volume
  - Stable revenue (especially weekdays)
- Walk-in:
  - Low volume, no commission

-----------------------------------
BOOKING STATUS DISTRIBUTION
-----------------------------------
- Checked-Out: 70–80%
- Confirmed: 15–25%
- Cancelled: 5–10%

-----------------------------------
TABLE STRUCTURE
-----------------------------------

TABLE: fact_bookings
booking_id (PK)
booking_date
check_in_date
check_out_date
channel_id (FK)
rate_code_id (FK)
gross_room_revenue
commission_amount
net_room_revenue
status

Rules:
- net_room_revenue = gross_room_revenue - commission_amount
- Cancelled bookings should have zero revenue
- Checked-Out and Confirmed should have normal revenue
- Length of stay between 1 to 7 nights
- Booking date should occur before check-in date

-----------------------------------

TABLE: dim_room_inventory
date (PK)
total_capacity (fixed = 120)
rooms_out_of_order (0–8)
rooms_available_for_sale = total_capacity - rooms_out_of_order

Rules:
- Hotel total capacity = 120 rooms
- rooms_out_of_order should vary between 0 to 8
- rooms_available_for_sale = total_capacity - rooms_out_of_order

-----------------------------------

TABLE: dim_channels
channel_id (PK)
channel_name
channel_type
commission_model
default_commission_rate
contract_owner

Suggested Values:
CH_01 Direct Website | Direct | Percentage | 0.03
CH_02 Booking.com | OTA | Percentage | 0.18
CH_03 Expedia | OTA | Percentage | 0.20
CH_04 Agoda | OTA | Percentage | 0.17
CH_05 Walk-in | Direct | Flat Fee | 0
CH_06 Corporate Agent | Wholesale | Percentage | 0.10
CH_07 GDS | Corporate | Percentage | 0.12

-----------------------------------

TABLE: dim_rate_codes
rate_code_id (PK)
rate_name
is_commissionable

Suggested Values:
RT_01 Rack Rate | True
RT_02 Non-Refundable | True
RT_03 Seasonal Promo | True
RT_04 Corporate Flat Rate | False
RT_05 AAA Discount | True
RT_06 Member Direct Rate | False

-----------------------------------

TABLE: fact_marketing_spend
spend_id (PK)
spend_date
channel_id (FK)
platform
cost_amount
clicks

Rules:
- Primarily for Direct Website (CH_01)
- Platforms: Google Ads, Facebook Ads, Instagram Ads, Meta Search
- Cost: 50–1000 USD
- Clicks: 20–1000

-----------------------------------

TABLE: dim_calendar
date_key (PK)
day_name
is_weekend
is_holiday
season

-----------------------------------
OUTPUT FORMAT
-----------------------------------
Provide:
1. Separate CSV content for each table
2. Data dictionary (column definitions)
3. Summary of business patterns reflected in the dataset
```

# Data Dictionary 
### TABLE 1: fact_bookings

- จำนวนแถวข้อมูล: **9978**
- จำนวนแอททริบิวต์: **10**

| Attribute | คำอธิบาย | Data Type | ช่วงค่าที่ถูกต้อง / ตัวอย่าง |
|----------|----------|----------|-----------------------------|
| booking_id | รหัสอ้างอิงการจอง (Primary Key) | Ordinal | BK00001, BK09985 |
| booking_date | วันที่ทำการบันทึกการจอง | Interval (Date) | 8/1/2025 |
| check_in_date | วันที่ลูกค้าเข้าพัก | Interval (Date) | 1/6/2025 |
| check_out_date | วันที่ลูกค้าออกจากที่พัก | Interval (Date) | 9/1/2025 |
| channel_id | รหัสช่องทางการจอง (Foreign Key) | Nominal | CH_01, CH_02, CH_03 |
| rate_code_id | รหัสประเภทเรต/โปรโมชั่น (Foreign Key) | Nominal | RT_01, RT_02, RT_05 |
| gross_room_revenue | รายได้ค่าห้องรวม (ก่อนหักค่าคอมมิชชัน) | Ratio (Continuous) | 0 – ∞ (เช่น 1066.4) |
| commission_amount | จำนวนค่านายหน้าหรือค่าธรรมเนียมช่องทาง | Ratio (Continuous) | 0 – ∞ (เช่น 213.28) |
| net_room_revenue | รายได้ค่าห้องสุทธิ (Gross - Commission) | Ratio (Continuous) | 0 – ∞ (เช่น 853.12) |
| status | สถานะของการจอง | Nominal | Confirmed, Checked-Out, Cancelled |

### TABLE 2: dim_room_inventory
- จำนวนแถวข้อมูล: **365** 
- จำนวนแอตทริบิวต์: **4**  

| Attribute                   | คำอธิบาย                                          | Data Type         | ช่วงค่าที่ถูกต้อง / ตัวอย่าง        |
|---------------------------|--------------------------------------------------|-------------------|------------------------------------|
| date                      | วันที่บันทึกข้อมูล (Primary Key)                  | Interval (Date)   | 8/1/2025                           |
| total_capacity            | จำนวนห้องทั้งหมดในโรงแรม                          | Ratio (Discrete)  | 120                                |
| rooms_out_of_order        | จำนวนห้องที่ปิดปรับปรุง/ไม่พร้อมใช้งาน           | Ratio (Discrete)  | 0 – 120 (เช่น 2, 5)                |
| rooms_available_for_sale  | จำนวนห้องที่ว่างและสามารถขายได้จริง               | Ratio (Discrete)  | 0 – 120 (เช่น 118, 120)            |


### TABLE 3: dim_channels
- จำนวนแถวข้อมูล: **7**
- จำนวนแอตทริบิวต์: **6** 

| Attribute                  | คำอธิบาย                                  | Data Type            | ช่วงค่าที่ถูกต้อง / ตัวอย่าง                |
|---------------------------|--------------------------------------------|----------------------|----------------------------------------------|
| channel_id               | รหัสช่องทางการจอง (Primary Key)           | Nominal              | CH_01, CH_02                                 |
| channel_name             | ชื่อเรียกช่องทางการจอง                    | Nominal              | Direct Website, Booking.com, Agoda          |
| channel_type             | ประเภทของช่องทาง                          | Nominal              | Direct, OTA, Wholesale, Corporate           |
| commission_model         | รูปแบบการคิดค่าคอมมิชชั่น                 | Nominal              | Percentage, Flat Fee                        |
| default_commission_rate  | อัตราค่าคอมมิชชั่นมาตรฐาน                | Ratio (Continuous)   | 0.0 – 1.0 (เช่น 0.15 สำหรับ 15%)            |
| contract_owner           | หน่วยงานที่ดูแลรับผิดชอบสัญญา            | Nominal              | Marketing Dept, Revenue Dept, Sales Dept    |
### TABLE 4: fact_marketing_spend
- จำนวนแถวข้อมูล: **600**  
- จำนวนแอตทริบิวต์: **6**  

| Attribute     | คำอธิบาย                                   | Data Type            | ช่วงค่าที่ถูกต้อง / ตัวอย่าง                |
|---------------|---------------------------------------------|----------------------|----------------------------------------------|
| spend_id      | รหัสรายการค่าใช้จ่าย (Primary Key)         | Nominal              | SP0001, SP0002                               |
| spend_date    | วันที่ใช้จ่าย                               | Date                 | 2025-01-01                                   |
| channel_id    | รหัสช่องทางการตลาด (Foreign Key)           | Nominal              | CH_01, CH_02                                 |
| platform      | แพลตฟอร์มที่ใช้โฆษณา                       | Nominal              | Google Ads, Facebook Ads, Instagram Ads      |
| cost_amount   | จำนวนเงินที่ใช้                             | Ratio (Continuous)   | 202.62, 777.14                               |
| clicks        | จำนวนคลิก                                  | Ratio (Discrete)     | 239, 974                                     |


### TABLE 5: dim_rate_codes
- จำนวนแถวข้อมูล: **6**  
- จำนวนแอตทริบิวต์: **3**  

| Attribute           | คำอธิบาย                                   | Data Type          | ช่วงค่าที่ถูกต้อง / ตัวอย่าง                |
|---------------------|---------------------------------------------|--------------------|----------------------------------------------|
| rate_code_id        | รหัสประเภทเรทราคา (Primary Key)             | Nominal            | RT_01, RT_02                                 |
| rate_name           | ชื่อเรทราคา                                | Nominal            | Rack Rate, Non-Refundable, Corporate Rate    |
| is_commissionable   | ระบุว่ามีค่าคอมมิชชั่นหรือไม่               | Binary (Boolean)   | True, False                                  |


### TABLE 6: dim_calendar
- จำนวนแถวข้อมูล: **365**  
- จำนวนแอตทริบิวต์: **5**  

| Attribute     | คำอธิบาย                          | Data Type          | ช่วงค่าที่ถูกต้อง / ตัวอย่าง        |
|---------------|----------------------------------|--------------------|--------------------------------------|
| date_key      | วันที่ (Primary Key)             | Date               | 2025-01-01                           |
| date_name     | ชื่อวัน                           | Nominal            | Monday, Tuesday                      |
| is_weekend    | เป็นวันหยุดสุดสัปดาห์หรือไม่     | Binary (Boolean)   | True, False                          |
| is_holiday    | เป็นวันหยุดนักขัตฤกษ์หรือไม่     | Binary (Boolean)   | True, False                          |
| holiday       | ฤดูกาลท่องเที่ยว                | Nominal            | High Season, Low Season              |
# Methodology

## Measures & Dimensions
สร้าง Calculated Fields สำหรับ Measures
 * ADR (Average Daily Rate) 

Total Gross Room Revenue / Number of Rooms Sold
  
  สูตรสำหรับ Tableau Calculated Fields:
```
SUM(
 IF [Status] IN ("Confirmed","Checked-Out")
 THEN [Gross Room Revenue]
 END
)
/
COUNT(
 IF [Status] IN ("Confirmed","Checked-Out")
 THEN [Date Key]
 END
)
```
ใช้ COUNT date key เพราะใช้นับเป็นจำนวนห้องที่ขายได้แทน

* OCC (Occupancy) 
(Number of Rooms Sold / Total Rooms Available) * 100
สูตรสำหรับ Tableau Calculated Fields:
```
COUNT(
 IF [Status] IN ("Confirmed","Checked-Out")
 THEN [Booking Id]
 END
)
/ SUM({ FIXED [Date Key] : MAX([Rooms Available For Sale]) })
```
ใช้ FIXED ต่อ 1 วัน (Date Key) ห้องทั้งหมดต้องนับแค่ครั้งเดียว และเอาค่า MAX ที่มากที่สุด ซึ่งจริง ๆ ทุก row เท่ากันอยู่แล้ว
ใช้ FIXED เพื่อ "ล็อก grain ของข้อมูลให้เป็นระดับวัน" แล้วใช้ MAX เพื่อดึง capacity ของวันนั้นมา 1 ค่า และ SUM เพื่อรวม capacity ทั้งช่วงเวลา

* Net ADR
Net Revenue / Rooms Sold
สูตรสำหรับ Tableau Calculated Fields:
```
SUM(
 IF [Status] IN ("Confirmed","Checked-Out")
 THEN [Net Room Revenue]
 END
)
/
COUNT(
 IF [Status] IN ("Confirmed","Checked-Out")
 THEN [Date Key]
 END
)
```


* Commission Cost 
Gross Revenue * Commission Rate
ซึ่งมีอยู่แล้วในตาราง fact_booking ชื่อคอลัมน์ commission_amout

* Net RevPAR 
(Gross Revenue - Commission Cost) / Total Rooms Available
สูตรสำหรับ Tableau Calculated Fields:
```
SUM(
 IF [Status] IN ("Confirmed","Checked-Out")
 THEN [Net Room Revenue]
 END
)
/ SUM({ FIXED [Date Key] : MAX([Rooms Available For Sale]) })
```

* Cost of Acquisition (COA) % 
(Total Commission + Marketing Spend) / Total Revenue 
สูตรสำหรับ Tableau Calculated Fields
( SUM([Commission Amount]) + SUM([Cost Amount]))
/
SUM([Net Room Revenue])
```


# Findings (Insights)

# Recommendations

# Presentation Documents 
