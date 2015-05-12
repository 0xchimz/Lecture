#Virtual Memory

Memory ส่วนไหนที่ไม่ได้ใช้ก็จะเอาไปเก็บใน Hard Disk ก่อน พอจะใช้ก็เอากลับมาเก็บใน Memory ใหม่

![](./imgs/vm-1.jpg)

**Background**
* ควรจะเพิ่มปริมาณการเก็บได้ไม่จำกัด
* เวลาโปรแกรมมันรันก็จถูกแบ่งเป็น page เยอะๆ แต่โปรแกรมไม่จำเป็นต้อง run ทุกๆ page โดย อันไหนที่ไม่ต้องใช้ก็เอาไปเก็บไว้ใน VM ได้ ทำให้ RAM ไม่จำเป็นต้องทำงานหนัก

**Virtual-address Space**
* ใน Virtual ก็จะมี Address ของตัวเองขึ้นมาเพื่อใช้ในการอ้างอิง

![](./imgs/vm-2.jpg)

**Demand Paging**

![](./imgs/vm-3.jpg)

* Lazy swapper - swap ไปมาเมื่อต้องการที่จะใช้
* Page Fault - ก็คือยังไม่มีใน Frame ก็เลยไปดึงมาจาก Virtual เพื่อเอามาเก็บใน Frame แล้วเปลี่ยนเป็น Valid

![](./imgs/vm-4.jpg)  

##Page Fault Rate
* มีค่าตั้งแต่ 0 ... 1
* EAT = hit + miss
* EAT = (1-p) x time + p x time

##Copy-on-Write

คือการแชร์ p1 กับ p2 อะไรที่ใช้ร่วมกันก็จะแชร์ไปใช้อันเดียวกัน

![](./imgs/vm-5.jpg)

คือถ้ามี p1 ต้องการจะแก้ page C มันเลยต้องสร้าง page ใหม่ขึ้นมาแล้วค่อยเข้าไปแก้ในนั้น

![](./imgs/vm-6.jpg)
