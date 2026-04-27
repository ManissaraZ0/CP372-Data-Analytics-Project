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

#### ขั้นตอนการพิสูจน์ Hypothesis 2: OTA ทำกำไรต่ำในวันธรรมดา (Weekday)

**1. Hypothesis Statement**

ช่องทาง OTA ในวันธรรมดาจะมีค่า Net RevPAR ต่ำกว่าช่องทาง Direct และ Corporate มากกว่า 20% เนื่องจากต้องใช้ส่วนลดราคาและมีค่าคอมมิชชันสูง ในขณะที่ demand โดยรวมของ weekday ต่ำกว่า weekend

**2. Research Objective**

วัตถุประสงค์ของสมมติฐานนี้คือ เพื่อวิเคราะห์ว่า OTA เป็นช่องทางที่มีประสิทธิภาพต่ำในวันธรรมดาหรือไม่ โดยเฉพาะในช่วงที่ demand ต่ำ และโรงแรมต้องพึ่ง OTA เพื่อเติม occupancy
สมมติฐานนี้ต้องการดูว่า OTA ช่วยเพิ่ม occupancy ได้จริงหรือไม่ และ occupancy ที่เพิ่มขึ้นนั้นสามารถชดเชย margin ที่เสียไปจาก commission ได้หรือไม่

**3. Sub-Hypotheses / Research Questions**
* H2.1 OTA มี ADR ต่ำกว่า Direct ในวันธรรมดาหรือไม่ : เพื่อตรวจสอบว่า OTA ใช้ราคาที่ต่ำกว่าเพื่อกระตุ้น demand หรือไม่
* H2.2 OTA มี COA% สูงกว่าช่องทางอื่นหรือไม่ : เพื่อตรวจสอบผลกระทบของ commission
* H2.3 Occupancy ของ OTA สามารถชดเชย Net RevPAR ที่ต่ำได้หรือไม่ : เพื่อตรวจสอบว่า OTA มีประสิทธิภาพเมื่อ occupancy สูงขึ้นหรือไม่

**4. Methodology**

วิเคราะห์ข้อมูลโดยแบ่งออกเป็น 2 มิติหลัก
1. Channel Type
    * เปรียบเทียบ OTA, Direct, Corporate และ Wholesale
2. Day Type
    * แยกวันเป็น Weekday และ Weekend
จากนั้นวิเคราะห์ว่า OTA มี performance ใน weekday ต่ำกว่าช่องทางอื่นหรือไม่ โดยใช้ตัวชี้วัดหลัก ได้แก่ ADR, COA%, Occupancy และ Net RevPAR

**5. Data Visualization**
**Graph 1: Box Plot**
* **ชื่อกราฟ:** ADR by Channel and Day Type
* **การแสดงผล**
   * Columns = Channel Type
   * Rows = ADR
   * Color = Day Type
   * Marks = Box Plot
* **เหตุผลที่เลือกใช้**
   * Box Plot เหมาะสำหรับวิเคราะห์การกระจายตัวของราคา เพราะแสดงค่า median, range, quartile และ outlier ได้ชัดเจน
* **กราฟนี้ช่วยตอบว่า**
   * OTA มี ADR weekday ต่ำกว่า Direct หรือไม่
   * ราคา OTA กระจายตัวมากกว่าช่องทางอื่นหรือไม่
   * มีการใช้ discount ใน weekday หรือไม่

**Graph 2: Scatter Plot with Trend Line**
* **ชื่อกราฟ:** Occupancy vs Net RevPAR by Channel
* **การแสดงผล**
    * X-axis = Occupancy Rate
    * Y-axis = Net RevPAR
    * Color = Channel Type
    * Trend Line = Linear Regression
* **เหตุผลที่เลือกใช้**
    * Scatter Plot เหมาะสำหรับดูความสัมพันธ์ระหว่าง occupancy กับ profitability
    * Trend Line ช่วยให้เห็นว่าเมื่อ occupancy เพิ่มขึ้น Net RevPAR เพิ่มขึ้นเร็วแค่ไหนในแต่ละช่องทาง

**Graph 3: Horizontal Bar Chart**
* **ชื่อกราฟ:** COA% by Channel
* **การแสดงผล**
    * Rows = Channel Type
    * Columns = COA%
    * Label = COA%
    * Color = Channel Type
* **เหตุผลที่เลือกใช้**
    * Horizontal Bar Chart เหมาะกับการเปรียบเทียบต้นทุนระหว่างช่องทาง ช่วยให้เห็นได้ชัดว่า OTA มี acquisition cost สูงกว่าช่องทางอื่นหรือไม่


**6. Hypothesis Testing Criteria**
สมมติฐานนี้จะถือว่า Supported หากพบว่า
* OTA มี ADR ใน weekday ต่ำกว่า Direct
* OTA มี COA% สูงกว่าช่องทางอื่น
* OTA มี Net RevPAR ต่ำกว่า Direct และ Corporate มากกว่า 20%
* Occupancy ของ OTA ไม่สามารถชดเชย margin ที่เสียไปได้

**7. Analysis Results**
ผลการวิเคราะห์พบว่า สมมติฐานนี้ Partially Supported
* OTA มีต้นทุน commission สูงจริง และมีฐานรายได้สุทธิต่ำกว่า Direct ในช่วง occupancy ต่ำ แต่เมื่อ occupancy เพิ่มขึ้น OTA สามารถสร้าง Net RevPAR ได้ดีขึ้น และไม่ได้ด้อยประสิทธิภาพเสมอไป

**8. Sub-Hypothesis Findings**
##### H2.1 OTA มี ADR ต่ำกว่าช่องทางอื่นในวันธรรมดาหรือไม่
ผลลัพธ์พบว่า

| Channel                  | ADR โดยประมาณ                    |
|--------------------------|-----------------------------------|
| Direct                   | 536.17                           |
| OTA                      | 508.10                             |
| Corporate                | 456.95                             |
| Wholesale                | 325.23                            |

* OTA มี ADR ต่ำกว่า Direct แต่สูงกว่า Corporate และ Wholesale
* **Conclusion:** Partially Supported

##### H2.2 Commission Cost ของ OTA สูงกด Net RevPAR หรือไม่
ผลลัพธ์พบว่า

| Channel                  | COA%                  |
|--------------------------|-----------------------------------|
| Agoda                   | 20.48%                          |
| Booking.com                     | 23.25%                            |
| Expedia                | 26.00%                             |
| Direct Website                | 9.97%                            |
| Walk-in                | ≈ 0%                            |
| Corporate GDS               | 7.63%                           |

* OTA มีต้นทุนค่าคอมมิชชันสูงที่สุดในทุกช่องทางอย่างชัดเจนซึ่งเป็นปัจจัยสำคัญที่ทำให้ OTA มีรายได้สุทธิต่อห้องต่ำลง
* **Conclusion:** Supported

##### H2.3 Occupancy ของ OTA ช่วยชดเชยกำไรที่ต่ำหรือไม่
จาก Regression Analysis

| Channel                  | Regression Equation                    |
|--------------------------|-----------------------------------|
| Direct                   | Net RevPAR = 741.705(OCC) - 27.4799                           |
| OTA                      | Net RevPAR = 770.43(OCC) - 173.51                             |

* OTA มี slope สูงกว่า Direct แต่ intercept ต่ำกว่า แปลว่า OTA ต้องเริ่มจากฐานกำไรที่ต่ำกว่า แต่เมื่อ occupancy สูงขึ้น OTA สามารถเพิ่ม Net RevPAR ได้เร็ว
* **Conclusion:** Partially Supported

**9. Key Insights**
1. OTA มีต้นทุน commission สูงมาก
2. ในช่วง occupancy ต่ำ OTA ทำกำไรได้น้อยกว่า Direct
3. OTA ต้องพึ่ง occupancy สูงเพื่อให้คุ้มค่ากับต้นทุน
4. Corporate เป็น segment ที่เหมาะกับ weekday มากกว่า OTA
5. OTA ควรใช้เป็นเครื่องมือเติมห้อง ไม่ใช่ช่องทางหลักถาวร

**10. Business Implications / Recommendations**
1. ใช้ OTA เฉพาะวันที่ occupancy ต่ำ
    * เมื่อ forecast occupancy ต่ำ เช่น ต่ำกว่า 50% ควรเปิด OTA promotion เพื่อเติม demand
2. ลด OTA เมื่อ occupancy เริ่มสูง
    * เมื่อ occupancy สูงขึ้น ควรปิด promotion หรือจำกัดจำนวนห้องที่ขายผ่าน OTA
3. เพิ่ม Corporate Segment ใน weekday
    * Corporate traveler มักเดินทางในวันธรรมดาและมี commission ต่ำกว่า OTA
    * แนวทางที่ควรทำ ได้แก่
        * Corporate contract rate
        * Business package
        * Long-stay package
        * Partnership กับบริษัทในพื้นที่
4. ใช้ Dynamic Channel Allocation
    * ควรแบ่ง inventory ตามระดับ demand เช่น
        * Low OCC → OTA มากขึ้น
        * Mid OCC → OTA + Direct
        * High OCC → Direct + Corporate

#### ขั้นตอนการพิสูจน์ Hypothesis 3: ผลกระทบของ Promo Rate ต่อต้นทุนกำไร (COA%)

**1. Hypothesis Statement**

การจองที่ใช้ Promo Rate โดยเฉพาะผ่านช่องทาง OTA จะมีค่า Cost of Acquisition หรือ COA% สูงกว่าการจองแบบปกติ เนื่องจากรายได้ต่อ booking ลดลงจากส่วนลด แต่ต้นทุน commission ยังถูกคิดตามสัดส่วนของราคาขาย ทำให้ margin ถูกบีบจากทั้งฝั่ง revenue และ cost

**2. Research Objective**

วัตถุประสงค์ของสมมติฐานนี้คือ เพื่อวิเคราะห์ว่า promotion ทำให้ต้นทุนการได้ลูกค้าเพิ่มขึ้นจริงหรือไม่ และช่องทางใดได้รับผลกระทบจาก promotion มากที่สุด

โดยเฉพาะต้องการเปรียบเทียบว่า

* OTA มี COA% สูงเป็น baseline อยู่แล้วหรือไม่
* Promo Rate ทำให้ COA% เพิ่มขึ้นหรือไม่
* Direct Promotion มีความเสี่ยงด้าน profitability หรือไม่

**3. Sub-Hypotheses / Research Questions**
* H3.1 OTA มี COA% สูงกว่าช่องทางอื่นหรือไม่ : เพื่อตรวจสอบ baseline cost ของแต่ละช่องทาง
* H3.2 Commission Rate มีความสัมพันธ์กับ COA% หรือไม่ : เพื่อตรวจสอบว่า commission เป็นตัวแปรหลักที่ผลัก COA%
* H3.3 Promo Rate ทำให้ COA% สูงขึ้นหรือไม่ : เพื่อตรวจสอบผลกระทบของ discount ต่อ profitability

**4. Methodology**
วิเคราะห์ข้อมูลใน 3 มิติ ได้แก่
1. Channel Baseline
    * ตรวจสอบว่าแต่ละช่องทางมี COA% ปกติเท่าไร
2. Commission Relationship
    * ตรวจสอบความสัมพันธ์ระหว่าง Commission Rate และ COA%
3. Rate Type Impact
    * เปรียบเทียบ Promo Rate กับ Non-Promo Rate เพื่อดูผลกระทบของ promotion

**5. Data Visualization**
* **Graph 1: Bar Chart**
* **ชื่อกราฟ:** COA% by Channel
* **การแสดงผล**
    * Columns = Channel Type
    * Rows = COA%
    * Color = Channel Type
    * Label = COA%
* **เหตุผลที่เลือกใช้**
    * Bar Chart เหมาะสำหรับเปรียบเทียบค่า COA% ระหว่างช่องทาง ทำให้เห็นทันทีว่า OTA มีต้นทุนสูงกว่าช่องทางอื่นหรือไม่


**Graph 2: Scatter Plot with Trend Line**
* **ชื่อกราฟ:** Commission Rate vs COA%
* **การแสดงผล**
    * X-axis = Commission Rate
    * Y-axis = COA%
    * Color = Channel Type
    * Detail = Channel Name
    * Trend Line = Linear
* **เหตุผลที่เลือกใช้**
    * Scatter Plot เหมาะสำหรับตรวจสอบความสัมพันธ์ระหว่างตัวแปรเชิงปริมาณ 2 ตัว คือ Commission Rate และ COA%
    * ถ้า trend line ชันขึ้น แปลว่า commission เป็นตัวแปรที่ส่งผลโดยตรงต่อ COA%


**Graph 3: Side-by-Side Bar Chart**
* **ชื่อกราฟ:** Rate Type vs COA% by Channel
* **การแสดงผล**
    * Columns = Is promo และ Channel Type
    * Rows = COA%
    * Color = Channel Type
    * Label = COA%
    * Tooltip = Booking Count
* **เหตุผลที่เลือกใช้**
    * Side-by-Side Bar Chart เหมาะสำหรับเปรียบเทียบ Promo และ Non-Promo ภายใน channel เดียวกัน ทำให้เห็นผลของ promotion ต่อ COA% อย่างชัดเจน


**6. Hypothesis Testing Criteria**
สมมติฐานนี้จะถือว่า Supported หากพบว่า
* OTA มี COA% สูงกว่าช่องทางอื่น
* Commission Rate เพิ่มขึ้นแล้ว COA% เพิ่มขึ้นตาม
* Promo Rate มี COA% สูงกว่า Non-Promo Rate

**7. Analysis Results**
ผลการวิเคราะห์พบว่า สมมติฐานนี้ Supported
* OTA มี COA% สูงกว่าช่องทางอื่นจริง และ Commission Rate มีความสัมพันธ์กับ COA% อย่างชัดเจน นอกจากนี้ Promotion ยังทำให้ COA% เพิ่มขึ้น โดยเฉพาะในช่องทาง Direct ที่ COA% เพิ่มขึ้นอย่างมากเมื่อมีการทำ promotion

**8. Sub-Hypothesis Findings**
#### H3.1 OTA มี COA% สูงที่สุดเมื่อเทียบกับช่องทางอื่นหรือไม่
ผลลัพธ์พบว่า

| Channel                  | COA%                    |
|--------------------------|-----------------------------------|
| OTA                   | 23.29%                           |
| Corporate                      | 7.63%                             |
| Direct                | 6.60%                             |
| Wholesale                | 0.00%                           |

* OTA มี COA% สูงกว่าช่องทางอื่นอย่างชัดเจน
* **Conclusion:** Supported

#### H3.2 Commission Rate มีความสัมพันธ์กับ COA% หรือไม่
* จาก Scatter Plot พบว่า OTA เช่น Booking.com, Agoda และ Expedia มี Commission Rate สูง และมี COA% สูงตามไปด้วย
* ในขณะที่ Direct และ Corporate มี commission ต่ำกว่า จึงมี COA% ต่ำกว่า
* **Conclusion:** Supported

#### H3.3 Promo Rate ส่งผลให้ COA% สูงขึ้นหรือไม่
ผลลัพธ์พบว่า

##### Non-Promotion

| Channel                  | COA%              |
|--------------------------|-----------------------------------|
| Direct                   | 7.78%                         |
| OTA                      | 24.00%                            |
| Corporate                | 7.63%                            |

##### Promotion

| Channel                  | COA%              |
|--------------------------|-----------------------------------|
| Direct                   | 23.11%                         |
| OTA                      | 24.29%                            |

* Direct COA% เพิ่มจาก 7.78% เป็น 23.11%
* OTA COA% เพิ่มจาก 24.00% เป็น 24.29%
* **Conclusion:** Supported

**9. Key Insights**
1. OTA มี COA% สูงเป็น baseline อยู่แล้ว
2. Commission Rate เป็นตัวผลัก COA% ที่สำคัญ
3. Promotion ทำให้ revenue ต่อ booking ลดลง
4. Direct Promotion มีความเสี่ยงสูงกว่าที่คาด เพราะ COA% เพิ่มขึ้นใกล้เคียง OTA
5. การลดราคาอาจทำให้ยอดขายเพิ่ม แต่ไม่จำเป็นต้องทำให้กำไรเพิ่ม

**10. Business Implications / Recommendations**
1. ใช้ OTA อย่างมีกลยุทธ์
    * OTA ยังจำเป็นสำหรับ visibility และ customer acquisition แต่ไม่ควรปล่อยให้เป็นช่องทางหลักของยอดขายทั้งหมด
2. ควบคุม Promotion บน OTA
    * ไม่ควรใช้ deep discount บน OTA เพราะ OTA มี commission สูงอยู่แล้ว เมื่อรวมกับ discount จะทำให้ margin ลดลงมาก
3. ระวัง Direct Promotion
    * Direct ไม่มี commission สูงเหมือน OTA แต่หากใช้ discount มากเกินไปหรือใช้ marketing cost สูง COA% จะเพิ่มขึ้นจนเกือบเท่า OTA
4. ใช้ Value-added Promotion แทน Discount
    * แทนที่จะลดราคา ควรเพิ่มสิทธิประโยชน์ เช่น
        * ฟรีอาหารเช้า
        * Late check-out
        * Room upgrade
        * เครดิตอาหารและเครื่องดื่ม
        * Airport transfer
5. เพิ่ม Corporate Segment
    * Corporate มี COA% ต่ำและช่วยสร้าง weekday demand จึงควรเพิ่ม partnership กับบริษัทต่าง ๆ

#### ขั้นตอนการพิสูจน์ Hypothesis 4: โครงสร้างอัตราราคามีผลต่อ Net Revenue ของโรงแรม

**1. Hypothesis Statement**

อัตราราคาหรือ Rate Code ที่แตกต่างกันส่งผลต่อ Net Revenue และ Net RevPAR ของโรงแรมอย่างมีนัยสำคัญ โดย Rate ที่มี Net RevPAR สูง, Cancellation Rate ต่ำ และ Commission ต่ำ จะสามารถสร้างรายได้สุทธิได้ดีกว่า Rate อื่น

**2. Research Objective**

วัตถุประสงค์ของสมมติฐานนี้คือ เพื่อวิเคราะห์ว่า Rate Code ใดสร้างรายได้สุทธิให้โรงแรมได้ดีที่สุด และ Rate ใดควรถูกเพิ่ม ลด หรือปรับกลยุทธ์ใหม่
สมมติฐานนี้เน้นการประเมิน Rate Strategy เพื่อช่วยให้โรงแรมบริหารราคาขายได้มีประสิทธิภาพมากขึ้น

**3. Sub-Hypotheses / Research Questions**
* H4.1 Rate Code ที่มี Net RevPAR สูง จะสร้าง Net Revenue ได้ดีกว่า Rate อื่นหรือไม่ : เพื่อดูว่า Rate ใดสร้างรายได้สุทธิต่อห้องได้ดีที่สุด 
* H4.2 Rate Code ที่มี Cancellation Rate ต่ำ จะมีคุณภาพ booking ดีกว่าหรือไม่ : เพื่อดูว่า Rate ใดมีความเสี่ยงการยกเลิกต่ำที่สุด 
* H4.3 Rate Code ที่มี Commission ต่ำ จะสร้าง margin ได้ดีกว่าหรือไม่ : เพื่อดูว่า Rate ใดมีต้นทุนต่ำและกำไรสูงกว่า 
* H4.4 Promotional Rate ช่วยเพิ่มยอดขายแต่ลด Net RevPAR หรือไม่ : เพื่อดูว่า Promotion เพิ่ม booking แต่กระทบรายได้สุทธิหรือไม่ 

**4. Methodology**
วิเคราะห์ข้อมูลการจองโดยแบ่งตาม Rate Code จากนั้นเปรียบเทียบ performance ของแต่ละ rate ใน 4 มิติ
1. Revenue Performance
    * ใช้ Net RevPAR เพื่อดูว่า Rate ใดสร้างรายได้ดีที่สุด
2. Demand Performance
    * ใช้ Booking Volume เพื่อดูว่า Rate ใดดึงลูกค้าได้มากที่สุด
3. Booking Quality
    * ใช้ Cancellation Rate เพื่อวัดความเสี่ยงของรายได้
4. Cost Efficiency
    * ใช้ Commission Amount เพื่อดูต้นทุนที่ถูกหักจากรายได้

**5. Data Visualization**
**Graph 1: Bar Chart**
* **ชื่อกราฟ:** Net RevPAR by Rate Code
* **การแสดงผล**
    * Columns = Rate Code
    * Rows = Net RevPAR
    * Sort = Descending
    * Label = Net RevPAR
* **เหตุผลที่เลือกใช้**
    * Bar Chart เหมาะสำหรับเปรียบเทียบ performance ระหว่าง Rate Code หลายกลุ่ม และสามารถเรียงลำดับจากสูงไปต่ำเพื่อให้เห็น rate ที่ดีที่สุดได้ทันที

**Graph 2: Bar Chart**
* **ชื่อกราฟ:** Booking Volume by Rate Code
* **การแสดงผล**
    * Columns = Rate Code
    * Rows = COUNTD(Booking ID)
    * Label = Booking Volume
* **เหตุผลที่เลือกใช้**
    * ใช้ดูว่า Rate Code ใดสร้าง demand สูงสุด และ rate ใดมีการใช้งานน้อย

**Graph 3: Bar Chart**
* **ชื่อกราฟ:** Cancellation Rate by Rate Code
* **การแสดงผล**
    * Columns = Rate Code
    * Rows = Cancellation Rate
    * Label = Cancel %
* **เหตุผลที่เลือกใช้**
    * ใช้วิเคราะห์คุณภาพของ booking เพราะ Rate ที่ cancel สูงอาจสร้างยอดจองเยอะ แต่ไม่สามารถแปลงเป็นรายได้จริงได้ทั้งหมด

**Graph 4: Bar Chart**
* **ชื่อกราฟ:** Commission Amount by Rate Code
* **การแสดงผล**
     * Columns = Rate Code
     * Rows = SUM(Commission Amount)
     * Label = Commission Amount
* **เหตุผลที่เลือกใช้**
     * ใช้ตรวจสอบว่า Rate ใดมีต้นทุน commission สูง และอาจทำให้ Net Revenue ลดลง

**6. Hypothesis Testing Criteria**
สมมติฐานนี้จะถือว่า Supported หากพบว่า
1. Rate Code ที่มี Net RevPAR สูง สร้าง Net Revenue ได้ดีกว่า
2. Rate Code ที่มี Cancellation Rate ต่ำ มี performance ดีกว่า
3. Rate Code ที่มี Commission ต่ำ มี margin ดีกว่า
4. Promotional Rate มี Net RevPAR ต่ำกว่า Rack Rate หรือ Non-Refundable

**7. Analysis Results**
ผลการวิเคราะห์พบว่า สมมติฐานนี้ Supported

* Rate Structure มีผลต่อ Net Revenue อย่างชัดเจน โดย Rack Rate เป็น rate ที่สร้าง Net RevPAR สูงที่สุด ขณะที่ Non-Refundable Rate มีประสิทธิภาพสูงเพราะมี cancellation ต่ำ ส่วน Member Direct Rate มี performance ต่ำที่สุด แม้ไม่มี commission

**8. Sub-Hypothesis Findings**
#### H4.1 Rack Rate เป็น rate ที่สร้างรายได้ดีที่สุดหรือไม่

ผลลัพธ์พบว่า

| Metric                  | Value              |
|--------------------------|-----------------------------------|
| Net RevPAR                   | 140.60                         |
| Booking Volume                      | 5,200                            |
| Commission Amount                | 893,592.70                            |

* Rack Rate เป็นตัวสร้างรายได้หลักของโรงแรม แต่ยังมี commission สูง แสดงว่าบางส่วนของ Rack Rate อาจขายผ่านช่องทางที่มี commission
* **Conclusion:** Supported

#### H4.2 Non-Refundable Rate มีประสิทธิภาพสูงหรือไม่

ผลลัพธ์พบว่า

| Metric                  | Value              |
|--------------------------|-----------------------------------|
| Net RevPAR                   | 71.17                         |
| Booking Volume                      | 2,865                            |
| Cancellation Rate                | 9.21%                            |
| Commission Amount               | 604,506.09                            |

* Non-Refundable มี cancellation ต่ำที่สุด และสร้างรายได้ดีรองจาก Rack Rate
* **Conclusion:** Supported

#### H4.3 Member Direct Rate มี performance ต่ำหรือไม่
ผลลัพธ์พบว่า

| Metric                  | Value              |
|--------------------------|-----------------------------------|
| Net RevPAR                   | 16.83                         |
| Booking Volume                      | 568                            |
| Cancellation Rate                      | 10.92%                            |
| Commission Amount                | 0                            |

* แม้ไม่มี commission แต่ Net RevPAR ต่ำมาก แสดงว่า discount อาจมากเกินไป หรือสิทธิประโยชน์ยังไม่ดึงดูดลูกค้ามากพอ
* **Conclusion:** Supported

#### H4.4 Promotional Rates ช่วยเพิ่มยอดขายแต่ Net RevPAR ต่ำหรือไม่
ผลลัพธ์พบว่า

| Rate Type                  | Net RevPAR              |
|--------------------------|-----------------------------------|
| Seasonal Promo                   | 38.10                         |
| AAA Discount                      | 36.63                            |

* Promo Rate มี Net RevPAR ต่ำกว่า Rack Rate และ Non-Refundable อย่างชัดเจน
* **Conclusion:** Supported

**9. Key Insights**
1. Rack Rate เป็นรายได้หลักของโรงแรม
2. Non-Refundable เป็น rate ที่มี balance ดีระหว่างรายได้และความเสี่ยง
3. Member Direct ยังใช้ศักยภาพไม่เต็มที่
4. Promotional Rate ช่วยเพิ่ม demand แต่ลด Net RevPAR
5. Corporate Flat Rate ช่วยสร้าง base demand ที่มั่นคง
6. โรงแรมยังมี cost leakage จาก commissionable channel
7. Rate Strategy ควรผูกกับ demand level ไม่ใช่ใช้ rate เดียวตลอดเวลา

**10. Business Implications / Recommendations**
1. เพิ่มสัดส่วน Non-Refundable Rate
    * Non-Refundable มี cancellation ต่ำและสร้าง Net RevPAR ดี จึงควรถูกผลักดันในช่วง high demand หรือ early booking
    * แนวทาง
        * แสดง Non-Refundable ให้เด่นบน website
        * ใช้ข้อความ เช่น Best Value หรือ Limited Availability
        * เสนอราคาต่ำกว่า Rack Rate เล็กน้อย
        * ใช้กับ booking ล่วงหน้า

2. ลดการพึ่งพา OTA ที่มี commission สูง
    * แม้ Rack Rate สร้างรายได้สูง แต่ commission amount สูง แสดงว่ารายได้บางส่วนรั่วไหลผ่านช่องทางที่มีค่าคอมมิชชัน
    * แนวทาง
        * จำกัด OTA inventory ช่วง high demand
        * ลด OTA promotion ในวันที่ขายดี
        * ใช้ direct-only benefit เพื่อดึงลูกค้า
        * ทำ remarketing ให้ลูกค้า OTA กลับมาจองตรง

3. ปรับ Member Direct Rate
    * Member Direct ไม่มี commission แต่ Net RevPAR ต่ำสุด จึงควรเปลี่ยนจากการลดราคาเป็นการเพิ่ม value
    * แนวทาง
        * ลด discount
        * เพิ่มสิทธิพิเศษแทน เช่น free breakfast, upgrade, late check-out
        * ทำ membership tier
        * ใช้ personalized offer

4. ใช้ Dynamic Rate Allocation
    * ควรกำหนด rate strategy ตาม demand
        * High Demand → Rack Rate / Non-Refundable
        * Low Demand → Seasonal Promo
        * Shoulder Period → AAA Discount หรือ Limited Promo
        * Weekday → Corporate Flat Rate

5. ขยาย Corporate Segment
    * Corporate Flat Rate ไม่มี commission และให้ demand สม่ำเสมอ โดยเฉพาะ weekday
    * แนวทาง
        * ทำ annual corporate contract
        * เสนอ long-stay package
        * ทำ package ห้องพัก + ห้องประชุม
        * สร้าง partnership กับบริษัทในพื้นที่

#### Overall Conclusion
จากการวิเคราะห์ทั้ง 4 Hypothesis พบว่า ช่องทางการขายและโครงสร้างราคามีผลต่อรายได้สุทธิของโรงแรมอย่างชัดเจน

ภาพรวมสามารถสรุปได้ว่า

1. **OTA ช่วยสร้างยอดจองสูง แต่มีต้นทุนสูง** : OTA เหมาะสำหรับสร้าง visibility และดึงลูกค้าใหม่ แต่ไม่ควรเป็นช่องทางหลักในทุกช่วงเวลา
2. **Direct ให้ margin ดีกว่า แต่ต้องบริหาร promotion อย่างระมัดระวัง** : Direct มีต้นทุนต่ำกว่า OTA แต่หากใช้ deep discount มากเกินไป COA% จะเพิ่มขึ้นอย่างมาก
3. **Corporate เป็น segment ที่ควรขยาย** : เพราะมี commission ต่ำและเหมาะกับ weekday demand
4. **Non-Refundable Rate เป็น opportunity สำคัญ** : เพราะมี cancellation ต่ำและให้ Net RevPAR ดี
5. **Member Direct ต้องปรับกลยุทธ์ใหม่** : เพราะแม้ไม่มี commission แต่ Net RevPAR ต่ำที่สุด
6. **ควรใช้ Dynamic Channel & Rate Strategy** : โดยปรับ channel mix และ rate plan ตาม demand, occupancy และ day type


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

# Findings (Insights)

จากการวิเคราะห์ข้อมูลการจอง รายได้ ต้นทุนค่าคอมมิชชั่น COA% และประสิทธิภาพของแต่ละช่องทาง พบว่า ปัญหาหลักของโรงแรม Azure Stay ไม่ได้เกิดจากการขาด Demand หรือจำนวนลูกค้าไม่เพียงพอ เพราะโรงแรมยังสามารถสร้างยอดจองได้สูง โดยเฉพาะผ่านช่องทาง OTA แต่ปัญหาที่แท้จริงคือ โครงสร้างต้นทุนของช่องทางการขาย (Distribution Cost Structure) ที่ทำให้รายได้สุทธิหลังหักค่าคอมมิชชั่นลดลงอย่างมาก ส่งผลให้ยอดขายสูงไม่ได้แปลว่ากำไรสูงเสมอไป

## 1. โรงแรมพึ่งพา OTA มากเกินไปในการสร้างยอดจอง
* จากการวิเคราะห์ Booking Volume พบว่า OTA เป็นช่องทางที่สร้างยอดจองสูงที่สุด โดยมียอดรวมมากกว่า 23,000 bookings ซึ่งสูงกว่าช่องทาง Direct, Corporate และ Wholesale อย่างชัดเจน โดยเฉพาะ Booking.com, Expedia และ Agoda ที่เป็นแหล่ง demand หลักของโรงแรม
* สิ่งนี้สะท้อนว่า OTA มีบทบาทสำคัญในการเพิ่ม Visibility, Occupancy และ Customer Acquisition ให้กับโรงแรม อย่างไรก็ตาม การพึ่งพา OTA มากเกินไปทำให้โรงแรมต้องเสียค่าคอมมิชชั่นจำนวนมาก และทำให้ต้นทุนการได้ลูกค้าเพิ่มขึ้นตาม volume ที่สูงขึ้น
* **Root Cause:** โรงแรมใช้ OTA เป็นช่องทางหลักในการสร้างยอดขาย แทนที่จะใช้เป็นเพียงเครื่องมือช่วยสร้าง demand และดึงลูกค้าใหม่เข้าสู่โรงแรม

## 2. ค่าคอมมิชชั่นของ OTA เป็นสาเหตุหลักที่ทำให้กำไรสุทธิลดลง
* จากการวิเคราะห์ COA% พบว่า OTA มีต้นทุนการได้ลูกค้าสูงที่สุด โดยมี COA% เท่ากับ 23.29% ขณะที่ Direct มีเพียง 6.60%, Corporate 7.63% และ Wholesale ใกล้เคียง 0%
* นอกจากนี้ เมื่อดู Commission Cost รายช่องทาง พบว่า Booking.com มีต้นทุนค่าคอมมิชชั่นสูงที่สุดประมาณ 870K รองลงมาคือ Expedia ประมาณ 650K และ Agoda ประมาณ 490K ซึ่งทั้งหมดอยู่ในกลุ่ม OTA
* แสดงให้เห็นว่า OTA ไม่ได้เป็นเพียงช่องทางที่สร้างยอดขายสูง แต่ยังเป็นช่องทางที่สร้างต้นทุนสูงที่สุดให้กับโรงแรมด้วย
* **Root Cause:** OTA มี Commission Rate สูง ทำให้รายได้สุทธิหลังหักต้นทุนลดลง แม้ราคาขายก่อนหักค่าคอมมิชชั่นจะใกล้เคียงกับช่องทาง Direct

## 3. OTA สร้าง Volume สูง แต่ Profit Efficiency ต่ำ
* ผลการวิเคราะห์พบว่า Gross ADR ของ OTA ใกล้เคียงกับ Direct แสดงว่าโรงแรมไม่ได้ขายผ่าน OTA ในราคาที่ต่ำกว่ามากนัก แต่เมื่อหักค่าคอมมิชชั่นแล้ว Net ADR ของ OTA ลดลงอย่างชัดเจน
* Direct มี Net ADR ประมาณ 550 ขณะที่ OTA มี Net ADR ประมาณ 420 หรือ OTA ต่ำกว่า Direct ประมาณ 23.6%
* ประเด็นนี้แสดงให้เห็นว่า ปัญหาไม่ได้เกิดจากการตั้งราคาขาย OTA ต่ำเกินไป แต่เกิดจากต้นทุนหลังการขาย โดยเฉพาะค่าคอมมิชชั่นของแพลตฟอร์ม
* **Root Cause:** เกิด Revenue Leakage หลังการขาย เพราะรายได้ส่วนหนึ่งถูกหักออกไปเป็นค่าคอมมิชชั่น ทำให้ยอดขายสูงแต่กำไรต่อ booking ต่ำ

## 4. Direct Channel เป็นช่องทางที่สร้างกำไรต่อ Booking สูงที่สุด
* แม้ Direct Channel จะมียอดจองต่ำกว่า OTA แต่เป็นช่องทางที่ให้ Net ADR สูงที่สุด และมีต้นทุนค่าคอมมิชชั่นต่ำมาก เมื่อเปรียบเทียบ Gross Revenue และ Net Revenue พบว่าทั้งสองค่าใกล้เคียงกันมากในช่องทาง Direct
* แสดงให้เห็นว่า Direct เป็นช่องทางที่มี Profit Margin ต่อ booking สูงที่สุด เพราะโรงแรมสามารถเก็บรายได้ไว้ได้มากกว่า ไม่ต้องแบ่งรายได้ให้ตัวกลางเหมือน OTA
* อย่างไรก็ตาม Direct ยังมี volume ต่ำกว่า OTA อย่างชัดเจน แปลว่ายังมีโอกาสในการเติบโตอีกมาก
* **Root Cause:** Direct Channel ยังไม่ได้ถูกพัฒนาให้เป็นช่องทางหลักด้านกำไร ทั้งที่มีประสิทธิภาพด้าน margin สูงที่สุด

## 5. OTA ทำกำไรได้ดีเฉพาะเมื่อ Occupancy สูง
* จาก Regression Analysis พบว่า OTA มีสมการ
`Net RevPAR = 770.43(OCC) - 173.51`
* ในขณะที่ Direct มีสมการ
`Net RevPAR = 741.705(OCC) - 27.48`
* ค่าดังกล่าวแสดงว่า OTA มี slope สูงกว่า Direct หมายความว่าเมื่อ Occupancy เพิ่มขึ้น OTA สามารถผลักดัน Net RevPAR ได้เร็ว แต่ OTA มี intercept ต่ำกว่ามาก แปลว่าในช่วงที่ Occupancy ต่ำ OTA จะเริ่มต้นจากฐานกำไรที่ต่ำกว่า Direct
* ดังนั้น OTA จะคุ้มค่ามากขึ้นเมื่อใช้ในช่วงที่ต้องการเพิ่ม occupancy หรือเติมห้องว่าง แต่ไม่เหมาะที่จะใช้เป็นช่องทางหลักตลอดเวลา
* **Root Cause:** OTA เหมาะกับบทบาท Occupancy Driver มากกว่า Profit Driver เพราะต้องอาศัย volume สูงเพื่อชดเชยต้นทุนค่าคอมมิชชั่น

## 6. Promotion ทำให้ต้นทุนต่อการจองเพิ่มขึ้นอย่างมาก
* จากการเปรียบเทียบ COA% ระหว่าง Non-Promotion และ Promotion พบว่า Direct มี COA% เพิ่มจาก 7.78% เป็น 23.11% ส่วน OTA เพิ่มจาก 24.00% เป็น 24.29%
* ประเด็นที่สำคัญคือ Direct ซึ่งปกติเป็นช่องทางที่มีต้นทุนต่ำ กลับมี COA% เพิ่มขึ้นจนเกือบเท่ากับ OTA เมื่อมีการใช้ Promotion แสดงว่า Promotion อาจทำให้รายได้ต่อ booking ลดลงมากเกินไป ขณะที่ต้นทุน marketing หรือ acquisition ยังไม่ได้ลดลงตาม
* **Root Cause:** การใช้ Deep Discount Promotion ทำให้รายได้สุทธิต่อ booking ลดลง และทำลายข้อได้เปรียบด้านต้นทุนของ Direct Channel

## 7. โครงสร้าง Rate Plan บางประเภทสร้างรายได้ต่ำเกินไป
* จากการวิเคราะห์ Rate Code พบว่า Rack Rate มี Net RevPAR สูงที่สุดที่ 140.60 รองลงมาคือ Non-Refundable ที่ 71.17 ขณะที่ Seasonal Promo และ AAA Discount มี Net RevPAR เพียง 38.10 และ 36.63 ตามลำดับ ส่วน Member Direct Rate มี Net RevPAR ต่ำที่สุดที่ 16.83
* แสดงให้เห็นว่า Rate Plan มีผลโดยตรงต่อรายได้สุทธิต่อห้อง โดยเฉพาะกลุ่ม Promotional Rate ที่ช่วยเพิ่ม demand แต่ลด Net RevPAR ลงอย่างชัดเจน
* นอกจากนี้ Member Direct Rate แม้ไม่มีค่าคอมมิชชั่น แต่ Net RevPAR ต่ำมาก แปลว่าส่วนลดหรือ benefit อาจถูกออกแบบไม่เหมาะสม
* **Root Cause:** กลยุทธ์ราคาไม่ได้เชื่อมโยงกับระดับ demand, seasonality และต้นทุนของแต่ละ channel อย่างเหมาะสม

## 8. Seasonality ทำให้โรงแรมพึ่งพา OTA แม้ในช่วงที่ Demand สูง
* จาก Seasonality Analysis พบว่า High Season สร้าง Net Room Revenue สูงที่สุดประมาณ 9.6M และ OTA เป็นช่องทางหลักในการสร้างรายได้ในทุกฤดูกาล โดยเฉพาะ High Season ที่ OTA สร้างรายได้มากกว่า 5.8M
* อย่างไรก็ตาม ในช่วง High Season demand ของตลาดสูงอยู่แล้ว โรงแรมอาจไม่จำเป็นต้องพึ่งพา OTA มากเท่ากับช่วง Low Season เพราะการใช้ OTA มากเกินไปในช่วงนี้ทำให้โรงแรมเสียค่าคอมมิชชั่นโดยไม่จำเป็น
* **Root Cause:** โรงแรมยังไม่ได้จำกัดหรือปรับสัดส่วน OTA ตามฤดูกาล ทำให้เสียโอกาสในการเพิ่ม Net Revenue ในช่วงที่ demand สูง

## 9. พฤติกรรมลูกค้าแตกต่างกันตาม Channel และวันในสัปดาห์
* จากการวิเคราะห์ยอดจองรายวัน พบว่า OTA และ Direct มียอดจองเพิ่มขึ้นในช่วงวันเสาร์–อาทิตย์ ซึ่งสะท้อน demand จากกลุ่มลูกค้าท่องเที่ยวหรือ leisure travelers ขณะที่ Corporate Booking มีแนวโน้มสูงในช่วงวันทำงาน ซึ่งสอดคล้องกับพฤติกรรมของลูกค้าธุรกิจ
* Insight นี้แสดงให้เห็นว่าความต้องการของลูกค้าแต่ละกลุ่มไม่ได้เกิดขึ้นในช่วงเวลาเดียวกัน ดังนั้นโรงแรมควรบริหาร channel และ rate plan ให้แตกต่างกันตามวันในสัปดาห์
* **Root Cause:** โรงแรมยังไม่ได้ใช้ Channel Strategy ที่ปรับตาม demand pattern ของลูกค้าแต่ละกลุ่มอย่างชัดเจน

## 10. คุณภาพของ Booking ในแต่ละช่องทางใกล้เคียงกัน
* จากการวิเคราะห์ Booking Status พบว่าอัตรา Checked-Out อยู่ในช่วงประมาณ 52–55% ในทุกช่องทาง และ Cancellation Rate ของ OTA อยู่ที่ประมาณ 9.42% ซึ่งต่ำกว่า Direct ที่ประมาณ 10.29% และ Corporate ที่ประมาณ 10.25% เล็กน้อย
* ดังนั้น OTA ไม่ได้มีปัญหาเรื่อง cancellation สูงกว่าช่องทางอื่นอย่างมีนัยสำคัญ คุณภาพของ booking โดยรวมถือว่าใกล้เคียงกันในทุก channel
* **Root Cause:** ปัญหาหลักของ OTA ไม่ใช่คุณภาพ booking หรือ cancellation แต่เป็นต้นทุนค่าคอมมิชชั่นและ COA% ที่สูงเกินไป

## Overall Root Cause
* จากการวิเคราะห์ทั้งหมด พบว่า ปัญหาหลักของ Azure Stay ไม่ได้อยู่ที่ยอดขายหรือจำนวนลูกค้า เพราะโรงแรมยังสามารถขายห้องพักได้จำนวนมาก โดยเฉพาะผ่าน OTA แต่ปัญหาที่แท้จริงคือ โครงสร้างต้นทุนของช่องทางการขาย ที่ทำให้รายได้สุทธิลดลงหลังจากหักค่าคอมมิชชั่น
* กล่าวคือ โรงแรมมี Volume สูง แต่ Profit ต่อ booking ต่ำ เนื่องจากช่องทางที่สร้างยอดขายมากที่สุดเป็นช่องทางที่มีต้นทุนสูงที่สุด

สาเหตุหลักประกอบด้วย
1. โรงแรมพึ่งพา OTA มากเกินไปในการสร้างยอดขาย
2. Commission Rate ของ OTA สูง ทำให้เกิด Revenue Leakage
3. Direct Channel ยังมีสัดส่วนยอดจองต่ำ ทั้งที่ margin สูง
4. Promotion ทำให้ต้นทุนต่อ booking เพิ่มขึ้น โดยเฉพาะใน Direct Channel
5. Rate Strategy ยังไม่สอดคล้องกับ demand, seasonality และ channel cost
6. โรงแรมยังไม่ได้บริหาร channel mix ตามวันในสัปดาห์และฤดูกาลอย่างเหมาะสม

## Key Strategic Insight
เพื่อให้ Azure Stay สามารถ Maximize Net Revenue ได้ โรงแรมควรเปลี่ยนจากการมองเฉพาะจำนวน booking ไปสู่การบริหาร Profitability per Channel

กลยุทธ์ที่ควรใช้คือ

* ใช้ OTA เป็นเครื่องมือสร้าง demand และ visibility โดยเฉพาะช่วง Low Season หรือช่วงที่ occupancy ต่ำ
* เพิ่มสัดส่วน Direct Booking เพราะเป็นช่องทางที่ให้ Net ADR และ margin สูงที่สุด
* ขยาย Corporate Segment เพื่อเติม demand ในช่วงวันธรรมดา
* ลดการใช้ Deep Discount Promotion ที่ทำให้ COA% สูง
* ปรับ Rate Plan ตาม demand level เช่น ใช้ Rack Rate และ Non-Refundable ในช่วง demand สูง
* ใช้ Dynamic Channel Mix Strategy โดยปรับสัดส่วน OTA, Direct และ Corporate ตาม season, occupancy และ day type

โดยสรุป โรงแรมไม่ควรใช้ OTA เป็นช่องทางหลักตลอดเวลา แต่ควรใช้ OTA อย่างมีกลยุทธ์ และเพิ่มน้ำหนักให้ช่องทางที่สร้าง Net Revenue สูงกว่า เช่น Direct และ Corporate เพื่อยกระดับกำไรสุทธิของโรงแรมในระยะยาว

# Recommendations

จากการวิเคราะห์ข้อมูลพบว่าโรงแรม Azure Stay ไม่ได้ประสบปัญหาด้าน Demand หรือจำนวนลูกค้าที่เข้าพัก เนื่องจากโรงแรมยังสามารถสร้างยอดจองได้จำนวนมาก โดยเฉพาะผ่านช่องทาง OTA อย่างไรก็ตาม ปัญหาที่แท้จริงคือ โครงสร้างต้นทุนของช่องทางการขาย (Distribution Cost Structure) ที่ทำให้โรงแรมต้องเสียค่าคอมมิชชั่นจำนวนมาก ส่งผลให้รายได้สุทธิต่อการจองลดลง
ดังนั้น แนวทางการแก้ไขปัญหาควรมุ่งเน้นไปที่ การเพิ่มสัดส่วนช่องทางที่มี Profit Margin สูง และลดการพึ่งพาช่องทางที่มีต้นทุนสูง พร้อมทั้งปรับกลยุทธ์ด้านราคา การตลาด และการบริหาร Channel Mix ให้สอดคล้องกับ Demand Pattern ของลูกค้าในแต่ละช่วงเวลา

## 1. เพิ่มสัดส่วน Direct Booking เพื่อลดต้นทุนค่าคอมมิชชั่น
จากการวิเคราะห์พบว่า Direct Channel เป็นช่องทางที่มี Net ADR และ Profit Margin สูงที่สุด เนื่องจากไม่มีค่าคอมมิชชั่นจากตัวกลาง ดังนั้นการเพิ่มสัดส่วน Direct Booking จะช่วยลด Revenue Leakage และเพิ่มรายได้สุทธิของโรงแรมได้อย่างมีประสิทธิภาพ

**แนวทางดำเนินการ**

โรงแรมควรลงทุนในการพัฒนา Hotel Website และ Booking Engine ให้มีประสิทธิภาพมากขึ้น เช่น

* ระบบจองที่ใช้งานง่าย รองรับมือถือ และมีขั้นตอนการจองที่รวดเร็ว
* การเชื่อมต่อระบบชำระเงินที่สะดวกและปลอดภัย
* การแสดงโปรโมชั่นหรือข้อเสนอพิเศษสำหรับผู้ที่จองผ่านเว็บไซต์โดยตรง

นอกจากนี้ควรใช้ Digital Marketing Strategy เพื่อเพิ่มจำนวนผู้เข้าชมเว็บไซต์ เช่น

* Search Engine Optimization (SEO)
* Google Hotel Ads
* Social Media Marketing

เพื่อเพิ่ม traffic และ conversion rate ของ Direct Booking

แทนที่จะใช้การลดราคาห้องพักโดยตรง โรงแรมควรใช้ Value-added Benefits เช่น

* Free breakfast
* Late check-out
* Complimentary room upgrade
* Welcome drink

เพื่อสร้างแรงจูงใจให้ลูกค้าจองผ่านเว็บไซต์ของโรงแรม

**ผลลัพธ์ที่คาดหวัง**

* เพิ่ม Net Revenue ต่อ booking
* ลดค่า Commission Cost ที่ต้องจ่ายให้ OTA
* เพิ่ม Customer Loyalty และโอกาสในการกลับมาพักซ้ำ

## 2. ใช้ OTA อย่างมีกลยุทธ์เพื่อสร้าง Demand
OTA มีบทบาทสำคัญในการเพิ่ม Visibility ของโรงแรมในตลาดออนไลน์ และช่วยสร้าง demand จากลูกค้าใหม่ อย่างไรก็ตาม OTA มีค่าคอมมิชชั่นสูง จึงไม่ควรใช้เป็นช่องทางหลักในการขายห้องพัก

โรงแรมควรใช้ OTA เป็น Demand Generator หรือเครื่องมือในการดึงลูกค้าใหม่เข้าสู่โรงแรม แล้วเปลี่ยนลูกค้าเหล่านั้นให้กลับมาจองผ่าน Direct Channel ในครั้งถัดไป

**แนวทางดำเนินการ**

* ใช้ OTA ในช่วงที่ Occupancy ต่ำ หรือ Low Season เพื่อเพิ่มจำนวนการจอง
* จำกัดจำนวนห้อง (Inventory Allocation) ที่ขายผ่าน OTA ในช่วง High Season
* ใช้ Rate Parity Strategy ที่ให้ราคา OTA เท่ากับ Direct แต่เพิ่มสิทธิพิเศษใน Direct

ตัวอย่างเช่น
```
OTA Price = Standard Rate
Direct Price = Standard Rate + Free Breakfast + Late Checkout
```
 
**ผลลัพธ์ที่คาดหวัง**

* ยังคงรักษา Booking Volume จาก OTA
* ลดต้นทุนค่าคอมมิชชั่น
* เพิ่ม Direct Booking ในระยะยาว

## 3. ขยายตลาด Corporate เพื่อเพิ่มรายได้ที่มีต้นทุนต่

จากการวิเคราะห์พบว่า Corporate Channel มี COA ต่ำ (ประมาณ 7.63%) และมี demand ในช่วงวันทำงาน ซึ่งช่วยเพิ่ม occupancy ในช่วง weekday ที่ demand จาก leisure travelers ต่ำกว่า

ดังนั้นโรงแรมควรขยายตลาด Corporate เพื่อเพิ่มรายได้ที่มีต้นทุนต่ำและมีความเสถียร

**แนวทางดำเนินการ**

* ทำ Corporate Contracts กับบริษัทในพื้นที่
* เสนอ Negotiated Corporate Rates
* ทำ partnership กับองค์กรธุรกิจ โรงงาน หรือสำนักงานใกล้โรงแรม
* สร้าง Corporate Loyalty Program

**ผลลัพธ์ที่คาดหวัง**

* เพิ่ม occupancy ในช่วง weekday
* เพิ่มรายได้ที่มีต้นทุนต่ำ
* ลดการพึ่งพา OTA

## 4. ลดการใช้ Deep Discount Promotion
จากการวิเคราะห์ COA% พบว่า Promotion ทำให้ต้นทุนต่อ booking เพิ่มขึ้นอย่างมาก โดยเฉพาะใน Direct Channel ที่ COA% เพิ่มขึ้นจากประมาณ 7.78% เป็น 23.11%

ดังนั้นโรงแรมควรลดการใช้ Deep Discount Strategy ที่เน้นการลดราคา และเปลี่ยนไปใช้ Value-based Promotion

**แนวทางดำเนินการ**

แทนการลดราคา เช่น 20% Discount ควรใช้

* Free breakfast
* Airport transfer
* Spa package
* Dining credit
  
**ผลลัพธ์ที่คาดหวัง**

* รักษาระดับ ADR ของโรงแรม
* ลดการสูญเสียกำไรจากการลดราคา
* เพิ่ม perceived value ของลูกค้า

## 5. ปรับ Rate Strategy ให้สอดคล้องกับ Demand
จากการวิเคราะห์ Rate Code พบว่า Promotional Rate หลายประเภทมี Net RevPAR ต่ำมาก เช่น Seasonal Promo และ AAA Discount

ดังนั้นโรงแรมควรปรับกลยุทธ์ราคาให้สัมพันธ์กับ

* Demand Level
* Seasonality
* Channel Cost
  
**แนวทางดำเนินการ**

* ใช้ Rack Rate และ Non-Refundable Rate ในช่วง High Demand
* จำกัดการใช้ Seasonal Promo ในช่วง High Season
* ปรับ Member Rate ให้เหมาะสมกับต้นทุนจริง
  
**ผลลัพธ์ที่คาดหวัง**

* เพิ่ม Net RevPAR
* ลดการสูญเสียรายได้จากราคาที่ต่ำเกินไป

## 6. ใช้ Dynamic Channel Mix Strategy

โรงแรมควรปรับ Channel Mix ตามสถานการณ์ตลาด เพื่อให้ได้ Net Revenue สูงที่สุด

**ตัวอย่างกลยุทธ์**

* High Season
    * ลด OTA inventory
    * เพิ่ม Direct Booking
* Low Season
    * ใช้ OTA เพื่อเพิ่ม Demand
* Weekday
    * เน้น Corporate Segment
* Weekend
    * เน้น Direct และ OTA สำหรับ Leisure Market

**ผลลัพธ์ที่คาดหวัง**
* เพิ่ม Net Revenue โดยไม่ต้องเพิ่มจำนวนห้องที่ขาย

## 7. ใช้ Data Analytics เพื่อบริหาร Distribution Strategy
เพื่อให้การบริหาร Channel Mix มีประสิทธิภาพ โรงแรมควรใช้ Data Analytics ในการติดตาม performance ของแต่ละช่องทางอย่างต่อเนื่อง

**ตัวชี้วัดสำคัญที่ควรติดตาม**

* Net RevPAR
* Net ADR
* COA%
* Booking Volume by Channel
* Cancellation Rate
  
**ผลลัพธ์ที่คาดหวัง**

* สามารถปรับกลยุทธ์ได้อย่างรวดเร็วตามสภาพตลาด
* ลดความเสี่ยงจากการพึ่งพาช่องทางใดช่องทางหนึ่งมากเกินไป

## Strategic Conclusion

จากการวิเคราะห์ทั้งหมด พบว่า ปัญหาหลักของ Azure Stay ไม่ได้เกิดจากการขาด Demand แต่เกิดจากการพึ่งพาช่องทางที่มีต้นทุนสูงเกินไป โดยเฉพาะ OTA

ดังนั้น กลยุทธ์ในการเพิ่มกำไรควรมุ่งเน้นไปที่

* ลดการพึ่งพา OTA
* เพิ่มสัดส่วน Direct และ Corporate Booking
* ปรับ Rate Strategy และ Promotion Strategy
* ใช้ Data-driven Channel Management

หากโรงแรมสามารถปรับ Channel Mix ได้อย่างเหมาะสม Azure Stay จะสามารถ เพิ่ม Net Revenue และ Profitability ได้โดยไม่จำเป็นต้องเพิ่มจำนวนลูกค้าหรือจำนวนห้องพัก แต่เป็นการเพิ่มประสิทธิภาพของช่องทางการขายแทน


# Presentation Documents 
