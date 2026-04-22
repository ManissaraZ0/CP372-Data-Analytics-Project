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

# Methodology

# Findings (Insights)

# Recommendations

# Presentation Documents 
