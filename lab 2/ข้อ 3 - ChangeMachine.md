# Lab 2 - Problem III : ChangeMachine

ข้อนี้เป็นการแปลงจากเหรียญให้เป็นจำนวนเงินที่มีทั้งหมด และแปลงเงินเหล่านั้นออกมาเป็นแบงค์ขนาดต่าง ๆ

หลักการ
![](https://pondhub.ga/img/2021/01/05/Untitled_11.png)

```java
public class ChangeMachine {
    public static void main(String[] args) {
        if (args.length == 4) {
            int oneCoin = Integer.parseInt(args[0]);
            int twoCoin = Integer.parseInt(args[1]);
            int fiveCoin = Integer.parseInt(args[2]);
            int tenCoin = Integer.parseInt(args[3]);
            //Note: Integer.parseInt() ใช้ในการแปลงค่าจาก String -> int
            int balance = oneCoin + 2 * twoCoin + 5 * fiveCoin + 10 * tenCoin; //รวมเหรียญให้เป็นจำนวนเงินรวม

            int thousandBank = balance / 1000;
            int fiveHundredBank = (balance % 1000) / 500;
            int hundredBank = ((balance % 1000) % 500) / 100;
            int twentyBank = (((balance % 1000) % 500) % 100) / 20;
            int remainBalance = (((balance % 1000) % 500) % 100) % 20;
            /*
            หลักการ
            เมื่อนำเงินทั้งหมด มาหารด้วย 1000 -> ได้จำนวนแบงค์พันทั้งหมด และ เศษ
            โดยนำเศษที่ได้จากการหารด้วย 1000 มาหาร 500 ต่อ ทำไปเรื่อย ๆ จนถึง 20 และหาเศษของการหารด้วย 20
            */
            System.out.println("1-baht coins : " + oneCoin);
            System.out.println("2-baht coins : " + twoCoin);
            System.out.println("5-baht coins : " + fiveCoin);
            System.out.println("10-baht coins : " + tenCoin);
            System.out.println("Balance amount : " + balance);
            System.out.println("1,000-baht bill : " + thousandBank);
            System.out.println("500-baht bill : " + fiveHundredBank);
            System.out.println("100-baht bill : " + hundredBank);
            System.out.println("20-baht bill : " + twentyBank);
            System.out.println("Money remain : " + remainBalance);
        } else {
            System.err.println("ChangeMachine <1-baht coins> <2-baht coins> <5-baht coins> <10-baht coins>");
        }
    }
}
```
---
อย่าลืม!
- Setup Run Configurations ด้วย ใส่ $Prompt$ ใน Program Arguments ไม่งั้นจะขึ้น Error `java.lang.ArrayIndexOutOfBoundsException`
- Style เป็นสิ่งที่สำคัญ อย่าลืมกฎ Camel Case Naming และการตั้งชื่อตัวแปรต่าง ๆ ให้สื่อความหมายและทำความเข้าใจได้ง่าย