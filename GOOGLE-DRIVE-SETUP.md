# ตั้งค่า Google Drive ฟรี

เจ้าของเว็บต้องตั้งค่า OAuth ครั้งแรกเอง ไม่ต้องสร้าง API key หรือส่ง Client Secret ให้ใคร

1. เปิด https://console.cloud.google.com/ และสร้างโปรเจกต์ฟรี ไม่ผูก Billing หรือเปิด Free Trial หากระบบบังคับ Billing ให้หยุด
2. APIs & Services → Library → Google Drive API → Enable
3. Google Auth Platform / OAuth consent screen → ตั้งชื่อแอปและอีเมลติดต่อ → Audience: External หากอยู่สถานะ Testing เพิ่มบัญชี Google ของคุณเป็น Test user (เพิ่มคนรู้จักเป็นผู้ทดสอบด้วยหากจะให้เชื่อม)
4. Data Access / Scopes → เพิ่ม https://www.googleapis.com/auth/drive.appdata เท่านั้น
5. Clients / Credentials → Create OAuth client → Web application
6. Authorized JavaScript origins ใส่ https://projectkeerati-tech.github.io เท่านั้น ไม่มี /tree-ledger/ ไม่มีเครื่องหมาย / ปิดท้าย
7. คัดลอก Client ID ที่ลงท้าย .apps.googleusercontent.com นี่เป็นข้อมูลสาธารณะของเว็บ ไม่ใช่ Client Secret ห้ามส่ง Client Secret หรือรหัสผ่านในแชต
8. เปิดแอป → สำรอง Google Drive → วาง Client ID → เชื่อม Google → อนุญาตพื้นที่เฉพาะแอป
9. อีกเครื่องใช้บัญชี Google เดียวกันและ Client ID เดียวกัน กดกู้คืนจาก Drive เลือกไฟล์ของเครื่องต้นทาง ตรวจจำนวนและยืนยัน ระบบรวมข้อมูล ไม่เขียนทับสมุดทั้งหมด

สำรองอัตโนมัติหลังแก้ไขเมื่อแอปเปิด ออนไลน์ และ access token ใช้งานได้เท่านั้น ปิดแอปหรือ token หมดอายุจะต้องเชื่อมใหม่ ไม่มี backend เก็บ refresh token และไม่รับประกันเบื้องหลัง iOS

แอปเก็บหนึ่งไฟล์ล่าสุดต่อรหัสอุปกรณ์ใน appDataFolder แยกไฟล์แต่ละเครื่องเพื่อไม่ทับกัน ไม่ใช่การซิงก์/แก้ข้อมูลพร้อมกันแบบเรียลไทม์ ข้อมูลบน Drive เป็น JSON ไม่เข้ารหัส แต่การเชื่อมต่อใช้ HTTPS และสิทธิ์บัญชี Google ของคุณ ยังควรเก็บไฟล์ JSON สำรองใน Files อีกทาง

คนรู้จักต้องผ่านการอนุญาตของ OAuth โปรเจกต์ หากแอปอยู่ Testing ใช้งานได้เฉพาะ Test users ตามข้อจำกัด Google หากต้องเผยแพร่ OAuth ให้บุคคลทั่วไป อาจต้องจัดทำหน้า privacy policy/ตั้งค่าความยินยอม/ยืนยันตามที่ Google กำหนด ห้ามข้ามหน้าคำเตือนความปลอดภัย

อ้างอิง:
https://developers.google.com/identity/oauth2/web/guides/use-token-model
https://developers.google.com/workspace/drive/api/guides/appdata
