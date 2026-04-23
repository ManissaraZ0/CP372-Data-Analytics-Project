# Channel Profitability Optimization for Azure Stay 

# Members
1. นางสาวมณิสรา	แซ่จัน		  รหัสนิสิต 66102010151
2. นายฐิติวัฒน์	ฮาบสุวรรณ		รหัสนิสิต 66102010238
3. นางสาวเอมี่หลุยส์	บราวน์		รหัสนิสิต 66102010572

# Project Canvas

# Background & Pain Points
 Azure Stay เป็นโรงแรมที่ขายห้องพักผ่านหลายช่องทาง เช่น Direct Web, Walk-in และ OTA (เช่น Booking.com, Expedia, GDS) เพื่อเพิ่มยอดจองและอัตราการเข้าพัก
อย่างไรก็ตาม ปัญหาหลักของธุรกิจนี้คือ High Distribution Costs โดยเฉพาะจาก OTA ที่มีการเรียกเก็บ commission ในอัตราสูง แม้ว่าช่องทางเหล่านี้จะสร้าง booking volume ได้มาก แต่กลับทำให้รายได้สุทธิของโรงแรมลดลง

 ผลกระทบคือ โรงแรมอาจมีรายได้รวม (Gross Revenue) สูง แต่กำไรจริงต่ำ เนื่องจากต้นทุนในการได้มาซึ่งลูกค้า (Cost of Acquisition) สูงเกินไป ส่งผลให้ Net Revenue และ Net RevPAR ต่ำกว่าที่ควรจะเป็น เป็นผลจากการที่โรงแรมจัดสรรสัดส่วนของช่องทางการขาย (channel mix) ได้ไม่เหมาะสม โดยพึ่งพาช่องทางที่มีต้นทุนสูงมากเกินไป และไม่ได้ให้ความสำคัญกับช่องทางที่สร้างกำไรสุทธิได้ดีกว่า 
 
 ดังนั้น การวัดผลจากแค่ยอดจองหรือรายได้รวมจึงไม่เพียงพอ โรงแรมจำเป็นต้องวิเคราะห์ Net Revenue และ profitability ของแต่ละช่องทาง เพื่อระบุว่า channel ใดสร้างกำไรได้จริง


# SMART Objectives
เพิ่มรายได้สุทธิหลังหักค่าคอมมิชชั่นของโรงแรมให้ได้ 15% ภายใน 12 เดือน โดยการปรับสัดส่วนของช่องทางการจอง เพิ่มการจองโดยตรง และลดการพึ่งพาช่องทางการจองผ่านตัวแทนจำหน่ายออนไลน์ (OTA) ที่มีค่าคอมมิชชั่นสูง


# Hypothesis & Method

## Hypothesis 1: ช่องทาง OTA สร้างยอดจองสูง แต่มี Net ADR ต่ำที่สุด
**สมมติฐาน**

ช่องทาง OTA เช่น Booking.com และ Expedia แม้จะสร้างจำนวนการจองสูง แต่จะมีค่า Net ADR ต่ำกว่าช่องทาง Direct Website อย่างน้อย 15% เนื่องจากมีอัตราค่าคอมมิชชันสูง แม้ว่า Gross ADR จะใกล้เคียงกัน

## Hypothesis 2: OTA ทำกำไรต่ำในวันธรรมดา (Weekday)
**สมมติฐาน**

ช่องทาง OTA ในวันธรรมดา (วันจันทร์–พฤหัสบดี) จะมีค่า Net RevPAR ต่ำกว่าช่องทาง Walk-in และ Corporate มากกว่า 20% เนื่องจากต้องใช้ส่วนลดราคาและมีค่าคอมมิชชันสูง ในขณะที่ demand โดยรวมต่ำ

## Hypothesis 3: Promo Rate ผ่าน OTA มี COA% สูงผิดปกติ
**สมมติฐาน**

การจองที่ใช้ Promo Rate ผ่านช่องทาง OTA จะมีค่า Cost of Acquisition (COA%) สูงกว่าการจองกลุ่มอื่น เนื่องจากรายได้ต่อการจองลดลงจากโปรโมชั่น แต่ยังคงถูกหักค่าคอมมิชชันจาก OTA


# logical folder structure
```
project-root/
│
├── data/
│   ├── ai_generated/
│   └── other_sources/
│
├── notebooks/
│   └── (Jupyter / Python notebooks)
│
├── dashboards/
│   └── (dashboard files / configs)
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
