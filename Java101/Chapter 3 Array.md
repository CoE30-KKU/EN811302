# Java Array

เราจะใช้ Array ในการเก็บข้อมูลหลาย ๆ ค่าในตัวแปรตัวแปรเดียว _(คล้ายกับการใช้ list ใน python)_

ในการประกาศให้ตัวแปรเป็น Array เราจะเติม `[]` ไว้ข้างประเภทของตัวแปร
```java
String[] meow = {"Meow", "meow", "MEOW", "MEOWWWWWWWWWWWWWWWWW"};
int[] num = {1, 2, 3 ,4, 5};
```
จะทำให้ตัวแปร `meow` มีค่าที่ถูกเก็บเอาไว้ข้างในมันอยู่ 4 ค่าย่อย โดยเป็น `String` ทั้งหมด

ในทางเดียวกันก็จะทำให้ตัวแปร `num` มีค่าที่ถูกเก็บเอาไว้ข้างในมันอยู่ 5 ค่าย่อย โดยเป็น `int` ทั้งหมด

### **Array Accessing**
ในการเข้าถึงค่าที่เก็บเอาไว้ใน Array เราจะใช้การบอกตำแหน่งใน `[]` เพื่อระบุว่าเราจะดูค่าในตำแหน่งที่เท่าไหร่

**NOTE**: Java เริ่มนับตำแหน่งที่ 0 ถึง n-1

เช่นถ้าหาก Array เรามีข้อมูลอยู่ 4 ตัว ข้อมูลจะอยู่ที่ตำแหน่งที่ 0, 1, 2, 3

เช่น
```java
String[] meow = {"Meow", "meow", "MEOW", "MEOWWWWWWWWWWWWWWWWW"};
System.out.println(meow[2]);
```
เราจะได้ค่าออกมาเป็น
> MEOW

### **Array Changing**
และเรายังสามารถเปลี่ยนค่าใน Array ได้ด้วย โดยการใช้การบอกตำแหน่งเช่นกัน
```java
String[] meow = {"Meow", "meow", "MEOW", "MEOWWWWWWWWWWWWWWWWW"};
meow[2] = "MEOW~~"; //meow = {"Meow", "meow", "MEOW~~", "MEOWWWWWWWWWWWWWWWWW"}
```
เพียงแค่นี้ ก็จะเป็นการเปลี่ยนให้ `meow[]` ในตำแหน่งที่ `3` (หรือเดิมคือ `MEOW`) เปลี่ยนเป็น `MEOW~~`

### **Multidimensional Arrays**
สำหรับ Array หลายมิติคล้ายกับการซ้อน Array ไว้ใน Array อีกที
เช่น ในการสร้าง 2D-Array
```java
int[][] num = { {1, 2, 3, 4}, {5, 6, 7} };
```
จะทำให้ num เป็น Array ที่มี Array 2 Array เป็นสมาชิก

สำหรับการเรียกใช้ ก็จำเป็นจะต้องระบุตำแหน่งเหมือนเดิม แต่จะแตกต่างเล็กน้อย
```java
int[][] num = { {1, 2, 3, 4}, {5, 6, 7} };
int x = num[1][2];
System.out.println(x); // Outputs 7
```
จาก `num[1][2]`
- `[1]` ตัวแรกจะเป็นการบอกว่าเป็น Array ตัวไหน (ซึ่งคือตัวที่สอง `{5,6,7}`)
- `[2]` ตัวถัดมาจะเป็นการบอกว่าเป็น Array ตัวไหนของ Array ที่เลือกมาก่อนหน้านี้ (จาก `{5,6,7}` -> ตัวที่ 3 คือ 7)


ดังนั้นผลลัพธ์จึงออกมาเป็น
> 7

### ข้อควรระวังเวลาคัดลอก Array
สมมติว่าเรามี Array อันหนึ่ง แล้วเรามี Array อีกอันที่จะคัดลอก เราก็อาจจะสามารถทำแบบนี้ได้

```java
int[] arrayFirst = {1,4,6,5,3};
int[] arraySecond = arrayFirst;
```

ลองปริ้นๆ

```java
System.out.println(Arrays.toString(arrayFirst));
System.out.println(Arrays.toString(arraySecond));
```

```
[1,4,6,5,3]
[1,4,6,5,3]
```

EZ ......แต่ๆๆๆๆๆถ้าเราลองเปลี่ยนค่าเปลี่ยนค่า

```java
int[] arrayFirst = {1,4,6,5,3};
int[] arraySecond = arrayFirst;
arrayFirst[2] = -420;
System.out.println(Arrays.toString(arrayFirst));
System.out.println(Arrays.toString(arraySecond));
```

ก็จะได้
```
[1,4,-420,5,3]
[1,4,-420,5,3]
```

WUT!? ทั้งๆที่เราแก้แค่ `arrayFirst` ไม่ได้แก้ `arraySecond` แต่ดันมีผลกลับ `arraySecond` ด้วย นั้นเพราะว่า...

#### :smiling_imp: วิชามาร (อาจทำให้คุณปวดหัวได้)
เวลาเราสร้าง Array ตัวนึง
ในความจำของคอมพิวเตอร์จะออกมาเป็นลักษณะนี้

```java
char[] OTOG = new char[] {'O','T','O','G'};
```
![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-1.png)

ถ้่าเราลอง `char[] newOTOG = OTOG;` มันจะเกิดสิ่งนี้

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-2.png)

จะเห็นว่าหน่วยความจำดันชี้ช่องเดียวกัน ดังนั้นไม่แปลกที่จะเปลี่ยนค่าใน Array นึงแล้วมีผลกับอีกอัน

### เวลาคัดลอก Array(ต่อ)
วิธีที่ 1 ประกาศใหม่ แล้วก็ก็อบทีละค่า
```java
char[] OTOG = new char[] {'O','T','O','G'};
char[] NewOTOG = new char[OTOG.length];
for (int i = 0; i < OTOG.length; i++) {
    NewOTOG[i] = OTOG[i];
}
```

วิธีที่ 2 ใช้บริการของ Arrays
```java
char[] OTOG = new char[] {'O','T','O','G'};
char[] NewOTOG = OTOG.clone();
```

วิธีที่ 3 ใช้บริการของ Arrays แบบ 2
```java
char[] OTOG = new char[] {'O','T','O','G'};
char[] NewOTOG = Arrays.copyOf(OTOG, OTOG.length);
System.out.println("H");
```

>จริงๆอาจจะมีหลายวิธีอยู่ อันนี้เป็นเพียงแค่การยกตัวอย่างเท่านั้น

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-3.png)

### ตัวอย่างการนำไปใช้
TODO


