# Lab 2 - Problem IV : CircleCalculator

ข้อนี้เป็นการคำนวนพื้นที่วงกลม (Area) ตามสูตร πr^2 และเส้นรอบวงกลม (Circumreference) ตามสูตร 2πr โดยใช้ค่า π จาก `Math.PI` ที่มีค่าระบุไว้อยู่แล้วใน Java

และเราสามารถใช้ `String.format("%.จำนวนหลักf", ตัวแปร)` ในการตัดทอนการแสดงตำแหน่งของทศนิยม เช่น `String.format("%.2f", 2.456)` จะได้ผลลัพธ์ออกมาเป็น 2.46 (ปัดขึ้นเพราะ 6)


```java
public class CircleCalculator {
    public static void main(String[] args) {
        if (args.length == 1) {
            double radius = Double.parseDouble(args[0]);
            double area = Math.PI * Math.pow(radius,2); //พื้นที่วงกลม = pi*radius^2
            double circumreference = 2 * radius * Math.PI; //เส้นรอบวงกลม = 2*pi*radius
            System.out.println("An area of a circle with radius of " + args[0] + " is " + String.format("%.2f", area));
            System.out.println("A circumference is " + String.format("%.2f", circumreference));
            //แสดงค่าออกเป็นทศนิยมสองตำแหน่ง (String.format("%.2f",...))
        } else {
            System.err.println("CircleCalculator <radius of circle>");
        }
    }
}
```
---
อย่าลืม!
- Setup Run Configurations ด้วย ใส่ `$Prompt$` ใน Program Arguments ไม่งั้นจะขึ้น Error `java.lang.ArrayIndexOutOfBoundsException`
- Style เป็นสิ่งที่สำคัญสำหรับการเขียนโค้ต อย่าลืมกฎ Camel Case Naming และการตั้งชื่อตัวแปรต่าง ๆ ให้สื่อความหมายและทำความเข้าใจได้ง่าย !
