# digital

สัญญาณรับข้อมูลเป็นเลขฐาน 2 คือ 0 และ 1 โดย 0 v คือเลข 0 และ 0-5 v คือ 1

# voltage

แรงดันไฟฟ้ากระแสตรงและกระแสสลับ

# computer

การวิวัฒนาของคอมพิวเตอร์

# internet

เชื่อมโยงเครือข่ายๆต่างๆทั้งแบบมีสายและไร้สาย

# program lang

เป็นภาษาของคอมพิวเตอร์ เช่น java c c+ c++ python

# platformio

micro controller มีขนาดเล็กที่จำนวนมาก

แต่ละแบบมีวิธีการพัฒนาต่างกันตามแบบของมัน

io คือมาตราฐาน sorfwearแบบเปิดที่ใช้เขียน microcontrollerหลายแบบ

ในท้องตลาดมีมากกว่า900แบบที่สามารถเอาไปพัฒนาต่อยอดได้

# ESP-01

1)เราจะเขียนโปรแกรมในmicrocontroller และใช้ platformio เพื่ออัปโหดโปรอกรมลงในmicrocontroller

2)อัปโหลดโปรแกรมเสร็จแล้วให้ setup(set wifi)โปรแกรมจะแสกนหาและแสดงผล wifi ที่เจอ

3)input port และ output port เมื่อเสียบ USB ที่คอมพิวเตอร์ขอ io 0 แล้วนำไปเข้าโปรแกรมในตย.3จะเกิด output วน loop

4)โปรแกรม set ให้ port 0 = input และ 2 = output และวน loop โดยข้อมูลจาก port 0 = 1 ส่งไที่ port 2  ดังนั้น input port 0 = ทำให้ไฟสว่าง

5) wifi จะใช้ username และ password โดน setup ระบุเชื่อม wifi โดยเข้า web browser

6)ส่วน wifi moblie ต้องมีการกำหนด gatway และ web browser โดย IP และ password ที่อัปโหลดในโปรแกรม
