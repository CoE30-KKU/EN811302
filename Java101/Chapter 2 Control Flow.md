# Java Control Flow

## _กำลังเขียน แปป ๆ_

โดยทั่วไปแล้ว Java จะรันโค้ตจากบนลงล่าง (Top-to-Bottom) ตามลำดับของบรรทัด โดย Control Flow จะช่วยในการเปลี่ยนการรันจากบนลงล่างให้มีความหลากหลายมากขึ้น ทั้งการใช้ Loop, การรันฟังก์ชั่นอื่น, ฯลฯ โดยจะมีอยู่ 3 ประเภทหลัก ๆ ที่ Java รองรับได้แก่:
* Decision-making statements : if-then, if-then-else, switch
* Looping statements : for, while, do-while
* Branching statements : break, continue, return

#### **สำหรับ If-then, If-then-else**
มันก็คือเจ้า if-else ปกติที่เรารู้จักกันหน่ะแหละ
```java
if (isCar) {
	System.out.println("I am a Car");
} else {
	System.out.println("I am a Truck");
}
```