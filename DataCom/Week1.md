#Course Introduction

1. วิธีที่จะใช้ทรัพยากรร่วมกันได้อย่างมีประสิทธิภาพมากที่สุด
  * ต้นทุนต่ำ
  * สามารถเข้าถึงได้ง่าย
2. วิธีที่จะแลกเปลี่ยนข้อมูลได้อย่างมีประสิทธิภาพมากที่สุด
  * ต้องแลกเปลี่ยนได้ไว
  * แลกเปลี่ยนได้ครั้งละใหญ่ๆ
  * ต้องมีความแม่นยำถูกต้อง

ในการที่จะสื่อสารกันได้นั้นต้องมีส่วนประกอบดังนี้
  1. **Message** - ข้อความที่จะใช้สื่อสารกัน
  2. **Sender** - ผู้ส่ง
  3. **Receiver** - ผู้รับ
  4. **Medium** - ตัวกลางระหว่างคนส่งกับคนรับ
  5. **Protocol** - มาตรฐานในการสื่อสารกันระหว่างคอมพิวเตอร์ ปัจจุบัน IPv6 ใช้กันเยอะๆ IPv4

##Protocol
ประกอบด้วยอะไรบ้าง?
- Syntax: รูปแบบของข้อมูลที่ใช้ส่ง
- Semantics: แต่ละส่วนมีความหมายยังไง?
- Timing: เวลา และ ความถี่ในการส่ง

##Standards
- สื่อสารกันผ่านตัวกลางเดียวกัน
- เข้าใจความหมายของข้อมูลจากทั้งสองฝ่าย

ตัวอย่างในการสื่อสารกันของข้อมูล

1. ตัวเลข : bit integer

2. ทศนิยม : floating point

3. ข้อความ : ASCII, Unicode

4. รูปภาพ : JPG, GIF, PNG

5. .....

บลาๆๆๆ

พอพัฒนากันไปกันมา ก็มีหลาย Standards ขึ้นมา....

_แล้ววววว ถ้าคนละ Standards จะคุยกันต้องทำไง?_

###Internetworking

ใช้ Gateways/routers ในการสื่อสารระหว่าง

พอเอามาต่อกันมากๆ แต่ละ Standards ก็มีคอมพิวเตอร์เยอะแยะไปหมดคุยกัน

ก็เลยเรียกพวกนี้ว่า "network of networks"

###The Internet

พอมี network of networks เยอะๆเข้า ก็เลยเรียกรวมๆว่า **The Internet**

ตอนนี้คืออัตราการเติบโตของ Internet มันไวมากกกกก

แถมการเชื่อมต่อสื่อสารระหว่างกันก็เยอะจนแบบ มากกว่าประชากรมนุษย์ซะอีก =3=

ยุคของ IOT นั่นเอง เย๊~

##Languages and Tools

เครื่องมือที่จะใช้เรียนในวิชานี้ได้แก่
- ping, traceroute (tracert on Windows) ก็เอาไว้ ping ดูอะนะ ว่ามันมี response กลับมาหรือเปล่า traceroute: ก็เอาไว้ track ว่า ตั้งแต่เครื่องเราส่งไปยังเป้าหมาย มันทำงานถูกต้องมั้ย

- Network traffic monitor

ตัวอย่างโปรแกรม ก็ **wireshark** - โปรแกรมนี้เอาไว้ดักดูข้อมูลที่ส่งออกและรับมาในเครื่องเรา

- Programming
  * Java (with Groovy shell)
  * Serial communication library
  * Such as RXTX

###Serial Communication

- เอาไว้ต่อคุยกันโดยตรงระหว่างเครื่องคอมพิวเตอร์

###Berkeley Socket API

- API ที่เอาไว้เขียนโปรแกรมเชื่อมต่อกันระหว่าง Internet (Socket นี่มัน real time นะจ๊ะ)
- มีภาษา Java, .NET, Python

###Web APIs (Web Services)

- มาตรฐานที่เอาไว้คุยกันผ่าน website
  * Facebook API
  * Twitter API
  * Various Google APIs

จบแล้วเย๊~
