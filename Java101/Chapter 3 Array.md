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
![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-1.PNG)

ถ้่าเราลอง `char[] newOTOG = OTOG;` มันจะเกิดสิ่งนี้

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-2.PNG)

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

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-3.PNG)

### ตัวอย่างการนำไปใช้

#### การหาตัวเลขต่ำสุด/สูงสุด
จริงๆภาษา Java ใน Arrays ก็มีบริการการหาค่าสูงสุดและต่ำสุดอยู่แล้ว แต่ถ้าวันหนึ่ง หัวคุณดันไปชนกับผนังจนลืม ถ้าเข้าใจหลักการนี้ได้ ก็จะสามารถเขียนได้แทบทุกภาษาเลย โดยในที่นี้ขอยกตัวอย่างการหาตัวเลขที่**สูงสุด**

หลักการคือ
ให้`คำตอบ`คือสมาชิกตัวแรก
จากนั้นตั้งแต่สมาชิกตัวที่สองเป็นต้นไปให้ทำการ**เปรียบเทียบระหว่าง `ตัวเลขนั้นๆ` กับ `คำตอบ`** หากตัวเลขนั้นๆดันมีค่า**มากกว่า** ก็ให้ใส่ใน`คำตอบ`

ตัวอย่างการเขียนโค้ด

```java
int[] nums = {1,7,2,8,9};
int ans = nums[0];
for (int i = 1; i < nums.length; i++) {//ไล่ตั้งแต่ตัวที่สอง
    if(nums[i] > ans){//เปรียบเทียบกลับตัวเก่า(กรณีนี้คือ ถ้ามากกว่า)
        ans = nums[i];//ใส่ในคำตอบ
    }
}
```

#### การหาข้อมูลแบบวิธี Linear Search
มันก็คือวิธีการหาข้อมูลว่ามันมีหรือเปล่า

หลักการ(ง่ายๆ)คือ
ไล่แม่งทุกตัวเลย แล้่วก็ค่อยเช็คว่าแต่ละตัวนั้นคือสิ่งที่หาหรือเปล่า

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-10.PNG)

ตัวอย่างการเขียนโค้ด

```java
int[] nums = {1,7,2,8,9};
int find = 8;
boolean isFound = false;
for (int i = 0; i < nums.length; i++) {//ไล่แม่งทุกตัวเลย
    if(nums[i] == nums){//ลองดูว่าใช่หรือเปล่าน้าาาา
        isFound = true;//เจอแว้วววววว
    }
}
```

ถ้าใครเซียนๆหน่อยก็ใส่ `break;` ตอนเจอแล้วก้ได้ จะได้เร็วขึ้น

> วิธีนี้ดีไหม
ดี เพราะมันง่าย และตรงไปตรงมา

แต่ๆๆๆๆ ข้อเสียคือ ***ช้า***

> ทำไมช้า
ถ้าเราหาเจอมันก็จะใช้เวลาไม่นานขนาดนั้น

แต่ถ้าเราหา**ไม่เจอ** มันก็จะต้อง**ไล่หาเท่ากับจำนวนของข้อมูล** ถ้ามี 10 20 ตัวก็ไม่เป็นไรหรอก แต่ถ้ามันดันมีเป็นล้าน สิบล้าน และแย่กว่านั้นคือ ถ้าไม่ได้ถามแค่ครั้งเดียวหล่ะ มันก็จะนานโคตรๆๆๆๆ

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-11.PNG)

#### การหาข้อมูลแบบวิธี Binary Search(การค้นหาแบบทวีภาค)
คือวิธีการหาข้อมูลที่**เร็วที่สุดในโลกแล้วววววววววว** แต่มีเงื่อนไขเดียวคือ **ข้อมูลจะต้องเรียงให้ถูกต้องก่อน**

หลักการเทพๆคือ
ทำการจิ้มไปตรง**กลาง** แล้วค่อยดูว่าตรงกลางมันใช่สิ่งที่เราหาหรือเปล่า ถ้าใช้ ก็เจอ แต่ถ้าไม่ใช่ ค่อยดูว่าระหว่าง**ตรงกลางกับสิ่งที่หานั้น อยู่ฝั่งไหน** แล้วค่อยหาต่อ....งง

ยกตัวอย่างเวลาเรียก `binarySearch`

```java
int[] nums = {1,2,7,8,9};
int find = 8;
boolean isFound = (Arrays.binarySearch(nums, find) >= 0);
```

ก็จิ้มไปตรงกลาง

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-4.PNG)

จะเห็นว่ามันจิ้มเลข `7` ซึ่งไม่ใช่เลข `8` แล้ว `8` จะอยู่ฝั่งไหนหล่ะ?

เป็นเรื่อง Common sense อยู่แล้วว่าต้องอยู่ฝั่งขวาแน่ๆ เพราะ เรา**เรียงตัวเลขแล้ว** **ฝั่งซ้าย** ก็ต้องเป็นตัวเลขที่**น้อยกว่า `7`** อยู่แล้วส่วน**ฝั่งขวา**ก็ต้องเป็นตัวเลขที่**มากกว่า `7`** อยู่แล้ว จะรออะไรหล่ะ ก็หา**ฝั่งขวาต่อ**

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-5.PNG)

จะเห็นว่ามันจิ้มเลข `8` พอดี

มาลองในกรณีที่หาไม่เจอ(ลองหาเลข 3) 
```java
int[] nums = {1,2,7,8,9};
int find = 3;
boolean isFound = (Arrays.binarySearch(nums, find) >= 0);
```

ก็จิ้มไปตรงกลาง

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-4.PNG)

จะเห็นว่ามันจิ้มเลข `7` ซึ่งไม่ใช่เลข `3` ก็หาฝั่ง**ซ้าย**ต่อ

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-6.PNG)

จะเห็นว่ามันจิ้มเลข `1` ซึ่งไม่ใช่เลข `3` ก็หาฝั่ง**ขวา**ต่อ

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-7.PNG)

จะเห็นว่ามันจิ้มเลข `2` ซึ่งไม่ใช่เลข `3` ก็หาฝั่ง**ขวา**ต่อ

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-8.PNG)

ปรากฏว่ามันไม่มีอะไรให้หาต้อแล้วแสดงว่ามันหาไม่เจอ

ตัวอย่างการใช้งาน

```java
int[] nums = {1,2,7,8,9};
int find = 3;
int isFound = Arrays.binarySearch(nums, find);
```

คำสั่ง `Arrays.binarySearch` จะไม่ได้คืนค่าเป็น `Boolean`(จริงเท็จเท็จจริง) แต่จะทำการคือเป็นตัวเลขตำแหน่ง แต่มีหลักการง่ายๆคือ ถ้าเป็นจำนวน**เต็มบวกหรือ 0** นั้นคือ**เจอ** ถ้ามัน**ติดลบ**มันก็คือ**ไม่เจอ**

>แล้ว วิธีนี้มันดีกว่ายังไง

จะเห็นว่าในระหว่างการหาของ binary search มันทำก่ารค่อยๆแบ่งครึ่งๆๆๆๆๆ ดังนั้น จำนวนครั้งที่แย่สุดก็คือ จำนวนการค่อยๆแบ่งครี่งๆๆๆจนมันแบ่งต่อไม่ได้แล้ว นั้นคือ ![Ceil(log(2;n))](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-9.PNG) เมื่อ n คือจำนวนข้อมูล

ก็เทียบโง่ๆ เลย มีข้อมูล `1000000` ตัว `Linear Search` หารอบนึงใช้เวลา `1000000` ครั้ง แต่ `Binary Search` ใช้เวลา `20` ครั้ง (ว้าวซ่า)

**อย่าลืมว่าก่อนจะหา Binary Search ต้องทำการเรียงข้อมูลก่อน**

**`Arrays.binarySearch` มีไว้หาเฉยๆ ไม่เรียงให้**

#### การเรียงข้อมูล
จากที่เรารู้แล้วว่า Binary Search นั้นใช้เวลาที่น้อยโคตรๆ แต่ก็มีข้อจำกัดอยู่หนึ่งอย่างก็คือ ต้อง**เรียงข้อมูลก่อน** โดยในเอกสารนี้จะเสนอแค่ 3 วิธี(ปกติมันมีเยอะมากๆๆๆๆๆ)

##### การเรียงข้อมูล โดยวิธี Insertion Sort
Insertion แปลว่า ~~เสียบ~~แทรก ดังนั้นวิธีนี้คือการแทรกเพื่อเรียง

หลักการง่ายๆ คือ ทุกตัวจะถูกหยิบและเช็คตัวด้านซ้าย ถ้ามีค่าน้อยกว่าก็ทำซ้ำไปเรื่อยๆ จนกว่าจะมีค่ามากกว่าฝั่งซ้าย...งง? ลองดูรูปต่อไปนี้

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-12.PNG)

เพราะ `42` อยู่ด้่านซ้ายอยู่แล้ว จึงไม่มีค่า(ฝั่งซ้าย)ให้เทียบ

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-13.PNG)

จะเห็นว่า `20` น้่อยกว่า `42` ดังนั้น ก็**แทรกมันซะ**

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-14.PNG)

แทรกสำเร็จแล้วก็ดูตัวต่อไป

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-15.PNG)

จะเห็นว่า `14` นั้นน้่อยกว่า `42` และก็น้อยว่า `20` ดังนั้น ก็**แทรกมันซะ**

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-16.PNG)

แทรกสำเร็จแล้วก็ดูตัวต่อไป

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-17.PNG)

จะเห็นว่า `13` นั้นน้่อยกว่า `42` น้อยว่า `20` และก็น้อยว่า `14` ดังนั้น ก็**แทรกมันซะ** แล้วก็ดูตัวต่อไป

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-18.PNG)

จะเห็นว่า `28` นั้นน้่อยกว่า `42` แต่ยังมากกว่า `20` ดังนั้น**ก็แทรกแค่หลัง `20`**

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-19.PNG)

แทรกสำเร็จแล้วก็ดูตัวต่อไป(ขอแบบเร็วๆ)

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-20.PNG)

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-21.PNG)

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-22.PNG)

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-23.PNG)

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-24.PNG)

>ว้าวซ่ามันเรียงให้แล้วว

##### การเรียงข้อมูล โดยวิธี Select Sort
Select แปลว่า เลือก ดังนั้นวิธีนี้คือการค่อยๆเลือกแล้วก็เรียง

หลักการง่ายๆ คือ ในทุกๆต่ำแหน่ง จะทำการหาตัวเลขที่น้อยที่สุด(ที่ไม่ใช่ฝั่งซ้ายของตำแหน่งมันเอง)มาสลับในตำแหน่งมันเอง


ลองดูรูปต่อไปนี้
![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-25.PNG)

มาเริ่มที่ตำแหน่งแรก (`42`) ตัวเลขที่น้อยที่สุดคือ `13` ดังนั้นก็สลับ `42` และ `13`

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-26.PNG)

สลับแล้วก็หาตัวเลขที่น้อยที่สุดตั้งแต่ `20`

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-27.PNG)

ตัวเลขที่น้อยที่สุดคือ `14` ดังนั้นก็สลับ `20` และ `14`

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-28.PNG)

สลับแล้วก็หาตัวเลขที่น้อยที่สุดตั้งแต่ `17` ขอแบบเร็วๆ
![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-29.PNG)

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-30.PNG)

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-31.PNG)

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-32.PNG)

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-33.PNG)

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-34.PNG)

![รูปภาพอันสวยงาม](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/3-35.PNG)


>ว้าวซ่ามันเรียงให้แล้วว

##### การเรียงข้อมูล โดยใช้คำสั่งในภาษา Java
จะเห็นว่าวิธี Insertion Sort และ Select Sort เป็นวิธีเรียงที่เข้าใจง่าย(มั้ง) แต่ข้อเสียก็ตามนั้นก็คือ ช้า นั้น เอง (ขออนุญาตไม่พิสูจน์ว่าทำไมมันช้า) เขียนก็ยาก ดังนั้นเลยเสนอวิธีสุดท้ายก็คือ `Arrays.sort`

ตัวอย่าง
```java
int[] nums = {3,5,1,2,9};
Arrays.sort(nums);
```

> จบเลย

แล้วเราจะเรียน Insertion Sort กับ Select Sort ไปธัมมัย

นั้นสิคิดเหมือนกัน แต่บางครั้งเราอย่างเรียงอะไรแปลกๆ เช่น เรียงจากมากไปน้อย เรียงเฉพาะเลขคู่ เราจะเขียนได้ยังไง

ลองไปคิดหรือไม่ก็ค้นหาในเน็ต(Sort Comparator)ได้ 

> ขาย ตรง :3

----------------------------------------
# เข้าสู่ช่วงขายของ (โจทย์ที่น่าลองจาก [Grader.ga](https://grader.ga/home/))

## Array
- [ข้อที่ 1 อนุพันธ์ในอาเรย์](https://grader.ga/problem/1)
- [ข้อที่ 2 ค่าเฉลี่ยและความแปรปรวน](https://grader.ga/problem/2)
- [ข้อที่ 6 Average](https://grader.ga/problem/6)
- [ข้อที่ 26 เพลงรักลมหนาวนิ](https://grader.ga/problem/26)
- [ข้อที่ 59 ฟุตฟิตฟอไฟ](https://grader.ga/problem/59)
- [ข้อที่ 70 ปลาทูของแมวน้อย](https://grader.ga/problem/70)
- [ข้อที่ 80 เบี้ยอักษร CoE](https://grader.ga/problem/80)

## Binary Search

- [ข้อที่ 67 ไบนารีเสิร์ช](https://grader.ga/problem/67)
- [ข้อที่ 68 ไบนารีเสิร์ช เมพ](https://grader.ga/problem/68)
- [ข้อที่ 69 โปรแกรมตัดเกรด](https://grader.ga/problem/69)
- [ข้อที่ 76 Hiking](https://grader.ga/problem/76)

## Sort

- [ข้อที่ 60-66 Sort 1 ถึง 7](https://grader.ga/problem/60)