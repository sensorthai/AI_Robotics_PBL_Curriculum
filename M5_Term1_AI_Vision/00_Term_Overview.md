# ม.5 ภาคเรียนที่ 1: AI Vision (40 คาบ)

**คำอธิบายรายวิชา:** การเรียนรู้เชิงลึกและการวิเคราะห์ภาพ  
**เครื่องมือ/อุปกรณ์:** AI Server (RTX 3090 24GB, Ubuntu 24.04, Docker), JupyterHub, PyTorch, OpenCV, Label Studio, โมเดลสำเร็จรูป (MobileNetV2/YOLO บน PyTorch), Webcam Logitech C270 + Tripod + ไฟ LED + Background Board + Object Sample Kit, NAS Storage / External SSD, Local Web App (Streamlit/Gradio บน LAN)

---

## ตารางสรุปภาพรวม 40 คาบ

| คาบที่ | ชื่อคาบ | แนวคิดหลัก | โครงงานปลายคาบ |
|---|---|---|---|
| 1 | ทบทวน ML Workflow, `pandas` และ `numpy` | ขั้นตอน ML และโครงสร้าง Array ของ `numpy` | สคริปต์ทบทวนโหลด-สำรวจ-แปลงข้อมูลด้วย `pandas`/`numpy` |
| 2 | Classification ด้วย `scikit-learn` (k-NN & Decision Tree) | การฝึกและเทียบ 2 อัลกอริทึมจำแนกบนชุดข้อมูลมาตรฐาน | โน้ตบุ๊กจำแนกชุดข้อมูลมาตรฐาน (เช่น Iris/Wine) |
| 3 | Regression เบื้องต้นและการวัดผล (MAE) | การทำนายค่าตัวเลขต่อเนื่องและ Mean Absolute Error | โมเดลทำนายค่าตัวเลขพร้อมรายงาน MAE |
| 4 | Train/Val/Test, Overfitting และ Cross-Validation | การแบ่งข้อมูล 3 ส่วน และ `cross_val_score` | รายงานเปรียบเทียบโมเดลที่ Fit เกิน vs Cross-Validation |
| 5 | ตั้งค่า JupyterHub (RTX 3090) และทดสอบย่อย ML | การเปิดใช้งาน GPU Runtime และวัดความพร้อม ML | JupyterHub (RTX 3090) Benchmark + ผ่านแบบทดสอบย่อย ML |
| 6 | จาก ML สู่ DL และเซลล์ประสาทเทียม | Perceptron, Weights, Bias, Layers | แบบจำลองโครงข่ายใน สคริปต์จำลองโครงข่ายประสาทเทียมบน JupyterHub + บันทึกผล |
| 7 | โครงข่ายหลายชั้นและ Activation Functions | Hidden Layers, ReLU, Softmax/Sigmoid | โครงข่ายประสาทขนาดเล็กจำแนกข้อมูลอย่างง่าย |
| 8 | Loss Function และ Optimizer (Gradient Descent) | การวัดความผิดพลาดและการปรับน้ำหนักอัตโนมัติ | การทดลองปรับ Learning Rate/Optimizer เพื่อทำนายผล |
| 9 | สร้างโมเดล PyTorch แรก (เช่น MNIST) | Sequential API (`Dense`, `compile`, `fit`) | โมเดล PyTorch จำแนกตัวเลขเขียนมือ MNIST |
| 10 | อ่านกราฟ Loss/Accuracy และประเมินโมเดล PyTorch | การพล็อต Learning Curve เพื่อดูแนวโน้มการเรียนรู้ | แดชบอร์ดกราฟ Loss/Accuracy และทำนายภาพตัวเลขจริง |
| 11 | แก้ Overfitting: Validation & Dropout | Validation Split และเทคนิค Dropout ปิดนิวรอนชั่วคราว | การทดลองเทียบโมเดล Baseline vs Dropout |
| 12 | แก้ Overfitting: Early Stopping & Data Augmentation | การหยุดฝึกอัตโนมัติและการเพิ่มความหลากหลายของภาพ | การทดลอง 3 รูปแบบแก้ Overfitting พร้อมตารางสรุป |
| 13 | รู้จัก CNN: Convolution และ Pooling | การสกัดลักษณะเด่น (Feature Map) และลดขนาดภาพ | โค้ดสร้างชั้น `Conv2D` + `MaxPooling2D` บนภาพตัวอย่าง |
| 14 | สร้างโมเดล CNN จำแนกภาพ | สถาปัตยกรรม CNN (Conv → Pool → Flatten → Dense) | โมเดล CNN จำแนกภาพ 10 คลาส (เช่น Fashion-MNIST/CIFAR) |
| 15 | Transfer Learning ด้วย MobileNet (ตั้งค่าโมเดล) | การนำความรู้จากโมเดลใหญ่มาใช้ซ้ำ (Feature Extraction) | สคริปต์โหลด MobileNet เตรียมพร้อมฝึกกับภาพของตนเอง |
| 16 | ฝึก Transfer Learning กับชุดภาพของตนเอง | Fine-tuning หัวจำแนก (Classifier Head) บนชุดภาพใหม่ | โมเดล MobileNet ที่จำแนกภาพของตนเองได้จริง |
| 17 | ทดสอบปฏิบัติ Deep Learning | การสร้าง ฝึก และรายงานผลโมเดลจำแนกภาพด้วย PyTorch | โมเดลภาพ + รายงานกราฟและ Accuracy ที่รันผ่าน |
| 18 | ภาพดิจิทัล: พิกเซล ช่องสี และ OpenCV เบื้องต้น | พิกเซล RGB/BGR, Grayscale, `cv2.imread` | โปรแกรมอ่าน แสดงข้อมูลมิติ และตัดแต่งภาพด้วย OpenCV |
| 19 | แปลงภาพ: Resize, Crop, Rotate และ Flip | การจัดการขนาดและเรขาคณิตของภาพเพื่อเตรียมเข้า AI | สคริปต์ Preprocessing ปรับขนาดและครอปชุดภาพอัตโนมัติ |
| 20 | แปลงสี ปรับความสว่าง และ Thresholding | Grayscale, Brightness/Contrast และ Binary Threshold | โปรแกรมสแกนเอกสาร/แยกพื้นหลังขาว-ดำด้วย Threshold |
| 21 | ฟิลเตอร์ลดสัญญาณรบกวนและการตรวจจับขอบ (Canny) | Gaussian Blur และ Canny Edge Detection | โปรแกรมตรวจจับขอบวัตถุจากภาพถ่ายจริง |
| 22 | Morphology เบื้องต้น (Erode/Dilate) และ Contours | การแต่งขอบภาพไบนารีและนับจำนวนวัตถุ | โปรแกรมนับจำนวนวัตถุ/เหรียญจากภาพถ่าย |
| 23 | แยกวัตถุตามสีด้วยระบบสี HSV | Hue-Saturation-Value และ `cv2.inRange` | โปรแกรมตรวจจับและติดตามวัตถุตามสี (Color Masking) |
| 24 | ภาพรวมงาน Computer Vision 3 ประเภท | Classification vs Detection vs Segmentation | ตารางวิเคราะห์ระบบ CV จริง 6 ระบบในอุตสาหกรรม |
| 25 | ออกแบบ Dataset ภาพและการถ่ายเก็บข้อมูล | แสง มุมกล้อง ฉากหลัง และกฎความสมดุล | โครงสร้าง Dataset ทีม (เริ่มเก็บภาพ ≥ 50 ภาพ/คลาส) |
| 26 | จัดการ Dataset: ติดป้าย ตรวจสอบ และแบ่ง Train/Val/Test | Data Hygiene และการป้องกัน Data Leakage | Dataset ทีม ≥ 100 ภาพ/คลาส ที่แบ่งโฟลเดอร์พร้อมฝึก |
| 27 | ฝึกโมเดลทีมรอบแรกด้วย Transfer Learning | Data Pipeline (`image_dataset_from_directory`) + MobileNet | โมเดลจำแนกภาพของทีมเวอร์ชัน v1 (Baseline) |
| 28 | ปรับแต่งและบันทึกโมเดลจำแนกภาพของทีม | Data Augmentation + ปรับจูน Learning Rate + Save `.pth` | ไฟล์โมเดล `.pth` เวอร์ชัน v2 พร้อมผลทดสอบ |
| 29 | ประเมินผล: Confusion Matrix, Precision และ Recall | การอ่านค่า Precision/Recall และวิเคราะห์ภาพที่ทายผิด | รายงานวิเคราะห์ Error Analysis จากภาพที่โมเดลทายผิด |
| 30 | ปรับปรุงข้อมูล (Data-Centric AI) และเทรนใหม่ | การแก้ Dataset ตาม Error Analysis เพื่อเพิ่มความแม่นยำ | โมเดลเวอร์ชัน v3 ที่แม่นยำกว่า v1/v2 พร้อมผลเปรียบเทียบ |
| 31 | Object Detection ด้วยโมเดลสำเร็จรูป (YOLO) | Bounding Box, Class Confidence และ Pretrained YOLO | สคริปต์ตรวจจับวัตถุหลายชิ้นในภาพนิ่งด้วย YOLO |
| 32 | Object Detection ในวิดีโอและนับจำนวนวัตถุ | การรัน YOLO บนไฟล์วิดีโอเฟรมต่อเฟรม | วิดีโอผลลัพธ์ที่ตีกรอบและนับจำนวนวัตถุอัตโนมัติ |
| 33 | เชื่อมต่อโมเดลกับเว็บแคมแบบเรียลไทม์ | Capture เฟรมจากเว็บแคม/JupyterHub Camera → Predict | ระบบจำแนก/ตรวจจับภาพแบบเรียลไทม์ผ่านเว็บแคม |
| 34 | สร้างเว็บแอป AI Vision อย่างง่าย (Gradio/Streamlit) | การห่อโมเดลเป็น UI ที่คนทั่วไปอัปโหลดภาพใช้งานได้ | เว็บแอปเดโมระบบจำแนกภาพที่ทดลองใช้งานได้จริง |
| 35 | ความเป็นส่วนตัวของภาพ อคติ Dataset และทดสอบย่อย | Visual Privacy, Dataset Bias + ทดสอบย่อย CV | กรณีศึกษาจริยธรรมภาพ + ผ่านแบบทดสอบย่อย |
| 36 | เสนอโจทย์ Mini Project และวางแผนข้อมูล | การตั้งโจทย์แก้ปัญหาจริง (เช่น แยกขยะ) และแผนเก็บภาพ | ใบเสนอโจทย์ Mini Project + แผนเก็บ Dataset |
| 37 | เก็บและเตรียม Dataset สำหรับ Mini Project | การเก็บภาพจริงให้หลากหลายและทำความสะอาด Dataset | ชุดข้อมูลจริงของทีม (พร้อม Split) ตรวจสอบแล้ว |
| 38 | ฝึกและประเมินโมเดล Mini Project (Checkpoint 1) | เทรนรอบแรก วิเคราะห์ Confusion Matrix และจูน | โมเดล Mini Project ที่ทำงานได้ + รายงานผล Checkpoint 1 |
| 39 | ปรับปรุงโมเดลและสร้างหน้าจอใช้งานจริง (Checkpoint 2) | เทรนปรับปรุง + เชื่อมเว็บแคม/Gradio/Streamlit | ระบบ AI จำแนกภาพฉบับสมบูรณ์พร้อมซ้อมสาธิต |
| 40 | Demo Day: นำเสนอและประเมินระบบ AI จำแนกภาพ | การสาธิตสดและประเมินผลตามรูบริก | เดโมระบบ AI จำแนกภาพ 3 นาที + รายงานผล |

---

## โครงงานรวบยอดประจำภาคเรียน
**ระบบ AI จำแนกภาพที่ใช้งานได้จริง** (เช่น ระบบแยกประเภทขยะจากภาพถ่าย, ตรวจจับป้าย/วัตถุ, หรือคัดกรองผลผลิต) โดย:
- ใช้พื้นฐาน ML & Validation จาก **Unit 1 (คาบ 1–5)**
- ใช้ Deep Learning, CNN และ Transfer Learning (MobileNet) จาก **Unit 2 (คาบ 6–17)**
- ใช้เทคนิคเตรียมภาพ OpenCV จาก **Unit 3 (คาบ 18–23)**
- ใช้การจัดการ Dataset, Error Analysis, YOLO และ UI แอปอย่างง่ายจาก **Unit 4 (คาบ 24–35)** มาประกอบเป็น **Mini Project (คาบ 36–40)**
