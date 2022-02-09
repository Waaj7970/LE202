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

1)เราจะเขียนโปรแกรมในmicrocontroller และใช้ platformio เพื่ออัปโหดโปรอกรมลงในmicrocontroller ใช้ pio device monitor เพื่อแสดงผลลัพธ์

2)อัปโหลดโปรแกรมเสร็จแล้วให้ setup(set wifi)และใช้คำสั่ง pio device monitor เพื่อแสดงผล wifi ที่เจอ

3)เสียบ input port และ output port เพื่อดูการแสดงผลของ input และ output ที่จะนำไปใช้กับหลอด LED โดยที่เกิด loop เปิดปิดทำให้หลอดไฟกระพริบ

4)โปรแกรม set ให้ port 0 = input และถ้าอ่าน port 0 ไฟติด อ่าน port 1 ไฟดับ แล้วต่อ censor light โดยเจอแสงไฟติด(อ่านport 0)

5)wifi จะใส่ SSID และ password โดน setup ระบุเชื่อม wifi โดยเช็คการทำงานที่ web browser

6)ส่วน wifi moblie ต้องมีการกำหนด gatway และ web browser โดย IP และ password ที่อัปโหลดในโปรแกรม
