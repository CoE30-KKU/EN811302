# Lab 3 - Problem I : GuessNumberGame

ข้อนี้เป็นการเขียนโปรแกรมเพื่อสุ่มเลข และเช็คว่าเลขที่ผู้ใช้ป้อนเข้ามาตรงกับที่สุ่มเอาไว้ก่อนหน้านี้หรือไม่

โดยในการสุ่มเลข เราจะใช้สมการ
```java
int random_number = minNum + (int) (Math.random() * ((maxNum - minNum) + 1));
```
ซึ่งเจ้าฟังก์ชั่น `Math.random()` จะเป็นการ Random ค่าระหว่าง [0,1) (เป็นทศนิยม)

แล้วถามว่าทำไมสมการด้านบนทำให้ค่า random_number เป็นค่าที่อยู่ในช่วงของ [minNum,maxNum] กันหล่ะ?

สมมติให้ `minNum = 1, maxNum = 10`

เราลองแทนค่าให้ `Math.random() = 0` ซึ่งเป็นค่าน้อยที่สุดที่เป็นไปได้ของ `Math.random()`
จะได้ว่า
```java
int random_number = 1 + (int) (0*((10-1)+1)) // = 1
```
จะได้ random_number = 1 พอดี ซึ่งเป็นขอบเขตล่างตามที่เราต้องการ

ในทางกลับกันเราลองแทนค่าให้ `Math.random() = 0.99` ซึ่งเป็นค่า(เกือบ)มากที่สุดที่เป็นไปได้ของ `Math.random()`
จะได้ว่า
```java
int random_number = 1 + (int) (0.99*((10-1)+1)) // = 1 + 9.99 แต่ 9.99 ถูก cast เป็น (int) เลยเหลือแค่ 1 + 9 = 10
```
จะได้ random_number = 10 พอดี ซึ่งเป็นขอบเขตบนตามที่เราต้องการ


และสำหรับการรับค่าเข้าในข้อนี้ เราจะใช้ `java.util.Scanner;` ในการรับข้อมูลแทน
```java
    Scannar scan = new Scanner(System.in); //Make scanner listen to System.in (user input)
    scan.next(); //Get user input as string.
    scan.nextInt(); //Get user input as int.
    scan.nextFloat(); //Get user input as float.
    ...
```
อ่านเพิ่มเติมการใช้งาน Scanner ได้ที่ [w3schools.com](https://www.w3schools.com/java/java_user_input.asp)




```java
import java.util.Scanner;

public class GuessNumberGame {
    public static void main(String[] args) {
        int random_number = 1 + (int) (Math.random() * ((10 - 1) + 1)); //Random number within range of 1 to 10.
        Scanner input = new Scanner(System.in); //Get User input using Scanner.
        for (int tries = 2; tries >= 0; tries--) { //Loop tries to make program run 3 times.
            System.out.print("Please enter a guest (1-10):");
            int user_guess = input.nextInt(); //Get what number that user input.
            if (user_guess == random_number) { //User guess the right number.
                System.out.println("Congratulations! That's correct");
                break; //Exit loop by break it.
            } else if (user_guess > random_number)
                System.out.println("Please type a lower number! Number of remaining tries:" + tries); //Input is too high, advice him to lower it.
            else if (user_guess < random_number)
                System.out.println("Please type a higher number! Number of remaining tries:" + tries); //Input is too low, advice him to higher it.
            
        }
    }
}
```