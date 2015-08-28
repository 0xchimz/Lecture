# End-to-End Communication

### Direct Communication
  - ต่ออุปกรณ์เข้ากันโดยตรง ใช้ สายในการเชื่อมต่อ เป็นการต่อกันแบบพื้นฐาน
  - TX: pit ที่ใช้ส่งข้อมูล
  - RX: pit ที่เอาไว้รับข้อมูล
  - สาย ground เอาไว้จ่ายกระแสไฟฟ้า

### Internet Communication
  - ต่ออุปกรณ์ผ่าน Internet
  - ต่างจากแบบแรกตรงที่ตอนที่ผ่าน Internet มันจะผ่านระบบที่ใหญ่กว่า ไม่ใช่แค่การผ่านสายโดยตรงเหมือนแบบแรก

## Internet Communication

### Client-Server Paradigm
  - Client
    * เป็น service user เป็นคนส่ง request เป็นคนสร้าง request
  - Server
    * รอ issue จาก client เป็นคนตอบกลับ request ต่างๆ หลังจากแก้ปัญหาแล้ว

การที่จะทำให้ client กับ server ต่อกันได้ต้องมี protocol มาทำให้มันคุยกันได้

### Our Simple protocol - ลองสร้าง Protocol แบบง่ายๆกันดู
Client                     =====>   Server
Request Issued by Client            Response by Server
 id\r\n                             StdId, followed by \r\n
 name\r\n                           Name, followed by \r\n

Server response with "ERROR\r\n" when receiving an unknown command

**Sender & Receiver** - ขึ้นอยู่กับ client หรือ server เป็นคนส่งหรือรับข้อมูล

**Medium** - ขึ้นอยู่กับใช้อะไรในการส่งหรือรับ

###Python
- Python ไม่เหมือน Java ซึ่ง Java เป็นภาษาที่ต้อง compile

##TCP Socket: Flow in Python
  - Server is Application
  - Flow การทำงานดูตามสไลด์หน้า 14
  
