# Java Control Flow

โดยทั่วไปแล้ว Java จะรันโค้ตจากบนลงล่าง (Top-to-Bottom) ตามลำดับของบรรทัด โดย Control Flow จะช่วยในการเปลี่ยนการรันจากบนลงล่างให้มีความหลากหลายมากขึ้น ทั้งการใช้ Loop, การรันฟังก์ชั่นอื่น, ฯลฯ โดยจะมีอยู่ 3 ประเภทหลัก ๆ ที่ Java รองรับได้แก่:
* Decision-making statements : if-then, if-then-else, switch
* Looping statements : while, do-while, for
* Branching statements : break, continue, return

## **Decision-making statement**
### If-then, If-then-else
เราจะใช้ `if(เงื่อนไข)` ในการระบุให้โค้ตใน `if()` รันเมื่อเงื่อนไขเป็น**จริง**

ยังมี `else if (เงื่อนไข)` ในการระบุให้โค้ตในตัวมันเองรันเมื่อเงื่อนไขก่อนหน้าเป็น**เท็จ**แล้วเงื่อนไขของมันเป็น**จริง**

และ `else` ในการระบุให้โค้ตในตัวมันเองรันเมื่อเงื่อนไขของ `if()` , `else if()` ใด ๆ ก่อนหน้าทั้งหมดเป็น**เท็จ** (รันทุกตัวแล้วไม่เข้าสักเงื่อนไขเลย เลยเป็นเคสสุดท้าย)
```java
if (condition1) {
  // block of code to be executed if condition1 is true
} else if (condition2) {
  // block of code to be executed if the condition1 is false and condition2 is true
} else {
  // block of code to be executed if the condition1 is false and condition2 is false
}
```


**TIP** เราสามารถเขียน if-else อย่างย่อได้ด้วย
```java
variable = (condition) ? expressionTrue :  expressionFalse;
```

เช่น
```java
int year = 2021;
if (time < 2020) {
  System.out.println("Good year.");
} else {
  System.out.println("WTF year.");
}
```

เราสามารถเขียนอย่างย่อได้เป็น
```java
int time = 2021;
String result = (time < 2020) ? "Good year." : "WTF year.";
System.out.println(result);
```

### Switch
Switch เป็นคำสั่งในการเลือกทำงานของเงื่อนไขที่ตรงกันเพียงแค่เงื่อนไขเดียวเท่านั้น ซึ่งคล้ายกับการใช้ If-Else ในก่อนหน้านี้หน่ะแหละ แต่จะอยู่ในรูปแบบที่ย่อขึ้น

```java
switch(expression) {
  case x:
    // x-block
    break;
  case y:
    // y-block
    break;
  default:
    // default-block
}
```

มีความหมายเดียวกันกับ
```java
if (expression == x) {
  // x-block
} else if (expression == y) {
  // y-block
} else{
  // default-block
} 
```


เช่น
```java
int floor = 3;
switch(floor) {
	case 1:
		System.out.println("The 1st floor.");
		break;
	case 2:
		System.out.println("The 2nd floor.");
		break;
	case 3:
		System.out.println("The 3rd floor.");
		break;
	default:
		System.out.println("The " + floor + "th floor.");
}
```
เมื่อเรารัน `switch()` จะเช็คค่าที่ระบุเอาไว้ แล้วดูว่าตรงกับเงื่อนไข (Case) ไหน
ในกรณีนี้จะตรงกับ `case 3` ซึ่งจะแสดงข้อความ
> `The 3rd floor.`

**ข้อสังเกต**
- `switch` จะมีการระบุ `default` ไว้เสมอ (ซึ่งคล้ายกับการระบุ else ที่เป็นกรณีอื่น ๆ เมื่อไม่ตรงกับเงื่อนไขใด ๆ)
- ทุก ๆ case ใน `switch` จะต้องมีการ `break;` เพื่อยุติการค้นหาต่อใน `switch`

#### :smiling_imp: วิชามาร (อาจทำให้คุณปวดหัวได้)

ในแต่ละเคสสามารถใส่หลายเคสได้ เช่น


```java
String grade = "A";
switch(grade) {
  case "A":
  case "B+":
  case "B":
		System.out.println("มึงทำดีแล้ว");
		break;
  case "C+":
  case "C":
		System.out.println("พยายามขึ้นหน่อย");
		break;
  case "D":
		System.out.println("ดี ละ มึง!");
		break;
	default:
		System.out.println("ไก่จิกเด็กตายบนปากโอ่ง");
}
```

กรณีนี้คือ ถ้า grade เป็น A B+ หรือ B มันจะบอก มึงทำดีแล้ว

ถ้า grade เป็น C+ หรือ C มันจะบอก พยายามขึ้นหน่อย

ถ้า grade เป็น D มันจะบอก ดี ละ มึง!

ถ้ากรณีอื่นๆ มันจะบอก ไก่จิกเด็กตายบนปากโอ่ง


## Looping statement
### While loop
```java
while (condition) {
  // code block to be executed
}
```
`while` จะใช้สำหรับการรันโค้ตไปเรื่อย ๆ ตราบใดที่ `condition` ยังคงเป็นจริงเสมอ

เช่น
```java
int i = 0;
while (i < 10) {
  System.out.println(i);
  i++; //Add 1 to i
}
```
Loop while นี้จะจบเมื่อรันได้ 10 ครั้งเพราะ `i == 10` ทำให้เงื่อนไขใน `while` เป็นเท็จ

โดย while จะจบ loop ก็ต่อเมื่อ
- `condition` กลายเป็น**เท็จ**
- ถูกพัง loop โดย `break`


### Do-While loop
```java
do {
  // code block to be executed
}
while (condition);
```
สำหรับ do-while ก็เป็นอีกวิธีการเขียน while loop เพียงแต่นำโค้ตที่เราจะรันซ้ำไปไว้ใน `do {}` แทนและเขียนเงื่อนไขไว้ใน `while()` เช่นเดิม

เช่น
```java
int i = 0;
do {
  System.out.println(i);
  i++;
}
while (i < 10);
```

### For loop
```java
for (statement 1; statement 2; statement 3) {
  // code block to be executed
}
```
สำหรับ `for` เราจะใช้ในกรณีที่เรารู้แน่ชัดว่าโค้ตของเราจะมีการรันทั้งหมดกี่ครั้ง
โดยที่
- `statement 1` จะเป็นการรันครั้งแรกและครั้งเดียวก่อน loop จะเริ่มต้น
- `statement 2` จะเป็นเงื่อนไขในการรัน loop
- `statement 3` จะเป็นการรันหลังจากจบ loop แต่ละรอบ

เช่น
```java
for (int i = 0; i < 10; i++) {
	System.out.println(i);
}
```
ในที่นี้ จะเป็นการประกาศให้ตัวแปร `i` เป็น 0 แล้วเริ่มรัน loop จนกว่า `i < 10` จะเป็นเท็จ และทุกครั้งที่รันจะเพิ่มค่า `i` ครั้งละ 1


### For-each loop
for-each loop เป็นอีก 1 ประเภทของ for loop ที่มักจะใช้กับการวน loop ทุกตัวใน array

>ส่วน Array คืออะไร เราจะพูดใน Chapter ถัดไป

```java
for (type variableName : arrayName) {
  // code block to be executed
}
```
เช่น
```java
String[] faculty = {"EN", "SC", "MD", "PHARM", "ED", "VET", ...}; //ขอเขียนแค่นี้เพราะรู้ว่ามีอีกเยอะ
for (String i : faculty) {
  System.out.println(i);
}
```
จะเป็นการแทนให้ `i` เป็น `String` ที่แทนค่าจากค่าใน Array ของ `faculty` แต่ละตัวแล้วแสดงออกมาทีละตัว

## Branching statement
- **Break** ใช้ในการออกจาก loop ทั้งหมด (ออกเฉพาะ loop นั้น ๆ)
```java
for (int i = 0; i < 10; i++) {
  if (i == 4) { //When i == 4, loop will be break.
    break;
  }
  System.out.println(i);
}
```
- **Continue** ใช้ในการออกจาก loop เฉพาะครั้ง (กล่าวคือจะข้ามการรันโค้ตที่เหลือของ loop รอบนั้น ๆ แล้วไปที่ตัวถัดไปเลย)
```java
for (int i = 0; i < 10; i++) {
  if (i == 4) { //When i == 4, loop will be skip to 5.
    continue; //That mean loop isn't break at all, but break only for 4.
  }
  System.out.println(i);
}
```

![](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/2-1.png)


----------------------------------------
# เข้าสู่ช่วงขายของ (โจทย์ที่น่าลองจาก [Grader.ga](https://grader.ga/home/))

## if-then 
- [ข้อที่ 78 พ่อสอนลูกทำการบ้าน](https://grader.ga/problem/78)
- [ข้อที่ 21 อยากร้องเพลง](https://grader.ga/problem/21)

## while-do for

- [ข้อที่ 6 Average](https://grader.ga/problem/6)
- [ข้อที่ 10-15 Pattern 1 ถึง 6](https://grader.ga/problem/10)
- [ข้อที่ 9 การอาบน้ำของมานี](https://grader.ga/problem/9)
- [ข้อที่ 23 โรงแรมในฝัน](https://grader.ga/problem/23)




