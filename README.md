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
   - Von Neuman Architecture : เป็นสถาปัตยกรรมคอมพิวเตอร์ที่มี Memory ที่เก็บทั้ง Instruction และ Data อยู่ภายใน Memory เดียวกันทำให้มีพื้นที่ในการเก็บข้อมูลมาก
   - Harvard Architecture : เป็นสถาปัตยกรรมคอมพิวเตอร์ที่มี Memory แยกเก็บส่วน Instruction และ Data ไม่ได้อยู่ภายใน Memory เดียวกันทำให้มีประสิทธิภาพในการรับส่งข้อมูลที่รวดเร็ว
   
**CISC & RISC**
   * CISC ย่อมาจาก Complex instruction set computer : เป็นคอมพิวเตอร์ที่มีชุดคำสั่งซับซ้อน
      * ทุกชุดคำสั่งจะต้องมี Reference ถึง Memory
      * Program code มีขนาดเล็ก
      * รูปแบบชุดคำสั่งมีหลากหลาย
      * มี Register ชุดเดียว
      * ชุดคำสั่งเป็นแบบ Multi-cycle
   * RISC ย่อมาจาก Reduced instruction set computer : เป็นคอมพิวเตอร์ที่มีชุดคำสั่งน้อย
      * มีเพียงคำสั่ง Load และ Store ที่มี Reference ถึง Memory
      * Program code มีขนาดใหญ่
      * รูปแบบชุดคำสั่งตายตัว
      * มี Register ชุดเดียว
      * ชุดคำสั่งเป็นแบบ Single-cycle
      
 **Single-cycle & Multi-cycle**
   * Single-cycle processor : เป็นคอมพิวเตอร์ที่มีการประมวลผลคำสั่งแต่ละคำสั่งจบใน 1 รอบ หรือ 1 Clock cycle ซึ่งทุกคำสั่งจะใช้เวลาในการประมวลผลเท่ากัน
   * Multi-cycle processor  : เป็นคอมพิวเตอร์ที่มีการประมวลผลคำสั่งแต่ละคำสั่งไม่ได้จบใน 1 รอบ หรือ 1 Clock cycle ซึ่งแต่ละคำสั่งใช้เวลาในการประมวลผล หรือ Clock cycle ไม่เท่ากัน 
   
 **Pipelining**
   * เป็นการประมวลผลชุดคำสั่งที่มีความรวดเร็วกว่า Single-cycle และ Multi-cycle 

________________________________________________________________________________________________________________________________________

### การบ้านครั้งที่ 1

**คำสั่ง ADD Instruction ใน MIPS

คำสั่ง ADD ใน MIPS โดยเปลี่ยนรูปแบบคำสั่งแบบที่มนุษย์เข้าใจ ไปเป็นภาษาแบบที่คอมพิวเตอร์เข้าใจ โดยแปลงรูปแบบไปเป็นคำสั่งแบบ binary 32 bit

รูปแบบคำสั่งที่มนุษย์เข้าใจคือ : add $rd,$rs,$rt หมายความว่าให้นำค่าจาก $rs + $rt แล้วนำไปเก็บไว้ที่ $rd

ตัวอย่าง : add $4,$3,$2 

| op | rs | rt| rd | shamt | func |  
| --------- | --------- | --------- | --------- | --------- | --------- |
| 000000 | 00011 | 00010 | 00100 | 00000 | 100000 |

จะได้คำสั่งเป็น 000000 00011 00010 00100 00000 100000 : 32 bit โดยเป็นเลขฐาน 2
ซึ่งสามารถเปลี่ยนเป็นเลขฐาน 16 เป็น 00622020

### ส่งการบ้านครั้งที่ 1

[CLIP 1 "ADD" MIPS Instruction ](https://youtu.be/8yf97kqEWS8)
   
### การบ้านครั้งที่ 2

**การทำงานของ CPU**
|การทำงานของ MIPS CPU ตั้งแต่เปิดเครื่องขึ้นโดยตำแหน่งRegister แรกเมื่อเปิดเครื่องอาจจะอยู่ที่ตำแหน่ง Register 0 และจะมีการเปลี่ยนตำแหน่งRegisterไปเมื่อมีการทำงานในคำสั่งต่อๆไป|
[CLIP 2](https://youtu.be/UWN1qYOEa64)



* [CLIP 3](https://youtu.be/rQwzcYdYeCE)

  * อธิบายความแตกต่างกันของ CPU แบบ Single-cycle และ Multi-cycle ที่แตกต่างกันอย่างชัดเจนก็จะเป็น เวลาในการทำงานของคำสั่งต่างๆ โดยที่แบบ Single-cycle นั้นทุกคำสั่งจะใช้เวลาเท่ากัน มี ALU 3 ตัว และมี Memory 1 ตัว แต่แบบ Multi-cycle แต่ละคำสั่งจะใช้เวลาในการทำงานไม่เท่ากัน มี ALU 1 ตัว และมี Memory 2 ตัว

* [CLIP 4](https://youtu.be/CVvfJFUkybk)
 
  * อธิบายขั้นตอนการทำงานของคำสั่ง lw ใน CPU แบบ Multi-cyle ซึ่งเป็นคำสั่งที่เป็นการโหลดข้อมูลมาเก็บไว้ใน Register โดยที่คำสั่ง lw จะมีStepในการทำงานอยู่ 5 Step 

* [CLIP 5](https://youtu.be/y_5s8D-EJ9o)

  * อธิบายขั้นตอนการทำงานของคำสั่ง beq ใน Multi-cycle CPUซึ่งจะทำการเปรียบเทียบค่าสองค่าว่าเท่ากันหรือไม่ โดยคำสั่ง beq นั้นจะมี Step ในการทำงานอยู่ 3 Step

* [CLIP 6](https://youtu.be/Pz49OCkp3S4)

  * อธิบายเกี่ยวกับ State Machine ของคำสั่ง R-Format ในMIPS

* [CLIP 7]


________________________________________________________________________________________________________________________________________
