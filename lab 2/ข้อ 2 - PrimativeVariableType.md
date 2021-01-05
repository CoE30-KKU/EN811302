# Lab 2 - Problem II : PrimativeDataType

สำหรับข้อนี้เป็นการสอนเรื่องประเภทของการเก็บข้อมูลต่าง ๆ ที่มีใน Java

โดย
- byte ใช้ในการเก็บค่าตัวเลข ซึ่งสามารถเก็บได้ตั้งแต่ `-128 ถึง 127` (2^8)
- short ใช้ในการเก็บค่าตัวเลข ซึ่งสามารถเก็บได้ตั้งแต่ `-32768 ถึง 32767` (2^16)
- int ใช้ในการเก็บค่าตัวเลข ซึ่งสามารถเก็บได้ตั้งแต่ `-2147483648 ถึง 2147483647` (2^32)
- long ใช้ในการเก็บค่าตัวเลข ซึ่งสามารถเก็บได้ตั้งแต่ `-9223372036854775808 ถึง 9223372036854775807` (2^64)
- float - ใช้ในการเก็บค่าทศนิยม ซึ่งสามารถเก็บได้มากที่สุด `3.4028235E38`
- double ใช้ในการเก็บค่าทศนิยม ซึ่งสามารถเก็บได้มากที่สุด `1.7E308`
- char ใช้ในการเก็บตัวอักษร 1 ตัว
- string ใช้ในการเก็บตัวอักษร (เก็บได้มากกว่า char)
- boolean ใช้ในการเก็บค่าระหว่าง `จริง (true)` และ `เท็จ (false)`


```java
public class PrimitiveDataType {
    public static void main(String args[]){
        byte b = 120;
        short s = 32000;
        int i = 2000000000;
        long l = 9000000000000000000L;
        float f = 1.12345F;
        double d = 1.123456789123;
        char c = 'a';
        boolean bool = true;
        System.out.println(bool);
        System.out.println(b);
        System.out.println(f);
        System.out.println(l);
        System.out.println(i);
        System.out.println(c);
        System.out.println(s);
        System.out.println(d);
    }
}
```
