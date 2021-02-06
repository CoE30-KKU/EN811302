# Java Methods

`เมธอด` (หรือคล้ายๆ function หรือ def ในภาษา python) ก็คือคำสั่งเวทย์มนต์คำสั่งหนึ่งที่ใช้ในการเรียกอะไรซ้ำไปซ้ำมา

## ธัมมัยต้อกมีย์เมทอดอ่ะ~~~~~~~~~

มีเป็นล้าน ๆ เหตุผลที่เราควรเขียนโปรแกรมแบบมี`เมธอด`มาช่วยด้วยโดยข้อดีหลัก ๆ จะเป็นประมาณนี้
- มันจะทำให้โค้ดสั้นลง(ไม่มากก็น้อย)
- มันสามารถเรียกซ้ำ ๆ กี่ครั้งก็ได้
- มันทำให้โปรแกรมนั้นอ่านง่ายขึ้น(มั้ง)

เช่นตัวอย่างโปรแกรมตรงสอบว่าตัวเลขนั้น ๆ เป็นจำนวนเฉพาะหรือไม่
> No method here (Except main)
```java

public static void main(String args[]) {

    int num = 17;
    boolean isPrime = true;

    for (int i=2; i*i < num; i++) {//ลองตัวเลขและเช็คว่ามันหารลงหรือไม่
        if (num % i == 0) {//ถ้าหารลง
            isPrime = false;//แปลว่าจำนวนนั้นไม่ใช่จำนวนเฉพาะ
        }
    }

    System.out.println(num + "is prime?..." + isPrime);

    num = 15;
    isPrime = true;

    for (int i=2; i*i < num; i++) {//สังเกตุว่ามันซ้ำ
        if (num % i == 0) {
            isPrime = false;
        }
    }

    System.out.println(num + "is prime?..." + isPrime);

    num = 13;
    isPrime = true;

    for (int i=2; i*i < num; i++) {//สังเกตุว่ามันซ้ำอีกแล้ว
        if (num % i == 0) {
            isPrime = false;
        }
    }

    System.out.println(num + "is prime?..." + isPrime);

}

```
> Method version

```java
public static boolean isNumPrime(int num) {//สร้าง method ไว้เช็คว่าตัวเลขนั้นเป็นจำนวนเฉพาะหรือไม่
    boolean isPrime = true;

    for (int i=2; i*i < num; i++) {//ลองตัวเลขและเช็คว่ามันหารลงหรือไม่
        if (num % i == 0) {//ถ้าหารลง
            isPrime = false;//แปลว่าจำนวนนั้นไม่ใช่จำนวนเฉพาะ
        }
    }

    return isPrime;//ส่งผลกลับไป

}


public static void main(String args[]) {

    int num = 17;
    boolean isPrime = isNumPrime(num);

    System.out.println(num + "is prime?..." + isPrime);

    num = 15;
    isPrime = isNumPrime(num);

    System.out.println(num + "is prime?..." + isPrime);

    num = 13;
    isPrime = isNumPrime(num);

    System.out.println(num + "is prime?..." + isPrime);
}

```

สังเกตุว่าสั้นลงกว่าเดิมเยอะ โดยทั้งสองนี้มีผลลัพธ์เหมือนกันเลย
```
17 is prime?... true
15 is prime?... false
13 is prime?... true
```

## Method
ถ้านึกไม่ออกก็ลองนึกถึงกล่องเวทย์มนต์กล่องหนึ่งที่มันสามารถ**รับค่ากี่ตัวก็ได้** และ**ส่งออกกี่ตัวก็ได้**

![แมวๆๆๆๆๆ](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/4-1.PNG)

### วิธีการประกาศ Method

Method สามารถประกาศได้ดังนี้

```java
public static <ReturnValue> <Name> (<Parameter>) {
    ...
}
```
`Name` ก็ตามนั้นแหละ มันก็คือชื่อ Method นั้นๆ
`Parameter` ก็คือ สิ่งที่ Method จะรับ (หรือ จะไม่ใส่อะไรก็ได้)
`ReturnValue` ก็คือ ประเภทตัวแปรที่ Method จะคืนค่าให้ ถ้า**ไม่คืนค่าอะไรก็ให้ใส่ `void`**(ความว่างเปล่า)

เช่น

```java
public static void hello() {
    System.out.println("Wat sup meow");
}
```

> จริงๆเราสามารถเปลี่ยน public static ได้ แต่ใน Chapter ขอยังไม่พูดถึงความหมายมัน

### วิธีการเรียกใช้ Method
จริงสามารถเรียกใช้ที่ไหนก็ได้(ในเบื้องต้น) โดยวิธีการเรียกก็คือ `ชื่อ Method` และก็ `()` เช่น

```java
public static void hello() {
    System.out.println("Wat sup meow");
}

public static void main(String[] args) {
    hello();
}
```

โดยตอนนี้อาจจะงง ๆ อยู่ ดังนั้น ก็ลองศึกษา จาก ตัวอย่างกรณีศึกษา

## ตัวอย่างกรณีศึกษา

### Method ในการประกาศหัวข้อแบบ Cool ๆ

- Method นี้ จะต้องรับตัวสตริงมาหนึ่งตัว
- แค่ปริ้นออกมาในลักษณะ`================{Title}================`

> เท่ใช่ไหมล่าาาาาาา

สังเกตุว่า Method มันแค่ปริ้นออกมาเฉยๆ ดังนั้น Method จะคืนค่าเป็น `void`

```java
public static void coolTitle(String title) {
    System.out.println("================" + title + "================");
}

public static void main(String[] args) {
    coolTitle("Cal's Test")
    System.out.println("- Integral")
    System.out.println("- Integral")
    System.out.println("- Also integral")
}
```

สังเกตุว่า ยังเป็น `public static void` เหมือนเดิม(เพราะว่าฟังก์ชั่นนั้นไม่ได้ต้องการคืนค่าอะไรออกไป) แต่จะเห็นว่าในวงเล็บมันมี `String title` นั้นคือการสร้างตัวรับ `Parameter` (คล้ายประกาศตัวแปร)


```
================Cal's Test================
- Integral
- Integral
- Also integral
```

### Method ในการเรียกจำนวนเต็มเวทย์มนต์ :)

- Method นี้ ไม่รับอะไรทั้งสิ้น
- ส่งค่าออกมาเป็นตัวเลขเวทย์มนต์

```java
public static int magicNumber() {
    return 9;
    return 132;//ไม่มีผล
}

public static void main(String[] args) {
    magicNumber();
    System.out.println("-------------------");
    int magic = magicNumber();
    System.out.println("magic is " + magic);
    System.out.println("-------------------");
    System.out.println("magicNumber() is " + magicNumber());
}
```

จากตัวอย่างนี้ เราไม่เห็นคำว่า `void` แล้ว แต่เราเห็นเป็น `public static int` แทน นั้นหมายความว่า method นี้จะ**คืนค่าเป็นจำนวนเต็ม(`int`)**

จะเห็นว่า method นี้ มีการ `return` สองครั้ง (`9` และ `132`) แต่อย่างไรก็ตาม ในแต่ละ method **จะมีการ`return`แค่ 1 ครั้งเท่านั้น**ซึ่งมันจะยึดจาก **`return` แรกที่มันเจอ**

```
-------------------
magic is 9
-------------------
magicNumber() is 9
```


### Method หาค่าสูงสุด ต่ำสุด ของตัวเลขจำนวนเต็ม สอง ตัว

- Method นี้ จะต้องรับตัวเลขจำนวนเต็ม สอง ตัว ขอเรียก `a` และ `b`
- ลองเทียบตัวเลขสองตัว
- ถ้า a > b ก็ส่งค่า a ออกไป
- ถ้า a < b ก็ส่งค่า b ออกไป


```java
public static int maxNum(int a, int b) {
    if (a > b) {
        return a;
    } 
    else {
        return b;
    }
}

public static void main(String[] args) {
    maxNum(2,7);
    System.out.println("-------------------");
    int result = maxNum(9,1);
    System.out.println("max of 9 and 1 is " + result)
}
```


สังเกตุว่า `return` มันอยู่ตรงไหนก็ได้ `ใน method นั้นๆ`

```
-------------------
max of 9 and 1 is 9
```

### Method ตรวจสอบว่าจำนวนเต็มบวกนี้เป็นจำนวนเฉพาะหรือไม่

- Method นี้ จะต้องรับตัวเลขจำนวนเต็มบวกหนึ่งตัว
- ไล่หาตัวเลขตั้งแต่ 2 ไปเรื่อยๆและเช็คว่าหารลงหรือไม่
- ถ้ามีตัวเลขที่หารลงนั้นคือ ไม่ใช่จำนวนเฉพาะ
- ถ้าไม่มีที่หารลงนั้นคือ เป็นจำนวนเฉพาะ
- คืนค่าเป็น `true` และ `false`


```java
public static boolean isNumPrime(int num) {

    for (int i=2; i*i < num; i++) {
        if (num % i == 0) {
            return false;//ถ้ามันหารลงตัวนั้นคือไม่ใช่จำนวนเฉพาะแน่นอน ให้ส่งค่ากลับ
        }
    }

    return true;

}


public static void main(String args[]) {

    int num = 17;
    boolean isPrime = isNumPrime(num);

    System.out.println(num + "is prime?..." + isPrime);

    num = 15;
    isPrime = isNumPrime(num);

    System.out.println(num + "is prime?..." + isPrime);

    num = 13;
    isPrime = isNumPrime(num);

    System.out.println(num + "is prime?..." + isPrime);
}
```


```
17 is prime?... true
15 is prime?... false
13 is prime?... true
```

### Method หา หรม ของจำนวนเต็มบวกสองจำนวน(แบบง่ายๆ)

- Method นี้ จะต้องรับตัวเลขจำนวนเต็มบวกสองจำนวน
- ไล่หาตั้งแต่ ตัวเลขอะไรก็ได้ที่รับมา
- ไล่จนถึง 1
- ถ้าตัวเลขนั้นหารตัวเลขทั้งสองตัวลงตัว ตัวเลขนั้นคือ หรม ของ จำนวนเต็มบวกสองจำนวน


```java
public static int GCD(int a, int b) {

    for (int i = a ;i >= 1; i--) {
        if ( a % i == 0 && b % i == 0) {//ถ้า a และ b หารด้วย i ลง นั้นคือ i เป็น หรม
            return i;
        }
    }

    return 92387492;//IMPOSSIBLE

}


public static void main(String args[]) {

    int a = 14;
    int b = 16;
    System.out.println("GCD of " + a + " and " + b + " is " + GCD(a,b));
}
```


```
GCD of 14 and 16 is 2;
```

### Method หา ครน. ของจำนวนเต็มบวกสองจำนวน(แบบง่ายๆ)

- Method นี้ จะต้องรับตัวเลขจำนวนเต็มบวกสองจำนวน
- ใช้ทฤษฎีจำนวนมาช่วย
- ครน = a * b / หรม


```java
public static int GCD(int a, int b) {

    for (int i = a ;i >= 1; i--) {
        if ( a % i == 0 && b % i == 0) {//ถ้า a และ b หารด้วย i ลง นั้นคือ i เป็น หรม
            return i;
        }
    }

    return 92387492;//IMPOSSIBLE

}

public static int LCM(int a, int b) {

    long result = (long) a * b;
    result /= GCD(a,b);//เรียก Method หรม
    return result;

}


public static void main(String args[]) {

    int a = 14;
    int b = 16;
    System.out.println("LCM of " + a + " and " + b + " is " + LCM(a,b));
}
```


```
LCM of 14 and 16 is 112;
```

## Passing Parameters
ค่าที่เป็นตัวแปร **`Primative Data Type`(พวก int long)** *หรือ String ด้วยมั้ง* เวลาใช้ใน Function จะทำการประกาศใหม่เป็นข้อมูลของฟังก์ชั่นตัวมันเอง หรือก็คือเวลา**ค่าในฟังก์ชั่นเปลี่ยน จะไม่มีผลต่อข้างนอก**

```java
public static void changeMe(int x) {
    x = 55;
}

public static void main(String[] args) {
    int test = 12;
    System.out.println("Before Invoke " + test);
    changeMe(test);
    System.out.println("After Invoke " + test);
}
```

```
Before Invoke 12
After Invoke 12
```

*บ า ง ค รั้ ง ก็ เ ป ลี่ ย น*

```java
public static void changeMe(int[] x) {
    x[0] = 55;//เปลี่ยน อันแรกเป็น 55
}

public static void main(String[] args) {
    int[] test = {0,1,2,3};
    System.out.println("Before Invoke " + Arrays.toString(test));
    changeMe(test);
    System.out.println("After Invoke " + Arrays.toString(test));
}
```

```
Before Invoke [0, 1, 2, 3]
After Invoke [55, 1, 2, 3]
```

***ร ะ วั ง ด้ ว ย***

## Overloading Methods :smiling_imp: วิชามาร (อาจทำให้คุณปวดหัวได้)
ความสนุกของภาษา Java ก็คือ **ในคราสเดียวกัน สามารถสร้าง Method ชื่อซ้ำกันได้ ตามใดที่มี `Parameter` และประเภทการ `return` ไม่เหมือนกัน** เช่น

```java
public static int maxNum(int a, int b) {//Max num ของ int
    if (a > b) {
        return a;
    } 
    else {
        return b;
    }
}

public static double maxNum(double a, double b) {//Max num ของ double สังเกตว่าชื่อเหมือนกัน
    if (a > b) {
        return a;
    } 
    else {
        return b;
    }
}

public static int maxNum(int a, int b, int c) {//Max num ของ int 3 ตัว
    return maxNum( maxNum(a, b), c);
}
```

## Recursive Methods :smiling_imp: วิชามาร (อาจทำให้คุณปวดหัวได้)
Recursive คือการทำอะไรซ้ำไปซ้ำมา ซึ่งมีความคล้าย for do-while แต่ Recursive นั้น มันจะเป็นการ **เรียก ตัว เอง**

TIP:ลอง Search ว่า `Recursion` ก็จะเห็นปุ่ม `Did you mean: Recursion` หรือ `คุณหมายถึง Recursion` ก็ลองไปกดเล่นได้ :3

โดย Recursive จะเจอบ่อยในวิชาคณิตศาสตร์และอัลกอริทึมที่โหด ๆ

**ข้อสำคัญ : ตามที่บอกไปว่า Recursive มันคือการเรียกตัวเอง ดังนั้นให้กำหนดจุดตาย(จุดที่ไม่มีการเรียกตัวเองแต่เป็นจุดที่ส่งค่าออกมา) และต้องมั่นใจว่า การเรียกตัวเองซ้ำจะต้องถึงจุดตายได้แน่ ๆ เพราะถ้าไม่ถึงสักที มันก็จะเรียกไปเรื้อยไปอย่างไม่สิ้นสุด และทำให้เกิดสิ่งเล็กๆที่เรียกว่า Stack Overflow (เลวร้ายกว่าติด loop ใน for และ while-do)**

### Factorial
น่าจะรู้ ๆ กันอยู่ละว่า Factorial คืออะไร แต่ถ้าไม่รู้ Factorial ของ `n` มันก็คือผลคูณ `1` ถึง `n` โดยจะเขียนสัญลักษณ์ว่า `n!`

ในกรณีนี้ เราสามารถเขียนได้แบบนี้

`n!` มันก็คือ `n` * `(n-1)!`

`(n-1)!` มันก็คือ `(n-1)` * `(n-2)!`

`(n-2)!` มันก็คือ `(n-2)` * `(n-3)!`

`(n-3)!` มันก็คือ `(n-3)` * `(n-4)!`

...

`3!` มันก็คือ `3` * `2!` 

`2!` มันก็คือ `2` * `1!`

และ จบที่จุดตายนั้นก็คือ `1`

ถ้าเราลองแทนกลับไปก็จะเป็นลักษณะแบบนี้

`n!` มันก็คือ `n` * `(n-1)!`

`n!` มันก็คือ `n` * `(n-1)` * `(n-2)!`

`n!` มันก็คือ `n` * `(n-1)` * `(n-2)` * `(n-3)!`

`n!` มันก็คือ `n` * `(n-1)` * `(n-2)` * `(n-3)` * `(n-4)!`

...

`n!` มันก็คือ `n` * `(n-1)` * `(n-2)` * `(n-3)` * `(n-4)!` * ... * `3` * `2!`

`n!` มันก็คือ `n` * `(n-1)` * `(n-2)` * `(n-3)` * `(n-4)!` * ... * `3` * `2` * `1`

```java

public static int factorial(int n) {
    if (n <= 1) {//สร้างจุดตาย
        return 1;
    }
    return n * factorial(n-1);//เรียกซ้ำๆๆๆๆ
}


public static void main(String args[]) {
    System.out.println("3! is " + factorial(3));
    System.out.println("5! is " + factorial(5));
}
```

```
3! is 6
5! is 120
```

### ลำดับ fibonacci
ไม่พูดมากเจ็บคอ
`F(n) = F(n - 1) + F(n - 2)` where `F(1)` and `F(2)` is `1`

```java
public static int fibo(int n) {
    if (n <= 2) {//สร้างจุดตาย
        return 1;
    }
    return fibo(n - 1) + fibo(n - 2);//เรียกซ้ำๆๆๆๆ
}


public static void main(String args[]) {
    System.out.println("F(3) is " + fibo(3));
    System.out.println("F(5) is " + fibo(5));
    System.out.println("F(8) is " + fibo(8));
}
```

```
F(3) is 2
F(5) is 5
F(8) is 21
```