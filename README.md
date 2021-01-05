# Java 101

สำหรับใครที่อยากล่วงหน้าไปก่อน สามารถศึกษาได้ที่:
* https://www.w3schools.com/java/default.asp (Basic)
* https://www.youtube.com/playlist?list=PLoTScYm9O0GF26yW0zVc2rzjkygafsILN (Basic + Intermidate, เป็นวิดีโอ เหมาะสำหรับคนที่ไม่ชอบอ่านข้อความ, ถ้าทำ lab 1 แล้วให้เริ่มดู[คลิปที่ 9](https://www.youtube.com/watch?v=h3t2Gs_TvN4&list=PLoTScYm9O0GF26yW0zVc2rzjkygafsILN&index=9))
* https://introcs.cs.princeton.edu/java/ (Intermidate)
* http://math.hws.edu/javanotes/ (Advanced, Full version of Javadoc)

* https://www.youtube.com/watch?v=ypuHUfOzUTc&list=PL0ROnaCzUGB6Vtz0o4J22iE1VatwV03nj (Python -> Java,เป็นวิดีโอที่ฟังแล้วน่านอนมาก แต่ก็ถ้าเข้าใจจะดีมาก)

สำหรับข้อนี้เป็นพื้นฐานการใช้ Java และ Intelij IDEA ในการเขียน Java

## Java Syntax

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```
ทุก ๆ โค้ตที่รันใน Java จะต้องอยู่ภายในไฟล์ Class เท่านั้น โดยในตัวอย่างด้านบน เราตั้งชื่อ Class ว่า Main (และชื่อ Class ต้องตั้งชื่อตาม[กฎ Camel Case Naming](https://www.geeksforgeeks.org/java-naming-conventions/) ด้วย) โดยชื่อไฟล์**จะต้องตรงกับชื่อ Class ด้วย**

Note: **Java เป็นภาษาที่ Case-Sensitive**



โดยทั่วไปแล้ว Java จะมีต่างจาก Python ที่ใช้การเคาะย่อหน้า (Indient) ในการบอกกลุ่ม Block ของโค้ต โดยใน Java เราจะใช้ปีกกา `} {` หรือ Bracket ในการระบุกลุ่ม Block ของโค้ต

เปรียบเทียบ Block ของโค้ตระหว่าง Python และ Java
![](https://pondhub.ga/img/2021/01/05/Untitled_12.png)



และใน Java จะ **ไม่ได้รันโค้ตทั้งหมดจากบนลงล่างเหมือนใน Python เสมอไป** แต่จะเริ่มรันจาก **ฟังก์ชั่นหลัก** แล้ว **รันโค้ตที่อยู่ในฟังก์ชั่นหลักนั้นจากบนลงล่าง**

สำหรับ Java ที่เป็นการ Command Line App (หรือคือที่เราทำอยู่ในตอนนี้) จะมีฟังก์ชั่นหลักคือ `main`

โดยการสร้างฟังก์ชั่น main นี้ให้ประกาศว่า

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


อย่าลืม!
- Java ใช้ `{}` ในการระบุ Block ของโค้ต ไม่ได้ใช้การเคาะย่อหน้า, `:`, ฯลฯ เหมือนใน Python แล้ว
- ทุกบรรทัด อย่าลืม `;` ด้วย! Java ต้องใส่!



## **Java Variable**

ใน Python เมื่อเราต้องการให้ตัวแปรใด ๆ แทนค่าใด ๆ เราจะให้ `a = สิ่งที่เราต้องการ` ได้เลย

แต่ใน Java เราจำเป็นต้องระบุด้วยว่า a ที่เราต้องการจะให้แทนนั้น มีชนิดเป็นอะไร ซึ่งจะคล้ายๆลักษณะต่อไปนี้

`<ประเภทตัวแปร> <ชื่อตัวแปร> = สิ่งที่เราต้องการ`

เช่น

`int x = 72;`
`float y = -44.32;`
`String name = "Cat is CUTE!";`

โดยประเภทตัวแปรสามารถศึกษาแบบคร่าวๆได้ที่ [Lab ที่ 2 ข้อที่ 2](https://github.com/CoE30-KKU/EN811302/blob/master/lab%202/%E0%B8%82%E0%B9%89%E0%B8%AD%202%20-%20PrimativeVariableType.md)


## **เดี๋ยวมาอัพเดทเพิ่ม
ใครอยากไปนั่งดูเล่น ๆ ก่อน : https://www.youtube.com/watch?v=h3t2Gs_TvN4&list=PLoTScYm9O0GF26yW0zVc2rzjkygafsILN&index=9
