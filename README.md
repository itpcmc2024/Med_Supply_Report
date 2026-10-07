Med_Supply_Report V2 — Apps Script + GitHub Pages iframe

ไฟล์ในชุด
- Code.gs: อ่านข้อมูลจาก Spreadsheet ID และแท็บ result69; อนุญาต iframe สำหรับหน้า GitHub Pages
- index.html: ตารางรายการ, การ์ดกรองคลัง, กล่องรายละเอียด และกราฟเปรียบเทียบแบบลากวาง/เพิ่มรายการ

ติดตั้ง
1. เปิดโปรเจกต์ Apps Script ของระบบ แล้วแทนที่ Code.gs ด้วยไฟล์ในชุดนี้
2. เพิ่มหรือแทนที่ไฟล์ HTML ชื่อ index แล้ววางเนื้อหาจาก index.html
3. ตรวจ Spreadsheet ID และชื่อแท็บ result69 ใน Code.gs
4. บันทึก แล้วเลือก Deploy > Manage deployments > Edit > New version > Deploy
5. ใช้ URL /exec ของ Deployment เดิมใน iframe บน GitHub Pages
6. หากเปลี่ยนสิทธิ์การเข้าถึง ให้กำหนดตามกลุ่มผู้ใช้งานที่ควรเห็นข้อมูล

คอลัมน์ที่แอปอ่านจากแถวหัวตาราง
icode, n_name, n_unitcost, n_price, sap_oldcode, item_name, warehouse_name,
total_onhand_qty, sum_draw_qty, onhand_plus_draw_qty, unit_cost, sum_draw_value,
hos_qty, qty_diff2, compare_status, active_date

หมายเหตุ
- มูลค่าขาย/มูลค่าคิดเงินคำนวณจาก n_price × hos_qty ตามที่กำหนด
- ตัวกรองเปรียบเทียบคำนวณจาก sum_draw_qty เทียบกับ hos_qty
- การอนุญาต iframe ใช้ XFrameOptionsMode.ALLOWALL ซึ่งเปิดให้ทุกเว็บไซต์ฝังหน้าแอปได้
- เวอร์ชันนี้ยังไม่ได้ติดตั้งหรือ Deploy ในบัญชี Google ของคุณ

--------------------------------------------------------------------------

Med_Supply_Report — แอปแสดงรายการวัสดุการแพทย์ที่มิใช่ยา

ไฟล์ในชุด
- Code.gs: ฝั่ง Apps Script สำหรับอ่านข้อมูลในชีต result69
- index.html: หน้ารายการแบบโต้ตอบ รองรับมือถือ

วิธีติดตั้ง
1. สร้างโปรเจกต์ Apps Script (แนะนำเปิดจากชีตต้นทาง: ส่วนขยาย > Apps Script)
2. วางโค้ด Code.gs ในไฟล์ Code.gs
3. เพิ่มไฟล์ HTML ชื่อ index (ไม่ต้องใส่ .html) แล้ววางเนื้อหาจาก index.html
4. บันทึก แล้วเลือก Deploy > New deployment > Web app
5. ตั้ง Execute as เป็นบัญชีที่มีสิทธิ์อ่านชีต และกำหนดการเข้าถึงให้เหมาะกับผู้ใช้งานในองค์กรก่อน Deploy
6. หลังแก้ Code.gs ให้เลือก Deploy > Manage deployments > Edit > New version > Deploy เพื่อให้ค่าการฝัง iframe มีผลกับ URL /exec เดิม

ข้อกำหนดข้อมูล
- โค้ดเปิดชีตจาก Spreadsheet ID ที่ระบุไว้ใน Code.gs และอ่านแท็บชื่อ result69
- แถวแรกของ result69 ต้องเป็นแถวชื่อคอลัมน์
- ต้องมีคอลัมน์ n_name, icode, item_id, sap_oldcode, total_onhand_qty,
  sum_draw_qty, unit_cost, hos_qty, hos_value, qty_diff, compare_status
- ต้องมีคอลัมน์คลังสินค้า เช่น warehouse, warehouse_name, stock_name หรือ คลังสินค้า
- โค้ดรองรับหัวคอลัมน์ตัวพิมพ์เล็ก/ใหญ่ และเว้นวรรค/ขีด/ขีดล่างต่างกัน
- หาก compare_status ใช้ข้อความสถานะที่ต่างจาก “ตรงกัน / เบิกมากกว่าคิดเงิน /
  คิดเงินมากกว่าเบิก” ให้ปรับฟังก์ชัน classify ใน index.html ให้ตรงกับข้อมูลจริง

หมายเหตุ: เปิด iframe ด้วย XFrameOptionsMode.ALLOWALL เพื่อให้หน้า GitHub Pages ฝังได้ การตั้งค่านี้อนุญาตเว็บไซต์อื่นฝังหน้าแอปได้ด้วย ควรจำกัดสิทธิ์ผู้เข้าถึงข้อมูลใน Deploy ให้เหมาะสม ชุดนี้ยังไม่ได้ติดตั้งหรือเผยแพร่ในบัญชี Google ของคุณ
