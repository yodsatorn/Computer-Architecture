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
   
 **Pipeline**
   * เป็น Memory ที่เก็บเฉพาะคำสั่ง และจะมีการลำดับคำสั่งให้ใช้เวลาในการประมวลผลน้อยลง

________________________________________________________________________________________________________________________________________

### การบ้านครั้งที่ 1

**คำสั่ง ADD Instruction ใน MIPS**

คำสั่ง ADD ใน MIPS โดยเปลี่ยนรูปแบบคำสั่งแบบที่มนุษย์เข้าใจ ไปเป็นภาษาแบบที่คอมพิวเตอร์เข้าใจ โดยแปลงรูปแบบไปเป็นคำสั่งแบบ binary 32 bit

รูปแบบคำสั่งที่มนุษย์เข้าใจคือ : add $rd,$rs,$rt หมายความว่าให้นำค่าจาก $rs + $rt แล้วนำไปเก็บไว้ที่ $rd

ตัวอย่าง : add $4,$3,$2 

| op | rs | rt| rd | shamt | func |  
| --------- | --------- | --------- | --------- | --------- | --------- |
| 000000 | 00011 | 00010 | 00100 | 00000 | 100000 |

6 bit แรกจะเป็น Opcode จะเป็นตัวบอกว่าเป็นคำสั่งประเภทอะไร
<br>5 bit ต่อมาจะเป็นตำแหน่ง Register ตัวแรกที่จะนำมาประมวลผล
<br>5 bit ต่อมาจะเป็นตำแหน่ง Register ตัวที่สองที่จะนำมาประมวลผล
<br>5 bit ต่อมาจะเป็นตำแหน่ง Register ตัวที่เก็บค่าที่ได้จากการนำ Register ตัวแรกและตัวที่สองมาประมวลผลกัน
<br>5 bit ต่อมาคือ Shift amount
<br>6 bit สุดท้ายคือ Fucntion ซึ่งจะเป็นตัวบอกว่าคำสั่งนี้จะให้ทำอะไร

จะได้คำสั่งเป็น 000000 00011 00010 00100 00000 100000 : 32 bit โดยเป็นเลขฐาน 2
<br>ซึ่งสามารถเปลี่ยนเป็นเลขฐาน 16 เป็น 00622020

สามารถดูOpcode และ Functionได้จากรูป ALU Decoder

![image1](https://www.cise.ufl.edu/~mssz/CompOrg/Table4.3-MIPSdatapath-control.gif)

![image2](https://www.cise.ufl.edu/~mssz/CompOrg/Table4.2-MIPSdatapath-ALUcontrol.gif)


### ส่งการบ้านครั้งที่ 1

[CLIP 1 : "ADD" MIPS Instruction ](https://youtu.be/8yf97kqEWS8)
   
________________________________________________________________________________________________________________________________________

### การบ้านครั้งที่ 2

**การทำงานของ CPU**
การทำงานของ MIPS CPU ตั้งแต่เปิดเครื่องขึ้นโดยตำแหน่งRegister แรกเมื่อเปิดเครื่องอาจจะอยู่ที่ตำแหน่ง Register 0 และจะมีการเปลี่ยนตำแหน่งRegisterไปเมื่อมีการทำงานในคำสั่งต่อๆไป

**ตัวอย่าง** 

==Java Language== (คำสั่งในภาษา Java แบบที่มนุษย์เข้าใจ)

<br>...
<br>int a = 10;
<br>int b = 20;
<br>int c = a + b;
<br>...

==Machine Language== (ภาษาที่คอมพิวเตอร์เข้าใจ)

| ตำแหน่ง Register | คำสั่ง | | |
| --------- | --------- | --------- | --------- |
| 00000000 | 08400000 | //jump | ที่ Register ตำแหน่ง 00000000 มีคำสั่ง jump |
| 00000004 | 1A000000 | //data | ที่ Register ตำแหน่ง 00000004 มีข้อมูลเก็บอยู่ |
| 01000000 | 8C090004 | //lw $9,$0(4) | ที่ Register ตำแหน่ง 01000000 มีคำสั่ง Load ข้อมูล |
| 01000004 | 8D210000 | //lw $1,$9(0) | ที่ Register ตำแหน่ง 01000004 มีคำสั่ง Load ข้อมูล |
| 01000008 | 8D220004 | //lw $2,$9(4) | ที่ Register ตำแหน่ง 01000008 มีคำสั่ง Load ข้อมูล |
| 0100000C | 00221820 | //add $3,$1,$2 | ที่ Register ตำแหน่ง 0100000C มีคำสั่ง ADD |
| 01000010 | AD230008 | //sw $3,$9(8) | ที่ Register ตำแหน่ง 01000010 มีคำสั่ง Store ข้อมูล |
| 1A000000 | 0000000A | //a | |
| 1A000004 | 00000014 | //b | |
| 1A000008 | 0000001E | //c | |

### ส่งการบ้านครั้งที่ 2

[CLIP 2 : CPU MIPS Processing](https://youtu.be/UWN1qYOEa64)

________________________________________________________________________________________________________________________________________

### การบ้านครั้งที่ 3

**Single-cycle vs. Multi-cycle**

| Single-cycle | Multi-cycle |
| --------- | --------- |
| มี ALU 3 ตัว | มี ALU 1 ตัว |
| ทำงานจบใน 1 cycleต่อคำสั่ง | 1 คำสั่งไม่ได้ทำงานจบได้ใน 1 cycle |
| มี Memory 2 ตัว | มี Memory 1 ตัว |
| ทุกคำสั่งใช้เวลาในการประมวลผลเท่ากัน | แต่ละคำสั่งใช้เวลาในการประมวลผลไม่เท่ากัน |

- Single-cycle

![image3](https://i.stack.imgur.com/vCvw1.png)

- Multi-cycle 

![image4](https://camo.githubusercontent.com/3a759f503101d7359e3b9e88a79a64b022814d5a/68747470733a2f2f692e696d6775722e636f6d2f6d5758485770542e706e67)

### ส่งการบ้านครั้งที่ 3

[CLIP 3 : Comparison of Single-cycle vs. Multi-cycle](https://youtu.be/rQwzcYdYeCE)

________________________________________________________________________________________________________________________________________

### การบ้านครั้งที่ 4

**การทำงานของคำสั่ง lw ใน CPU แบบ Multi-cycle**

* การทำงานของคำสั่ง lw ใน cpu แบบ Multi-cycle นั้นมี cycle หรือ step ในการทำงานทั้งหมดอยู่ 5 step
   * Step 1 : การอ่านคำสั่ง โดยมีการดึงคำสั่งมาจากMemory
   * Step 2 : การแปลคำสั่ง 
   * Step 3 : การประมวลผล หรือ การคำนวณ โดยมีการนำค่าที่อยู่ใน Register rs + offset ไปเก็บที่ ALUout ซึ่งเกิดการทำงานหรือประมวลผลที่ ALU
   * Step 4 : นำค่าที่ได้จากการประมวลผลส่งไปที่ MDR
   * Step 5 : นำค่าที่เก็บไว้ที่ MDR ส่งไปเก็บไว้ยัง Register rt
   
- รูปตัวอย่าง CPU แบบ Multi-cycle 

![image5](https://camo.githubusercontent.com/3a759f503101d7359e3b9e88a79a64b022814d5a/68747470733a2f2f692e696d6775722e636f6d2f6d5758485770542e706e67)

### ส่งการบ้านครั้งที่ 4

[CLIP 4 : lw Instruction step in Multi-cycle CPU](https://youtu.be/CVvfJFUkybk)

________________________________________________________________________________________________________________________________________

### การบ้านครั้งที่ 5

**การทำงานของคำสั่ง beq ใน CPU แบบ Multi-cycle**

* การทำงานของคำสั่ง beq (Branch on equal) ใน CPU แบบ MIPS จะมี step ในการทำงานด้วยกันอยู่ 3 step
   * Step 1 : การอ่านคำสั่ง โดยมีการดึงคำสั่งมาจาก Memory 
   * Step 2 : แปลคำสั่ง มีการนำค่า ที่อยู่ใน register rs และ rt มาเก็บไว้ใน A และ B ดังในรูปของวงจร CPU แบบ Multi-cycle
   * Step 3 : การคำนวณ มีการนำค่าใน A และ B มาเปรียบเทียบกันว่าเท่ากันหรือไม่ ถ้าหากว่าเท่ากัน ก็จะส่งผลลัพธ์ที่ได้ออกไปทาง ALUout ส่งไปยัง PC
   
- รูปตัวอย่าง CPU แบบ Multi-cycle 

![image5](https://camo.githubusercontent.com/3a759f503101d7359e3b9e88a79a64b022814d5a/68747470733a2f2f692e696d6775722e636f6d2f6d5758485770542e706e67)

### ส่งการบ้านครั้งที่ 5

[CLIP 5 : beq Instruction step in Multi-cycle CPU](https://youtu.be/y_5s8D-EJ9o)

________________________________________________________________________________________________________________________________________

### การบ้านครั้งที่ 6 

**State Machine ของคำสั่ง R-format**

- รูปตัวอย่าง CPU แบบ Multi-cycle

![image6](https://camo.githubusercontent.com/3a759f503101d7359e3b9e88a79a64b022814d5a/68747470733a2f2f692e696d6775722e636f6d2f6d5758485770542e706e67)

* State Machine ของคำสั่ง R-format มีทั้งหมด 4 State โดยแต่ละ State จะมีสัญญาณ(เส้นสีส้ม) ดังรูป เพื่อส่งสัญญาณให้แต่ละส่วนทำงาน
   * State ที่ 1 : มีสัญญาณ Memread,lorD,IRWrite,ALUSrcA,ALUSrcB,ALUOP,PCWrite,PCSource ทำงาน
   * State ที่ 2 : มีสัญญาณ ALUSrcA,ALUSrcB,ALUOP ทำงาน
   * State ที่ 3 : มีสัญญาณ ALUSrcA,ALUSrcB,ALUOP ทำงาน
   * State ที่ 4 : มีสัญญาณ RegWrite,MemtoReg,RegDst ทำงาน

### ส่งการบ้านครั้งที่ 6

[CLIP 6 : R-format State Machine](https://youtu.be/Pz49OCkp3S4)

________________________________________________________________________________________________________________________________________

### การบ้านครั้งที่ 7 

**Pipeline**

* Pipeline คือ Memory ที่เก็บเฉพาะชุดคำสั่ง โดยจะมีการลำดับคำสั่งให้มีความรวดเร็วในการประมวลผลเพิ่มขึ้น เรียกว่า Pipelining หลักการคือ ในแต่ละคำสั่งจะมีการซ้อนทับกัน โดยที่เมื่อคำสั่งแรก ทำงานในหน่วยประมวลผลส่วน ที่ 1 จบไปแล้ว และไปเริ่มทำงานในส่วนที่ 2 คำสั่ง 2 ก็จะไปเริ่มทำงานในหน่วยประมวลผลส่วนที่ 1 ต่อ โดยที่ไม่ต้องรอให้คำสั่งแรกทำงานจบทั้งหมดก่อน

- รูปแสดงการทำงานของ CPU ที่เป็น non-pipelined และ pipelined

**แบบ non-pipelined**

![image7](https://cs.stanford.edu/people/eroberts/courses/soco/projects/risc/pipelining/laundry1.gif)

**แบบ Pipelined**

![image8](https://cs.stanford.edu/people/eroberts/courses/soco/projects/risc/pipelining/laundry2.gif)

### ส่งการบ้านครั้งที่ 7

[CLIP 7 : Pipelining](https://youtu.be/IjAffqTXEYc)


________________________________________________________________________________________________________________________________________
