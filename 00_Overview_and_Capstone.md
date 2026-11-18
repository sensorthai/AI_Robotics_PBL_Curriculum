# หลักสูตร AI & Robotics (ม.4 – ม.6) รูปแบบ Project-Based Learning (PBL) — ฉบับ Local AI 100%

เอกสารฉบับนี้แตกแผนการสอนจากหลักสูตร **AI & Robotics (ม.4 – ม.6)** (6 ภาคเรียน • 30 หัวข้อ • 240 คาบ) โดยปรับแก้ให้ใช้ **เครื่องมือและโครงสร้างพื้นฐานตามเอกสาร BOQ ภายในโรงเรียน (Local AI 100%)** ทั้งหมด ไม่พึ่งพา Cloud AI หรือบริการคลาวด์ภายนอก

---

## 1. สมมติฐานและสถาปัตยกรรมเครื่องมือ (อ้างอิงเอกสาร BOQ โรงเรียน)

1. **เวลาเรียนต่อคาบ:** 1 คาบ = **50 นาที** (40 คาบ/ภาคเรียน) โดยช่วง **"โครงงานปลายคาบ"** ใช้เวลา **≥ 40% ของคาบ (20–45 นาที)**
2. **จำนวนผู้เรียนและรูปแบบกลุ่ม:** ผู้เรียน **30 คน** แบ่งเป็น **5 กลุ่มปฏิบัติการหลัก** (จัดเตรียมชุดอุปกรณ์กลุ่มไว้ **6 ชุด** สำหรับ 5 กลุ่ม + 1 ชุดครู/สำรอง) ผู้เรียนมี Notebook หรือ Tablet ส่วนตัว
3. **โครงสร้าง Local AI 100% (ไม่ส่งข้อมูลออก Cloud AI):**
   - **AI Server ส่วนกลาง (1 ระบบ):** AMD Ryzen 9 7900, RAM DDR5 128GB, SSD NVMe 2TB, GPU **NVIDIA RTX 3090 24GB** รันบน **Ubuntu Server 24.04 LTS + Docker**
   - **ซอฟต์แวร์บน AI Server:** **Ollama** (Local LLM ขนาด 7B–14B Quantized) + **Open WebUI** (หน้า Chat AI), **JupyterHub** (เขียน Python/DL), **PyTorch**, **OpenCV**, **Label Studio** (ติดป้าย Dataset), **Local Git Server** (เก็บ Source Code)
   - **การจัดคิวใช้งาน GPU/LLM:** เนื่องจาก RTX 3090 24GB รองรับ LLM 7B–14B ได้ดีแต่ไม่เหมาะให้ 30 คนยิงพร้อมกัน จึงใช้วิธี **แบ่ง 5–6 กลุ่มและจัดคิวงาน**
   - **NAS Storage (Synology DS223j + 8TB x 2):** เก็บ Dataset, Source Code, Model, ภาพ/วิดีโอ และสำรองข้อมูลทุกวัน
   - **Network Infrastructure:** Managed Switch + Wi-Fi 6 AP (Dual Band) แยก **VLAN ระหว่าง นักเรียน / AI Server / อุปกรณ์ IoT** พร้อม Firewall
4. **ชุดอุปกรณ์ฮาร์ดแวร์ตลอด 3 ปี:**
   - **บอร์ดหลักประจำตัว (30 ชุด):** **ESP32-S3 DevKitC-1 N16R8** (1 บอร์ด/คน) พร้อม Breadboard 830 Point, สาย Jumper, LED/R/Diode, Button & Buzzer, สาย USB-C Data, และชุดกลุ่ม (Sensor Basic: LDR/IR/Ultrasonic, **OLED I2C 0.96"**, Power Module 5V)
   - **Robotics Kit (6 ชุด):** **4WD Aluminum Chassis**, DC Gear Motor 6V–12V (4 ตัว/คัน), **TB6612FNG Motor Driver**, Ultrasonic HC-SR04, Servo SG90, **Wheel Encoder**, แบตเตอรี่ 18650 + Charging Module, สนามทดสอบ
   - **AI Vision Kit (6 ชุด):** **Webcam Logitech C270**, Tripod, ไฟ LED ถ่ายภาพ, Background Board, สายต่อ USB, Object Sample Kit, External SSD
   - **IoT & Smart Systems Kit (6 ชุด):** **Capacitive Soil Moisture**, **DHT22/AM2302**, **Water Level Sensor**, **Rain Sensor**, **2-Channel Relay**, **DC Water Pump 5V–12V**, OLED I2C, 12V DC Power Supply, ถังทดลอง+สายยาง, กล่องกันน้ำ (Enclosure)
   - **3D Printing (1 เครื่อง):** **Bambu Lab A1 Mini** + PLA Filament สำหรับพิมพ์กล่อง ESP32, ชิ้นส่วนหุ่นยนต์, Sensor Housing, IoT Enclosure และต้นแบบผลิตภัณฑ์
   - **เครื่องมือช่างและความปลอดภัย:** Soldering Station (ครูควบคุมเท่านั้น พร้อมแว่นตานิรภัยและ Fume Extractor), Multimeter, DC Power Supply, Hot Glue Gun

---

## 2. ภาพรวมหลักสูตร 6 ภาคเรียน (240 คาบ)

| ระดับชั้น/ภาคเรียน | ชื่อภาคเรียน | เครื่องมือหลักตาม BOQ | โครงงานรวบยอดประจำภาค | ไฟล์แผนการสอน |
|---|---|---|---|---|
| **ม.4 ภาคเรียนที่ 1** | AI Foundation | Notebook/Tablet, AI Server (Ollama + Open WebUI, JupyterHub), NAS, ESP32-S3 | โปรแกรม Python บน JupyterHub วิเคราะห์ CSV ของห้อง เก็บบน NAS/Local Git | [M4_Term1 Overview](M4_Term1_AI_Foundation/00_Term_Overview.md) |
| **ม.4 ภาคเรียนที่ 2** | AI & Robotics | ESP32-S3 N16R8, OLED, Sensor Kit, 4WD Robot Kit (TB6612FNG, Encoder), JupyterHub (PyTorch/sklearn), 3D Printer | หุ่นยนต์ 4WD / อุปกรณ์อัจฉริยะ ESP32-S3 (เซนเซอร์/Encoder + ตรรกะ/ML) | [M4_Term2 Overview](M4_Term2_AI_and_Robotics/00_Term_Overview.md) |
| **ม.5 ภาคเรียนที่ 1** | AI Vision | AI Server (JupyterHub, PyTorch, OpenCV, Label Studio, RTX 3090), Webcam C270 + Lighting/Board, NAS | ระบบ AI Vision (PyTorch/YOLO/OpenCV) จำแนกภาพ/ตรวจจับวัตถุเรียลไทม์บน LAN | [M5_Term1 Overview](M5_Term1_AI_Vision/00_Term_Overview.md) |
| **ม.5 ภาคเรียนที่ 2** | AIoT & Smart Systems | ESP32-S3, DHT22, Soil/Water/Rain Sensors, 2-Ch Relay, Pump, Docker (MQTT/Dashboard บน AI Server), NAS, 3D Printer | ระบบ Smart Farm / Smart Classroom ครบวงจรบน IoT VLAN พร้อม 3D Enclosure | [M5_Term2 Overview](M5_Term2_AIoT_Smart_Systems/00_Term_Overview.md) |
| **ม.6 ภาคเรียนที่ 1** | AI Innovation | AI Server, Local Git Server, NAS, Bambu Lab A1 Mini 3D Printer, อุปกรณ์ทุกหมวด | Capstone Project ฉบับต้นแบบ (Local AI 100%) พร้อมรายงานการพัฒนา (Sprint 0–3) | [M6_Term1 Overview](M6_Term1_AI_Innovation/00_Term_Overview.md) |
| **ม.6 ภาคเรียนที่ 2** | Future AI Entrepreneur | Local Git Server, NAS, AI Server, Bambu Lab A1 Mini 3D Printer, อุปกรณ์ทุกหมวด | Capstone Project ฉบับสมบูรณ์, Lean Canvas, Portfolio และ Final Presentation | [M6_Term2 Overview](M6_Term2_Future_AI_Entrepreneur/00_Term_Overview.md) |

---

## 3. โครงงานรวบยอดตลอดหลักสูตร (Cumulative Capstone Architecture)

1. **ม.4:** ฝึก Prompt ผ่าน **Open WebUI (Ollama)** และเขียน Python บน **JupyterHub** วิเคราะห์ข้อมูลที่เก็บบน **NAS** → ต่อยอดเป็น **MicroPython บน ESP32-S3** คุม OLED, เซนเซอร์ และขับเคลื่อน **หุ่นยนต์ 4WD (TB6612FNG + Wheel Encoder)**
2. **ม.5:** ใช้ **Webcam C270 + Label Studio + PyTorch + OpenCV** บน **RTX 3090 Server** สร้างระบบ AI Vision → ผสานกับ **DHT22, Capacitive Soil, Water Level, Rain Sensor, 2-Ch Relay, Water Pump** และ **Docker Dashboard** บน IoT VLAN จนได้ระบบ **Smart Farm / Smart Classroom** พร้อมตัวถังที่พิมพ์ด้วย **3D Printer**
3. **ม.6:** ใช้ **Local Git Server + NAS + AI Server + 3D Printer** พัฒนา **Capstone Project** ตั้งแต่ Business/Design Thinking → Sprint 0–5 → ทดสอบผู้ใช้จริง → **Portfolio & Final Presentation** โดยข้อมูล 100% อยู่ภายในเครือข่ายโรงเรียน

---

## 4. ข้อสังเกตและข้อเสนอแนะ (Observations & Recommendations)

1. **การแทนที่เครื่องมือ Cloud ด้วย Local Tools ตาม BOQ:**
   - แทนที่ *ChatGPT/Claude/Gemini* → **Ollama + Open WebUI** (โมเดล 7B–14B Quantized)
   - แทนที่ *Google Colab / TensorFlow / Teachable Machine* → **JupyterHub + PyTorch (`torchvision` / Ultralytics YOLO) + OpenCV** บน RTX 3090
   - แทนที่ *Google Drive / GitHub* → **NAS Storage (Synology DS223j)** และ **Local Git Server**
   - แทนที่ *Google Workspace / Canva* (ซึ่งไม่ได้ระบุใน BOQ) → ใช้ซอฟต์แวร์ออฟฟิศแบบ Local/Offline บน Notebook นักเรียน (เช่น **LibreOffice Calc/Writer/Impress** หรือ **Markdown/Draw.io**) `[เสริม]` เพื่อคงหลักการปิดอินเทอร์เน็ตได้เมื่อจำเป็น
2. **การบริหารคิว AI Server (RTX 3090 24GB):** ในคาบที่ใช้ Local LLM (ม.4/1) หรือฝึก PyTorch Vision (ม.5/1) ให้ใช้งานแบบ **5 กลุ่มปฏิบัติการ (กลุ่มละ 6 คน)** และจัดคิวรันงานตามที่ BOQ แนะนำ
3. **ความปลอดภัยในห้องปฏิบัติการ:** งานบัดกรีด้วย Soldering Station ต้องควบคุมโดยครู พร้อมแว่นตานิรภัยและ Fume Extractor เสมอ และห้ามต่อไฟบ้าน 220V ในห้องเรียน (ใช้ Power Supply 12V DC ตาม BOQ เท่านั้น)
