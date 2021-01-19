# Lab 2 - Problem I : Patient

ข้อนี้เป็นเบสิคของการเขียน Java

ก่อนอื่น เราต้อง Setup Run Configuration สำหรับทุก ๆ โจทย์ที่เราต้องรับค่าจากผู้ใช้ด้วย ตามรูปด้านล่าง

![](https://pondhub.ga/img/2021/01/05/Untitled_9.png)

สำหรับหลักการของข้อนี้:
เวลาที่ Java Command Line App รับค่าเข้าจากผู้ใช้ จะเก็บอยู่ในตัวแปร args ที่เราระบุเอาไว้ใน main (สังเกตจาก `public static void main(String[] args))`) ในรูปแบบของ Array โดยจะเรียงลำดับตามการรับเข้า ค่าไหนใส่ก่อนจะมาก่อน 

เช่น

ผู้ใช้กรอกข้อมูลมาว่า `Hello World OwO`
ข้อมูลใน args ที่เก็บไว้ได้แก่
```java
args[0] = "Hello";
args[1] = "World";
args[2] = "OwO";
```

จากข้อนี้ ให้รับค่า `ชื่อ`, `อายุ`, `ประเทศ` ตามลำดับจากผู้ใช้ แล้วแสดงออกมาตามที่โจทย์กำหนด

```java
public class Patient {
    public static void main(String[] args) {
        if (args.length == 3) { //args.length show how many item in args
            //Case that user insert all 3 required arguments.
            System.out.println("Patient's name is " + args[0]);
            System.out.println("Patient's age is " + args[1]);
            System.out.println(args[0] + " comes from " + args[2]);
        } else {
            //If not, display an error message.
            System.err.println("Patient <patient name> <patient age> <country>");
        }
    }
}
```
---
อย่าลืม!
- Setup Run Configurations ด้วย ใส่ `$Prompt$` ใน Program Arguments ไม่งั้นจะขึ้น Error `java.lang.ArrayIndexOutOfBoundsException`
- Style เป็นสิ่งที่สำคัญสำหรับการเขียนโค้ต อย่าลืมกฎ Camel Case Naming และการตั้งชื่อตัวแปรต่าง ๆ ให้สื่อความหมายและทำความเข้าใจได้ง่าย !
