# Javaへようこそ(Welcome to java)
ในวิชา EN811301 และ EN811302 หรือก็คือ Advanced Computer Programming ก็คือวิชาการ**เขียนโปรแกรม**ที่(อาจ)ต่อยอดมาจาก EN811300 FUNDAMENTALS OF COMPUTER PROGRAMMING

***ย้ำว่า Java ไม่ใช่ javascript***


## What is Java
Java คือ ภาษาชั้นสูงภาษาหนึ่งที่นิยมใช้ในการสร้างเครื่องมือต่างๆ แอพพลิเคชั่น และ เ ก ม ส์

หลักการทำงานของเจ้าภาษา Java จะต่างจากภาษา Python (นิดนึง) โดยภาษา Python จะทำงานในลักษณะ**อ่านและตีความเป็นทีละบรรทัด(Interpreter)** ส่วนภาษา Java จะเป็นในลักษณะ**อ่านและวิเคราะห์ทั้งไฟล์ก่อน(Compile) จากนั้นค่อยทำงาน(Run)**

## Why Java
* มันดีย์
* ลื่นไหล
* ¯\\_(ツ)_/¯


## Let's Hello world

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

> ณ ตอนนี้อาจจะงงว่า อะไรคือ public class อะไรคือ public static void แต่ช่างมันเถอะ จำๆไปก่อน :)

ในทุกๆไฟล์ต้องกลุ่มก้อนพลังก้อนใหญ่ๆอย่างน้อยหนึ่งก้อนเสมอ เราจะเรียกกลุ่มพลังก้อนใหญ่ว่า **class**

```java
public class ชื่อคราส {
}
```

โดยในตัวอย่างด้านบน เราตั้งชื่อ Class ว่า `Main` (และชื่อ Class ควรตั้งชื่อตาม[กฎ Camel Case Naming](https://www.geeksforgeeks.org/java-naming-conventions/) ด้วย) โดยชื่อไฟล์**จะต้องตรงกับชื่อ Class ด้วย**

Note: **Java เป็นภาษาที่ Case-Sensitive**

ใน Java จะ **ไม่ได้รันโค้ตทั้งหมดจากบนลงล่างเหมือนใน Python เสมอไป** แต่จะเริ่มรันจาก **ฟังก์ชั่นหลัก()** แล้ว **รันโค้ตที่อยู่ในฟังก์ชั่นหลักนั้นจากบนลงล่าง**

สำหรับ Java ที่เป็นการ Command Line App (หรือคือที่เราทำอยู่ในตอนนี้) จะมีฟังก์ชั่นหลักคือ `main`

โดยการสร้างฟังก์ชั่น main นี้ให้ประกาศว่า
`public static void main(String args[])` ตามตัวอย่างด้านล่างนี้

```java
public class Main {
    public static void main(String[] args) {
        //Write your code inside here
        System.out.println("Hello World");
    }
}
```
เมื่อเรารันโค้ต Java นี้ จะได้ผลลัพธ์คือ 

>Hello World

โดยทั่วไปแล้ว Java จะมีต่างจาก Python ที่ใช้การ**เคาะย่อหน้า** (Indient) ในการบอก**กลุ่ม Block ของโค้ต** โดยใน Java เราจะใช้ปีกกา `} {` หรือ Bracket ในการระบุกลุ่ม Block ของโค้ต

เปรียบเทียบ Block ของโค้ตระหว่าง Python และ Java
![](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/0-1.png)


อย่าลืม!
- ทุกบรรทัด อย่าลืม `;` ด้วย! Java ต้องใส่!