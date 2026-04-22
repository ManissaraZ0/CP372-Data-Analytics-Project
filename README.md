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

# Findings (Insights)

# Recommendations

# Presentation Documents 
