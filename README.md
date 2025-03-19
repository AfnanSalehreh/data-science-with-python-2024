# data-science-with-python-2024
Data Science with Python 2023 Course

The process of this work

<img width="500" alt="Screenshot 2568-02-25 at 21 21 10" src="https://github.com/user-attachments/assets/48f08243-2ab4-418f-aa20-d368b2c43397" />

1 CSV Reader


<img width="500" alt="Screenshot 2568-02-25 at 21 20 16" src="https://github.com/user-attachments/assets/facf2f8b-9e77-4d91-b841-953af174b99b" />

2 Statistics


<img width="500" alt="Screenshot 2568-02-25 at 21 21 31" src="https://github.com/user-attachments/assets/6a328527-d9b7-4fad-b918-84389bd46e52" /> 

3 Bar chart

<img width="500" alt="Screenshot 2568-02-25 at 21 21 46" src="https://github.com/user-attachments/assets/80e58635-c47b-4202-aa7e-db153b561988" />

4 Histogram


<img width="500" alt="Screenshot 2568-02-25 at 21 21 58" src="https://github.com/user-attachments/assets/64eb0854-2bdc-4bc7-b9a4-54187212ceab" />

5 Pie Chart

<img width="500" alt="Screenshot 2568-02-25 at 21 22 13" src="https://github.com/user-attachments/assets/aff2963b-a982-4cd9-91a9-3506cac2c005" />

6 Scatter Plot

---
# Project Final 
# การใช้ CRISP-DM ในการพยากรณ์ราคาหุ้น ADVANC ปี 2024

## 1. Business Understanding
บริษัท แอดวานซ์ อินโฟร์ เซอร์วิส จำกัด (มหาชน) (ADVANC) เป็นผู้ให้บริการเครือข่ายโทรคมนาคมที่ใหญ่ที่สุดในประเทศไทย ราคาหุ้นของ ADVANC มีความสำคัญต่อผู้ลงทุนและผู้เกี่ยวข้องในอุตสาหกรรมการสื่อสาร ดังนั้นการทำนายราคาหุ้นล่วงหน้าจึงมีประโยชน์อย่างยิ่งในการช่วยตัดสินใจด้านการลงทุนและการบริหารความเสี่ยง

วัตถุประสงค์ของโปรเจกต์นี้คือ:
- ทำนายราคาหุ้นของ ADVANC ในปี 2024 เพื่อประเมินความแม่นยำของโมเดล
- ทำนายราคาหุ้นในอนาคต (ปี 2025–2026) เพื่อให้แนวโน้มในการวางแผนกลยุทธ์การลงทุน

---

## 2. Data Understanding
**แหล่งข้อมูล:**  
- ข้อมูลราคาหุ้น ADVANC ตั้งแต่ปี 2015 ถึงปี 2023 ได้จาก [Yahoo Finance](https://finance.yahoo.com) ผ่านไลบรารี `yfinance`

**ข้อมูลที่ใช้:**  
- ราคาเปิด (Open)  
- ราคาสูงสุด (High)  
- ราคาต่ำสุด (Low)  
- ราคาปิด (Close)  
- ปริมาณการซื้อขาย (Volume)  

---

## 3. Data Preparation
### 3.1 การทำความสะอาดข้อมูล
- ลบข้อมูลที่มีค่า Missing Values ออก  
- ปรับรูปแบบวันที่ให้สอดคล้องกัน  

### 3.2 การปรับขนาดข้อมูล
- ใช้ `MinMaxScaler` ปรับขนาดข้อมูลในช่วง `[0, 1]` เพื่อให้โมเดลมีประสิทธิภาพในการเรียนรู้  

### 3.3 การสร้างชุดข้อมูลแบบ Time Series
- สร้างฟีเจอร์ **Lag Features** โดยใช้ค่า `Close` ของ 5 วันก่อนหน้า  

### 3.4 แบ่งข้อมูล Train-Test
- แบ่งข้อมูลเป็น Training Set (80%) และ Test Set (20%)  
- ใช้ข้อมูลปี 2024 เป็น Test Set เพื่อประเมินประสิทธิภาพของโมเดล  

---

## 4. Modeling and Training
### ✅ **Linear Regression**  
- ใช้ Linear Regression เพื่อทำนายราคาหุ้น  
- ประเมินผลโดยใช้ Mean Absolute Error (MAE) และ Mean Squared Error (MSE)  

### ✅ **Random Forest**  
- ใช้ Random Forest Regressor เพื่อทำนายราคาหุ้น  
- ประเมินผลโดยใช้ MAE และ MSE  

### ✅ **XGBoost**  
- ใช้ XGBoost เพื่อทำนายราคาหุ้น  
- ประเมินผลโดยใช้ MAE และ MSE  

### ✅ **LSTM (Long Short-Term Memory)**  
- ใช้ LSTM Neural Network เพื่อสร้างโมเดลที่สามารถเรียนรู้ข้อมูล Time Series  
- ปรับพารามิเตอร์:
    - Hidden Units = 50  
    - Activation = ReLU  
    - Optimizer = Adam  
    - Loss Function = Mean Squared Error (MSE)  

---

## 5. การทำนายหุ้น ADVANC ปี 2024
**เปรียบเทียบความแม่นยำของโมเดล (MAPE):**  
- Linear Regression: **{confidence_scores['Linear Regression']:.2f}%**  
- Random Forest: **{confidence_scores['Random Forest']:.2f}%**  
- XGBoost: **{confidence_scores['XGBoost']:.2f}%**  
- LSTM: **{confidence_scores['LSTM']:.2f}%**  

---

## 6. Visualization of Prediction
### 📌 **การแสดงผลราคาหุ้นจริง เทียบกับผลพยากรณ์**  
- เปรียบเทียบราคาหุ้นจริงและราคาหุ้นที่ทำนายได้จากแต่ละโมเดล  
- นำเสนอในรูปแบบกราฟแยกสำหรับแต่ละโมเดลเพื่อให้เห็นแนวโน้มที่ชัดเจน  

### 📌 **การทำนายหุ้นปี 2025–2026**  
- ทำนายราคาหุ้นปี 2025–2026 โดยใช้ข้อมูลล่าสุด  
- แสดงผลในรูปแบบกราฟเพื่อประเมินแนวโน้มในอนาคต  

---

## 7. สรุปผลการวิเคราะห์
- **โมเดล LSTM** มีความแม่นยำสูงสุดในการทำนายราคาหุ้น ADVANC ปี 2024  
- **XGBoost** และ **Random Forest** ให้ผลการทำนายที่แม่นยำรองลงมา  
- การพยากรณ์ปี 2025–2026 ชี้ให้เห็นแนวโน้มการเติบโตในระยะยาวของราคาหุ้น ADVANC  

---

✅ **โมเดลที่มีความแม่นยำสูงสุด:**  
- 🏆 **LSTM** สำหรับข้อมูล Time Series  
- 🏆 **XGBoost** สำหรับการพยากรณ์ในระยะสั้น  
