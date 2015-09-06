# Week3 (Draft)

### ข้อดีของ Direct Communication กับ Internet Communication
- **ความเสถียร** : ความเสถียร Internet มีความเสถียรมากกว่า เพราะว่าในปัจจุบันเราสามารถมีได้หลาย Router หลาย Hub (Cloud) ทำให้สามารถไปได้หลาย Link ไม่จำเป็นต้องไปเส้นทางเดียวกัน
  **ยกเว้น** ต่อ Internet แบบเส้นตรงเส้นเดียว แบบนี้ Internet สามารถล่มได้
- **ความเร็ว** : ขึ้นอยู่กับว่าใช้แบบไหน ถ้าใช้สายต่อตรงแบบเร็วๆอย่า Lan ที่มีความเร็วมากๆ 1 Gbps ก็จะไวกว่า Internet เพราะไม่ต้องแชร์กับใคร
- **ความปลอดภัย** : แน่นอนว่า Direct ปลอดภัยกว่า เพราะต่อตรงๆไม่ผ่านไปไหนเลย แต่ Internet ก็มีวิธีทำให้ปลอดภัยนะ
- **ความซับซ้อน** :
  - Internet ต้องใช้ซอฟแวร์ในการเชื่อมต่อที่ซับซ้อนกว่าเพราะว่าต้องใช้พวก Communication Library (Full TCP/IP Stack)
  - Direct ใช้แค่ serial protocol มันต้องการแค่ Hardware ธรรมดาก็สามารถเชื่อมต่อได้แล้ว แต่เช่นเดียวกันมันก็จะเชื่อมต่อ Internet ไม่ได้

  _Full TCP/IP Stack_ : Set of networking protocol ประกอบด้วยหลายๆ layer เดี๋ยวจะกล่าวต่อไป

- **สถานที่** : Internet เวลาจะเชื่อมต่ออุปกรณ์กันไม่จำเป็นต้องอยู่ใกล้กันตราบใดที่ยังมี Internet ก็สามารถเชื่อมต่อกันได้
- **reliability** : Internet เนื่องจากมันมีหลาย Device ที่ต้องผ่าน ทำให้อาจจะเกิด Delay ที่สูงหน่อย

### แล้วอะไรเป็น Protocol ที่จะใช้ในการแสดงผลเว็บละ?

> **Browser** เป็นเหมือน Client Software ที่ติดต่อกับ Webserver แล้วมันรู้ได้ไงว่ามันจะเอาอะไรมาแสดง?

> แล้ว **Webserver** รู้ได้ไงว่า Client ต้องการอะไร?

**HTTP** - HyperText Transfer Protocol

**HTTPS** - Hyper Text Transfer Protocol with Secure Sockets Layer (SSL)

**TCP** - Transmission Control Protocol

**IP** - Internet Protocol

> ที่กล่าวมาทั้งหมดนี้เป็น Protocol หมดเลย เรามีหลาย Level ของ Protocol เพื่อช่วยกันให้ Internet สามารถทำงานได้

> ส่วน Protocol ที่ Fetch เอาเนื้อหาจาก Webserver มาแสดงผลเป็นเว็บไซต์ คือ **HTTP/HTTPS**

> **Socket** มันทำงานอยู่บน TCP

> **IP** ถ้าจะต่อ Internet ต้องใช้ตัวนี้ในการเชื่อมต่อ

###HTTP, TCP, IP. How it's work?

## Traditional Internet Application

### World Wide Web (www)

เราไม่ได้เรียกใช้ Protocol โดยตรง Web bowser เป็นตัวเรียกใช้งาน Protocol ต่างๆ

***www*** มันก็มีหลาย Standard ที่จะใช้ในการแสดงผลเว็บ 1 เว็บ ได้แก่
  * HTTP - Protocol
  * HTML - ภาษาที่ใช้แสดงผลเว็บไซต์
  * URL

### HTTP GET Requests/Responses

คำสั่งพื้นฐานในการ GET ค่าผ่าน HTTP

  ``` _GET /index.html HTTP/1.1_```

เมื่อ Client ส่งคำสั่ง GET ไปยัง Server ตัว Server ก็จะตอบกลับบางอย่างกลับมา เช่น

```HTML
HTTP/1.0 200 OK
Server: Apache/1.3.37
Content-Length: 221
Content-Type: text/html
<HTML>
:
</HTML>
```
แล้ว Browser ก็จะ render ออกมาให้เราดู

#### Wireshark
  บางครั้งที่เราต้อง Link ไปที่ต่างๆ นอกเครื่อง Wireshark จะ Monitor ทุกอย่างไว้ให้เราว่ามีการเข้าออกอะไรอย่างไรบ้าง

> คำสั่งที่ใช้ในการมองหา IP ของทุก OS คือ 'nslookup www.xxxx.com'

## Packet Switching, Layer Models and Protocol Suites

![](img/wk3_001.png)
จากภาพ A จะส่งข้อมูลไปหา B ก็ต้องผ่าน Protocol ซึ่ง Protocol ส่วนใหญ่จะเป็น Software การเชื่อมต่อผ่าน Internet ของ A ไป B จะต้องเหมือนกับการต่อกันโดยตรง แต่การที่จะส่งข้อมูลโดยตรงผ่าน Internet เลยนั้นทำไม่ได้ ต้องใช้ protocol เข้ามาช่วย

### Dedicated circuits
- เหมือนการต่อไปตรงๆ แบบต่อหมดทุกเครื่อง ธรรมดาไม่มีอะไร ถ้าต้องการจะ connect ไปไหนก็ต่อไปตรงๆเลย
  - ปลอดภัยมาก เพราะต่อเข้าตรงๆ
  - แต่ถ้าต้องการจะเปลี่ยนเครื่องที่เชื่อมต่อ ต้องทำการดึงปลั๊กออกแล้วก็เสียบเข้ากับเครื่องใหม่
  - ในอดีตต้องมีคนเปลี่ยนสาย Link ให้

![](img/wk3_002.png)

### Circuit Switching
- connect ไปยัง central switch
- ในอดีต central switch จะมีคนคอยดูให้ว่าจะโทรไปหาเบอร์อะไร ขั้นแรกต้องบอก Operator ก่อนว่าจะโทรไปหาใคร แล้ว Operator ก็จะต่อไปยังเบอร์ที่เราต้องการให้ แล้วจึงสามารถคุยกันได้
  - ข้อเสีย คือ มีคู่สายเป็นของตัวเอง คนอื่นมาใช้งานไม่ได้ เพราะไม่ได้แชร์ใคร ทำให้เปลืองทรัพยากร
  - ข้อดี คือ ไม่มีใครมาแชร์

![](img/wk3_003.png)

- ในปัจจุบัน automatic switch จะเปลี่ยนเส้นทางให้อัตโนมัติ
- แทนที่จะต้องคุยกับ Central Switch ก็ให้ automatic Switch เป็นคนเปลี่ยนเส้นกาคุยให้

### Packet Switching

![](img/wk3_004.png)

- ระบบนี้เราไม่จำเป็นต้องกังวลเรื่องคู่สายเลย เพราะแชร์กันได้
- ในการส่งแบบนี้ เราจำเป็นต้องแบ่งข้อมูลใหญ่ๆออกเป็นชิ้นเล็กๆ (Packet) ไม่ว่าข้อมูลจะใหญ่ขนาดไหนก็ตาม
- ในแต่ละชิ้นต้องมี Source and Destination Address แปะไปด้วย

  - ข้อดี
    - แชร์กันทุกอย่าง ใช้ทรัพยากรได้คุ้มค่า
    - 1 Link สามารถแชร์กับคนอื่นได้ในกรณีที่ไม่ได้ใช้

### Internet Layer Models
5 Layers Models

......... ภาพจากสไลด์ 12

#### Application Layer
ไอเดีย:

........ ภาพสไลด์ 13

- เวลาส่งไปเช่นผ่าน HTTP ก็ต้องส่งไปทั้ง Data และ Header(H5)

#### Transport Layer
ไอเดีย:

หน้าที่
- Port Addressing:
- Segmentation: ถ้าข้อมูลเยอะมากๆ ก็แยกเป็นชิ้นเล็กๆแล้วค่อยส่ง
- Connection control: จัดการให้ว่าต้องส่งไปช่องไหน เหมือนการเสียบของ switch
- Flow control:
- Error control:

ภาพสไลด์ 15 ......

Transport Layer ก็ยังไม่รู้ต้องไปทางไหนต่อ

#### Network Layer

เป็นสิ่งที่สำคัญที่สุด และยากที่สุดใน layer ต่างๆ

ไอเดีย: การส่งข้อมูลจากที่หนึ่งไปอีกที่หนึ่ง

service
  - Logical addressing: ต้องรู้ว่าจะส่งไปที่ไหน
  - Routing:

ภาพสไลด์ 17 ..........

Data > segment ที่จะส่งไป

H3 > Logical Address ที่จะส่งข้อมูลไป

เป็นตัวตัดสินใจว่าจะส่งไป Link ไหน แต่ส่งเองไมไ่ด้ ต้องส่งไปต่อที่ Data Link เพื่อพาข้อมูลส่งต่อไป

แต่ละ Network Address ต้อง Unique แล้วเชื่อมต่อแต่ละ Network ด้วย Router

#### Data Link Layer
ไอเดีย: ส่ง Frame ข้อมูลจาก node นึง ไปอีก node นึง

- ข้อมูลที่ส่งไปในรูปแบบ Frames: เตรียมข้อมูลสำหรับ signal transmission
- ต้องทำให้อยู่ในรูปที่ง่ายต่อการแปลงเป็น Electronic signal หรือ Radio Signal

... ภาพ(20)

#### Physical Layer
หน้าที่: เป็นตัวส่งจาก node นึงไปยังอีก node นึงในรูปแบบ bit

..... ภาพ(24)

#### Internet Models

MAC Address ใช้สำหรับ data link layer

IP Address ใช้สำหรับ network layer

**Network Layer** ถ้าเปลี่ยนนี่ลำบาก แต่ Layer อื่นๆ เปลี่ยนได้ ไม่กระทบ Layer อื่นๆ
