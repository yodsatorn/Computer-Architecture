# Computer-Architecture
## สรุปเนื้อหา

**Computer Organization**
   - ส่วนประกอบของ Computer ประกอบไปด้วย 1. CPU (Central Processing Unit) 2 .I/O (Input,Output) 3 .Main Memory
   - ส่วนประกอบของ CPU      ประกอบไปด้วย 1. ALU (Arithmetic Logic Unit) 2. Control Unit 3. Register


**MIPS Instruction format** : มีทั้งหมด 3 ประเภท และทุกคำสั่งมีขนาด 32 bit

**R-format** : เป็นคำสั่งเกี่ยวกับการคำนวณทั้งทางคณิตศาสตร์และตรรกศาสตร์ (Math and Logic)

| R-Format |  |  |  |  |  |  
| --------- | --------- | --------- | --------- | --------- | --------- |
| op | rs | rt| rd | shamt | func |

| คำสั่ง |  |
| --------- | --------- |
| ALU | alu $rd,$rs,$rt |
| jr | jr $rs |

**I-format** : เป็นคำสั่งประเภทการTransferข้อมูล

| I-Format |  |  |  |
| --------- | --------- | --------- | --------- |
| Op | rs | rt| value or offset |   

| คำสั่ง |  |
| --------- | --------- |
| ALUi | alui $rt,$rs,value |
| Data Transfer | lw $rt,offset($rs) |
|  | lw $rt,offset($rs) |
| Branch | beq $rs,$rt,offset |

**J-format** : เป็นคำสั่งประเภทที่ให้Jumpไปทำงานที่ตำแหน่งอื่น

|J-Format |  |
| --------- | --------- |
| op | absolute address | 

| คำสั่ง |  |
| --------- | --------- |
| Jump | j address |
| Jump&Link | jal address |

**Von Neuman & Harvard Architectures**
   - Von Neuman Architecture : เป็นสถาปัตยกรรมคอมพิวเตอร์ที่มี Memory

________________________________________________________________________________________________________________________________________

*  [CLIP 1](https://youtu.be/8yf97kqEWS8)

   * อธิบายเกี่ยวกับคำสั่ง ADD ใน MIPS โดยเปลี่ยนรูปแบบคำสั่งแบบที่มนุษย์เข้าใจ ไปเป็นภาษาแบบที่คอมพิวเตอร์เข้าใจ โดยแปลรูปแบบไปเป็น binary 32 bit

* [CLIP 2](https://youtu.be/UWN1qYOEa64)

  * อธิบายการทำงานของ MIPS CPU ตั้งแต่เปิดเครื่องขึ้นโดยตำแหน่งRegister แรกเมื่อเปิดเครื่องอาจจะอยู่ที่ตำแหน่ง Register 0 และจะมีการเปลี่ยนตำแหน่งRegisterไปเมื่อมีการทำงานในคำสั่งต่อๆไป

* [CLIP 3](https://youtu.be/rQwzcYdYeCE)

  * อธิบายความแตกต่างกันของ CPU แบบ Single-cycle และ Multi-cycle ที่แตกต่างกันอย่างชัดเจนก็จะเป็น เวลาในการทำงานของคำสั่งต่างๆ โดยที่แบบ Single-cycle นั้นทุกคำสั่งจะใช้เวลาเท่ากัน มี ALU 3 ตัว และมี Memory 1 ตัว แต่แบบ Multi-cycle แต่ละคำสั่งจะใช้เวลาในการทำงานไม่เท่ากัน มี ALU 1 ตัว และมี Memory 2 ตัว

* [CLIP 4](https://youtu.be/CVvfJFUkybk)
 
  * อธิบายขั้นตอนการทำงานของคำสั่ง lw ใน CPU แบบ Multi-cyle ซึ่งเป็นคำสั่งที่เป็นการโหลดข้อมูลมาเก็บไว้ใน Register โดยที่คำสั่ง lw จะมีStepในการทำงานอยู่ 5 Step 

* [CLIP 5](https://youtu.be/y_5s8D-EJ9o)

  * อธิบายขั้นตอนการทำงานของคำสั่ง beq ใน Multi-cycle CPUซึ่งจะทำการเปรียบเทียบค่าสองค่าว่าเท่ากันหรือไม่ โดยคำสั่ง beq นั้นจะมี Step ในการทำงานอยู่ 3 Step

* [CLIP 6](https://youtu.be/Pz49OCkp3S4)

  * อธิบายเกี่ยวกับ State Machine ของคำสั่ง R-Format ในMIPS

* [CLIP 7]

* [CLIP 8]

* [CLIP 9]
________________________________________________________________________________________________________________________________________
