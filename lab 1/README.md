# **Lab 1 - Tools to develop and share Java Program**

สำหรับในเทอมนี้ ภาษาที่เราจะเรียนกันก็คือ "Java" โดยที่ Java นั้นจะใช้เครื่องมือที่สำคัญ ๆ หลัก ๆ อยู่ 3 ตัวได้แก่
- Java SE Development Kit (JDK)
- Intelij IDEA
- Git

### **Java SE Development Kit (JDK)**
---
สำหรับตัว Java SE Development Kit หรือเรียกสั้น ๆ ว่า JDK เป็นเสมือนกับแกนกลางสำคัญในการรันโปรแกรม Java เพราะเป็นตัวที่ใช้ในการ Compile File ของ Java ให้กลายเป็นไฟล์ที่คอมพิวเตอร์สามารถเข้าใจได้ และเป็นตัวเรียกการทำงานไฟล์ Java อีกด้วย

โดย JDK สามารถดาวน์โหลดได้ที่ [https://www.oracle.com/java/technologies/javase-jdk15-downloads.html](https://www.oracle.com/java/technologies/javase-jdk15-downloads.html) โดยให้เลือกดาวน์โหลด `Windows x64 Installer` สำหรับเครื่องคอมพิวเตอร์ Windows แล้วติดตั้งตัวโปรแกรมให้เรียบร้อย

![Image](https://pondhub.ga/img/2020/12/28/Screenshot%202020-12-28%20220535.png)

หลังจากที่ติดตั้งเสร็จเรียบร้อยแล้ว เราจะยังไม่สามารถใช้คำสั่งของ Java ได้ทันที ให้ทำการเข้าไปเซท Environment ของเครื่องก่อน

โดยให้

1) เข้า `Settings` ของคอมพิวเตอร์
2) พิมพ์ `Environement` แล้วเลือก `Edit System Environment Variables`
3) เลือก `Environment Variables`
4) เลื่อนหา `PATH` ใน `System Variables` (ถ้าไม่มีให้กด new เพื่อสร้างใหม่ได้เลย)
5) เพิ่มตำแหน่งของ JDK ที่เราลงเอาไว้ก่อนหน้า โดยให้เติม \bin ตามท้ายด้วย เช่น `C:\Program Files\Java\jdk...\bin`

![Image](https://pondhub.ga/img/2020/12/28/Untitled.png)

### **Intelij IDEA**
---
โปรแกรมนี้เป็นโปรแกรมหลักที่เราจะใช้ในการพัฒนาและเขียนโค้ตภาษา Java ในเทอมนี้ คล้าย ๆ กับเทอมก่อนหน้านี้ที่เราใช้ PyCharm ในการเขียนโค้ต Python 

สำหรับ Intelij IDEA จะมีหลาย Edition ที่มีให้โหลดกันทั้ง Ultimate Edition (เสียตัง/หรือฟรีสำหรับการศึกษา) และ Community Edition (ฟรี) โดยแนะนำให้เราลงทะเบียน Intelij for Education เพื่อให้สามารถได้ใช้ Intelij IDEA Ultimate Edition 

สามารถลงทะเบียนได้ที่ [https://www.jetbrains.com/community/education/](https://www.jetbrains.com/community/education/)

1) เลื่อนหาปุ่ม `Apply Now`
2) กรอกข้อมูลส่วนตัวของเราตามที่เว็บไซด์ต้องการ (ในส่วนของ Email แนะนำให้สมัครโดยใช้ KKUMail)
3) หลังจากที่ดำเนินการทุกอย่างเรียบร้อยแล้ว ให้เช็คในกล่องจดหมายของอีเมลเพื่อทำการยืนยันบัญชี
4) ในอีเมลที่ส่งมาจะมีให้กด `follow this link` เพื่อดำเนินการต่อ ให้อ่านเงื่อนไขการให้บริการให้เรียบร้อยแล้วกด Accept
5) หากยังไม่มี Jetbrains Account ให้กด `Create an account`, หากมีอยู่แล้วให้ใส่ข้อมูลแล้ว `Login`
6) ให้กดปุ่ม `Download` ด้านใต้ `JetBrains Product Pack for Students` แล้วตามหา Intelij IDEA Ultimate
![Image](https://pondhub.ga/img/2020/12/29/Screenshot%202020-12-29%20141104.png)
7) หลังจากที่ติดตั้งเรียบร้อยแล้ว จะมีให้ Activate License เมื่อเราเปิดโปรแกรมครั้งแรก ให้ล็อกอินด้วยข้อมูลเดียวกันกับที่ใช้ login ในเว็บ JetBrains ในขั้นตอนที่ `5`


### **การใช้งาน Intelij**
---

สำหรับการใช้งานครั้งแรก และยังไม่มีโปรเจค หรือต้องการจะสร้างโปรเจคใหม่ ให้เรากด `New Project` แล้วเลือก `Java` แล้วกด `Next`
![](https://pondhub.ga/img/2020/12/29/Untitled.png)

สำหรับหน้าถัดมา จะเป็น Project Template ให้ อันนี้แล้วแต่ว่าเราจำเป็นต้องใช้ Project Template ของ Intelij หรือไม่ (สำหรับคนที่พึ่งเริ่ม แนะนำให้ติ๊กเอาไว้ด้วย)
![](https://pondhub.ga/img/2020/12/29/Untitled_1.png)

หน้าถัดมาเป็นหน้าสำหรับตั้งข้อมูลของโปรเจคเรา ซึ่งข้อมูลส่วนนี้แล้วแต่ว่าเราจะตั้งค่าอะไรยังไงก็ได้
![](https://pondhub.ga/img/2020/12/29/Untitled_2.png)

หลังจากที่กด Finish แล้วจะปรากฏหน้าต่างสำหรับดำเนินการต่าง ๆ กับโค้ตของเราทั้งหมด เป็นอันว่าเสร็จสิ้นการสร้าง Project
![](https://pondhub.ga/img/2020/12/29/Untitled_3.png)


### **Git**
---
โปรแกรม Git เป็นโปรแกรมที่ใช้ในการเชื่อมโค้ตของเราระหว่างในคอมพิวเตอร์กับ GitHub ซึ่งเป็นแหล่งรวมโค้ตมากมาย อีกทั้งยังมีประโยชน์ต่อการดู/ตรวจสอบการเปลี่ยนแปลงของโค้ตของเรา และอื่น ๆ อีกมากมาย

สำหรับใครที่ใช้ Linux/MacOS ข้ามขั้นตอนนี้ไปเลย
สำหรับ Windows ให้ดาวน์โหลดได้ที่ [https://git-scm.com/downloads](https://git-scm.com/downloads)

หลังจากติดตั้งเรียบร้อยแล้ว ให้เปิด Command Prompt (CMD) แล้วพิมพ์ `git --version`

หากขึ้น version ออกมาถือว่าใช้งานได้แล้ว

![Image](https://pondhub.ga/img/2020/12/29/Screenshot%202020-12-29%20141618.png)


หากขึ้น `'git' is not recognized as ...` ให้เราทำการ Set PATH โดยทำเหมือนกับการตั้ง PATH ใน Java เลย โดยให้ Path เป็น Path ที่ติดตั้ง Git เอาไว้และเพิ่ม `\bin` (เช่น `C:\Program Files\Git\bin`)

![Image](https://user-images.githubusercontent.com/39224460/40680922-471c0946-63a5-11e8-8586-0f9eb97f6520.JPG)

สำหรับการใช้งานครั้งแรก ให้เราทำการตั้งค่าชื่อและ Email ของ Git ของเราด้วย
โดยการพิมพ์คำสั่ง

สำหรับการตั้งชื่อ
> ```git config --global user.name "ชื่อ"```

สำหรับการตั้ง Email
> ```git config --global user.email "email@website.com"```

**ต้องทำ หากไม่ทำ ในการ git push ครั้งแรกจะมีข้อความบังคับให้ทำอยู่ดี



### **การใช้งาน Git และ GitHub**
---
สำหรับการที่เราจะเอาไฟล์โค้ตของเราเข้า GitHub นั้นเราจำเป็นต้องมี Git อยู่ในเครื่องซะก่อน (สำหรับ Windows ต้องดาวน์โหลดเพิ่ม, ย้อนกลับไปดูข้างบน // สำหรับ MacOS - Linux ไม่ต้องทำอะไร)

และอีก 2 สิ่งที่ต้องมีคือ Account และ Repository อยู่บนเว็บไซด์ GitHub.com

**กรณีที่ยังไม่สมัคร GitHub**
 > [สมัครซะ !](https://github.com/join) แล้วก็อย่าลืม [รับ GitHub Student Developer Pack ด้วย !](https://education.github.com)


**กรณีที่ยังไม่สร้าง Reposity**
หลังจากที่เรา Login แล้ว ถ้ายังไม่มี Repository ให้เรากด ["Create repository"](https://github.com/new) ![](https://pondhub.ga/img/2021/01/05/Untitled.png)
จากนั้นให้เราตั้งชื่อ Repository ของเราซะ (โดยในที่นี้อาจารย์ให้ใช้เป็น `รหัสนักศึกษาไม่มีขีด-java-labs` เช่น `6330401661-java-labs` และอาจารย์ให้เลือกเป็น **Private** ด้วยนะ!) จากนั้นก็กด Create repository เลย ![](https://pondhub.ga/img/2021/01/05/Untitled_1.png)

เราจะได้ Repository ของเราขึ้นมา ให้เราคัดลอกลิ้งก์เข้า Repository ของเราไว้ (ตรงที่ลูกศรชี้ หรือ URL ของหน้าเว็บนี้ก็ได้)
![](https://pondhub.ga/img/2021/01/05/Untitled_2.png)


จากนั้นให้เข้ามาใน Command Prompt หรือ Git Bash (แล้วแต่สะดวก)
แล้วพิมพ์ `git clone <URL ของ Repository ที่คัดลอกไว้ วางโดยการคลิ๊กเม้าส์ขวา>` 

ถ้าหากทำถูกต้อง จะได้โฟลเดอร์ที่ชื่อเดียวกับ Repository ใน Github ที่อยู่ใน `C:/User/<User>/<Repository>` (ข้อสังเกต: ตำแหน่งของโฟลเดอร์จะเป็นตำแหน่งเดียวกับที่เขียนอยู่ใน Command Prompt ที่ขีดสีแดงเอาไว้) ![](https://pondhub.ga/img/2021/01/05/Untitled_4.png)


**ให้จำไว้ให้ดี ๆ ว่าเรา Clone Repository ใส่โฟลเดอร์ไหนเอาไว้ เพราจะได้ใช้อยู่เรื่อย ๆ ด้วย**

ตอนนี้ Command Prompt ของเราจะมี Current Directory หรือตำแหน่งที่ Command Prompt กำลังทำงานอยู่ โดยในรูปตอนนี้จะอยู่ที่ C:/User/palap (ในกรณีของเครื่องนี้) ให้เราทำการเปลี่ยน Current Directory หรือเปลี่ยน Target Path ไปยังโฟลเดอร์ที่มี Git เพื่อเราจะใช้คำสั่งอื่น ๆ ของ Git ได้

โดยใช้คำสั่ง `cd <Folder/Path>` เช่น ถ้าปัจจุบัน Command Prompt มี Current Directory อยู่ที่ `C:/User/palap` แล้วเราต้องการเข้าโฟลเดอร์ `6330401661-java-labs` ที่อยู่ในตำแหน่ง `C:/User/palap/6330401661-java-labs` (หรือก็คือเป็นโฟลเดอร์ย่อยของ palap) ให้เรา `cd 6330401661-java-labs` ซะ

(คำสั่ง cd หลักการคล้ายกับการที่เราคลิ๊กเปิดโฟลเดอร์เข้าไปข้างใน ในกรณีนี้ โฟลเดอร์ใหญ่คือ palap มีโฟลเดอร์ย่อยคือ 6330401661-java-labs การ cd เหมือนการ double-click เพื่อเปิดโฟลเดอร์ 6330401661-java-labs นั่นแหละ)


ข้อสังเกต หลังจากที่เราเปลี่ยน Current Directory แล้ว Path ที่อยู่ด้านหน้าจะเปลี่ยนตามไปด้วย
![](https://pondhub.ga/img/2021/01/05/Untitled_6.png)

เมื่อเรามีการแก้ไขหรือเปลี่ยนแปลงไฟล์ใด ๆ **ภายใต้โฟลเดอร์ที่มี git** (Note: โฟลเดอร์ที่เรา git clone มาจะมี git อยู่ข้างในด้วย, แต่เป็นโฟลเดอร์ที่ซ่อนเอาไว้) เจ้า git จะคอยเก็บว่าเรามีการแก้ไข-เพิ่ม-ลบ-เปลี่ยนแปลงไฟล์ใดบ้าง

หลังจากที่เราแก้ไข - เพิ่ม - ลบ - เปลี่ยนแปลงไฟล์ใด ๆ เสร็จสิ้นแล้ว 

0) อย่าลืมเปลี่ยน Current Directory ก่อน !
```cd <folder/path>```
1) `git add -A` เพื่อให้ git เช็คว่ามีไฟล์ใดเปลี่ยนแปลงบ้าง
2) `git commit -m "ข้อความ"` เพื่อเขียนมาร์คว่าเราทำอะไรไปกับไฟล์อะไรไปบ้าง (เหมือนเป็นการทิ้งโน้ตไว้ว่า ฉันทำอันนี้ ๆ ๆ ไปนะ)
3) `git push` เพื่อส่งไฟล์ทั้งหมดเข้า GitHub

ถ้าทำทุกอย่างถูกต้องจริง ใน Repository บน Github ของเราจะมีการเปลี่ยนแปลงไฟล์ตามที่เรา Push ไปเมื่อสักครู่

Warning: สำหรับการ push ครั้งแรก
- Git อาจจะเตือนให้ตั้งชื่อ , Email ให้เลื่อนกลับไปอ่านด้านบนในส่วนของ Git
- Git อาจขึ้นหน้าต่างหรือมีข้อความให้ Login ให้เราใช้ Username และ Password ของ GitHub.com ในการ Login

![](https://pondhub.ga/img/2021/01/05/Untitled_7.png)