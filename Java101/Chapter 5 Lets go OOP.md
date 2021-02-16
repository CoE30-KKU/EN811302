# Java OOP
`OOP` หรือ การเขียนโปรแกรมเชิงวัตถุ ก็คือการเขียน/สร้างวัตถุใหม่ **ที่ไม่ได้มีอยู่ใน Java มาใช้งานในด้านต่าง ๆ** เพื่อให้สะดวกมากขึ้น

## ทำไมต้อง OOP
เพราะ เพราะ เพราะ!! จากประสบการณ์ที่เขียนมา มันจะทำให้โปรแกรมเราดูเป็นกลุ่มก้อนมากยิ่งขึ้น มีความเป็นระเบียบ

> ถ้าไม่เขียนแบบ OOP โปรแกรมใหญ่ ๆ อาจจะยาวถึง 2000 บรรทัดได้ เวลาบัคทีนั่งหากันมันส์เลย :)

โดยใน Chapter นี้เราจะพูดถึงแค่แบบ Basic OOP เท่านั้น จะยังไม่ลงลึก เพราะอาจทำให้หัวระเบิดได้

## Class vs Object
`Class` ก็จะคล้าย ๆ โรงงานที่สามารถสร้าง `Object`

`Object` ก็จะคล้าย ๆ ผลผลิตที่ได้มาจาก `Class` โดย `Object` จะรันนอกเหนือจากโรงงาน(`Class`) และสามารถถูกทำลายได้ หากโปรแกรมนั้น ถูกทำงาน

ตอนนี้อาจจะยังงง ๆ แต่เดี๋ยวอาจจะเห็นชัดตอนหลัง ๆ ก็ได้

## คุณสมบัติ Class และ มันทำอะไรได้บ้าง

สิ่งที่ Class ควรมีคือ
- `Attribute` หรือ `data` ก็คือข้อมูลหรือคุณสมบัติต่าง ๆ ที่ Class จะเก็บไว้ โดยจะมีกี่อันก็ได้
- `Behavior` หรือ `method` ก็คือคำสั่งต่าง ๆ ที่ Class จะให้บริการ หรือให้โปรแกรมภายนอกมาใช้ได้ โดยจะมีกี่อันก็ได้

เช่นสมมติว่าเราจะสร้าง **รถ**
- Attribute ก็ควรเป็น `ยี่ห้อ` `สี` `จำนวนรถ` `ซีซี`
- Behavior ก็ควรเป็น Method ความเร็ว(โดยเราจะเอาค่า`ซีซี`รถมาคำนวณ) หรือว่าอะไรทำนองนั้น

สมมติว่าเราจะสร้าง **ตัวฮีโร่**
- Attribute ก็ควรเป็น `ชื่อ` `เลือด` `มานา` `Atk` `Def`....
- Behavior ก็ควรเป็น โจมตี(เอาค่า `Atk` มาคำนวณ) โดนโจมตี(เอาค่า `Def` มาคำนวณ จากนั้นก็ค่อยเอาไปลบกับ `เลือด`) เป็นต้น

โดยเราสามารถเขียนได้ดังนี้
```java
public class Hero {
    //Attribute
    String name;
    double hp = 100;
    double mana = 100;
    double atk = 12.5;
    double def = 1.2;

    //Behavior
    double heroAttack() {
        return atk;
    }

    void heroGotAttacked(double damage) {
        hp -= damage / def;
    }
}
```
จะเห็นว่า Attribute ก็เหมือนประกาศตัวแปรที่เอาไว้เก็บค่าเก็บข้อมูลต่าง ๆ ส่วน Behavior ก็คือการนำ Attribute ซึ่งแน่นอนว่า มันเป็น Method

## ระดับการเข้าถึง
การเข้าถึงหลักจะมีอยู่ 4 ชนิด คือ...
| Modifier  | Class              | Package            | Subclass           | World              |
|-----------|--------------------|--------------------|--------------------|--------------------|
| public    | :white_check_mark: | :white_check_mark: | :white_check_mark: | :white_check_mark: |
| protected | :white_check_mark: | :white_check_mark: | :white_check_mark: | :x:                |
| (ไม่มี)     | :white_check_mark: | :white_check_mark: | :x:                | :x:                |
| private   | :white_check_mark: | :x:                | :x:                | :x:                |

> มันคืออะไรอีกหนอ

จำได้ไหมว่า ใน [Chapter 4](https://github.com/CoE30-KKU/EN811302/blob/master/Java101/Chapter%204%20Method.md) ตรง *`จริงๆเราสามารถเปลี่ยน modifier (อี public static) ได้ แต่ใน Chapter นี้ขอยังไม่พูดถึงมันละกัน`* คำว่า `public` นั้นแหละคือระดับการเข้าถึง 

ตัวอย่างตารางนี้คือ `public` สามารถเรียกได้จาก `Class` `Package` `Subclass` และ `World` ได้

`(ไม่มี)` สามารถเรียกได้จาก `Class` `Package` ได้ แต่ไม่สามารถเรียกจาก  `Subclass` และ `World` ได้

> แล้ว Class Package Subclass World คืออะไร

- Class ก็คือ สิ่งที่อยู่ในคราสเดียวกัน
- Package ก็คือ สิ่งที่อยู่ใน Package จึงเป็นเหตุผลว่าทำไมเวลาทำแล็ปเลยมี Package โผล่มา
- Subclass ก็คือ อยู่คนละ Package แต่มันเรียกในนาม Subclass (ส่วน Subclass คืออะไร เดี๋ยวเราค่อยพูดถึง)
- World ก็คือ โปรแกรมที่ไม่มีความสัมพันธ์อะไรเลย ไม่มี Package ไม่เป็น Subclass

มาเขียนใหม่
```java
public class Hero {
    //Attribute
    public String name;
    public double hp = 100;
    public double mana = 100;
    public double atk = 12.5;
    public double def = 1.2;

    //Behavior
    public double heroAttack() {
        return atk;
    }

    public void heroGotAttacked(double damage) {
        hp -= damage / def;
    }
}
```

> ทำไมรอบนี้ไม่มี static หละ

เดี๋ยวเราจะพูดถึงความแตกต่างระหว่างการใส่ static และไม่ใส่ static ทีหลัง

## เวลาเรียกใช้
ตอนนี้เราสร้างคราส Hero แล้ว เวลาเรียกใช้ก็เรียกตามนี้

```java
public class Meow {
    public static void main(String[] args) {
        //สร้างคราส
        Hero subaku = new Hero();

        //เวลาเรียก Attribute หรือ Behavior
        subaku.name = "Subaku";
        subaku.hp = 200.5;
        subaku.mana = 0;
        subaku.atk = 24;

        subaku.heroGotAttacked(12);

        System.out.println(subaku.name + "'s HP : " + subaku.hp);
    }
}
```

## Static vs Non-Static
Static แปลว่า คงที่ 

แต่ถ้าจะเข้าง่าย ๆ ก็คือ มันจะเป็นตัวแปรที่อยู่กับ `Class` **ไม่ได้อยู่กับ `Object`**.....งง?

ลองดูนี้
```java
public class Hero {
    public String name;
    public double hp = 100;
    public double mana = 100;
    public double atk = 12.5;
    public double def = 1.2;

    //Static
    public static String clan = "สำนักคณะกรรมการข้าราชการศาลยุติธรรม";

    public double heroAttack() {
        return atk;
    }

    public void heroGotAttacked(double damage) {
        hp -= damage / def;
    }

    //Static 
    public static String heroClan() {
        return clan;
    } 
}
```

จะเห็นว่า `clan` และ `heroClan()` เป็น static

```java
public class Meow {
    public static void main(String[] args) {
        Hero subaku = new Hero();
        Hero kumatora = new Hero();

        subaku.clan = "สำนักงานรวจแห่งชาติ";//ทำไม่ได้
        Hero.clan = "สำนักงานตำหนวดแห่งชาติ";//ทำได้
    }
}
```

จะเห็นว่าเราไม่สามารถทำ `subaku.clan = "สำนักงานรวจแห่งชาติ";` ได้ เพราะว่า `subaku` เป็น `Object` ไม่ใช่ คราส

ส่วน `Hero.clan = "สำนักงานตำหนวดแห่งชาติ";` ทำได้เพราะ `Hero` เป็น `Class`

คราวนี้ก็คงเดาได้เนอะว่าเราจะสามารถเขียน `kumatora.heroClan()` ได้หรือไม่???

<details>
    <summary>Answer</summary>
  ทำไม่ได้

  เพราะว่า `kumatora` ก็เป็น `Object` (เหมือน `subaku`)
</details>

## Constructor
Constructor ก็คือตัวสร้างนั้นแหละ

จากที่เห็นหัวข้อ [วิธีเรียกใช้](https://github.com/CoE30-KKU/EN811302/blob/master/Java101/Chapter%205%20Lets%20go%20OOP.md#method) เราจะเห็นว่าเวลาเราสร้างเสร็จแล้ว เราก็ต้องเรียก name เรียก hp ทีหลังอีก มันไม่ค่อยสวย(จริง ๆ ไม่อยากให้เรียกด้วยซ้ำ) เราจึงมีวิธีการเขียนวิธีการสร้างหรือ Constructor นั้นเอง

วิธีการเขียนก็จะคล้ายการเขียน Method เลย **แต่ไม่มีการส่งค่า(พวก int หรือ void)** และต้องตั้งชื่อ**ตามชื่อคราสด้วย** เช่น

```java
public class Hero {
    public String name;
    public double hp = 100;
    public double mana = 100;
    public double atk = 12.5;
    public double def = 1.2;
    public static String clan = "สำนักคณะกรรมการข้าราชการศาลยุติธรรม";

    public Hero() {
        hp = 200;
    }
}
```

แต่เราเรียนคอนเซ็ปท์ [OverLoading](https://github.com/CoE30-KKU/EN811302/blob/master/Java101/Chapter%204%20Method.md#overloading-methods-smiling_imp-%E0%B8%A7%E0%B8%B4%E0%B8%8A%E0%B8%B2%E0%B8%A1%E0%B8%B2%E0%B8%A3-%E0%B8%AD%E0%B8%B2%E0%B8%88%E0%B8%97%E0%B8%B3%E0%B9%83%E0%B8%AB%E0%B9%89%E0%B8%84%E0%B8%B8%E0%B8%93%E0%B8%9B%E0%B8%A7%E0%B8%94%E0%B8%AB%E0%B8%B1%E0%B8%A7%E0%B9%84%E0%B8%94%E0%B9%89) มาแล้ว ดังนั้น เราก็สามารถ OverLoading Constructor ได้เหมือนกัน

```java
public class Hero {
    public String name;
    public double hp = 100;
    public double mana = 100;
    public double atk = 12.5;
    public double def = 1.2;
    public static String clan = "สำนักคณะกรรมการข้าราชการศาลยุติธรรม";

    public Hero() {
        hp = 200;
    }

    public Hero(String heroName) {
        name = heroName;
    }

    public Hero(String heroName, double heroHP) {
        name = heroName;
        hp = heroHP;
    }
}
```
คราวนี้เวลาเรียกเราก็สามารถเรียก `Hero()` แบบไหนก็ได้

```java
public class Meow {
    public static void main(String[] args) {
        Hero subaku = new Hero("Subaku");
        Hero kumatora = new Hero("Kumatora",75);
    }
}
```

### ตัวอย่าง การนำ static มาใช้กับ Constructor
ด้วยพลังของสองอย่างนี้ จะทำให้เราสามารถสร้างตัวแปรที่เอาไว้นับจำนวนฮีโร่ที่ถูกสร้างได้
```java
public class Hero {
    public String name;
    public double hp = 100;
    public double mana = 100;
    public double atk = 12.5;
    public double def = 1.2;
    public static String clan = "สำนักคณะกรรมการข้าราชการศาลยุติธรรม";
    public static int heroNum = 0;

    public Hero() {
        hp = 200;
        heroNum++;
    }

    public Hero(String heroName) {
        name = heroName;
        heroNum++;
    }

    public Hero(String heroName, double heroHP) {
        name = heroName;
        hp = heroHP;
        heroNum++;
    }
}
```

## this nuts
หลายครั้งที่เรามักจะขี้เกียจตั้งชื่อตัวแปรใหม่ เราก็เลยอาจเขียนในลักษณะนี้
```java
public class Hero {
    public String name;
    public double hp = 100;
    public double mana = 100;
    public double atk = 12.5;
    public double def = 1.2;
    public static String clan = "สำนักคณะกรรมการข้าราชการศาลยุติธรรม";
    public static int heroNum = 0;

    public Hero() {
        hp = 200;
        heroNum++;
    }

    public Hero(String name) {
        name = name;
        heroNum++;
    }

    public Hero(String name, double hp) {
        name = name;
        hp = hp;
        heroNum++;
    }
}
```
> งงดิ name = name; hp = hp;
โปรแกรมก็งง(มั้ง) อย่างอันนี้ความหมาย `name` ด้านขวา ก็คือชื่อที่ผู้เขียนใส่เข้ามา ส่วน `name` ด้านซ้ายคือ `name` ที่เป็น Attribute ในคราสนี้ ซึ่งเราสามารถระบุว่า `name` อันนี้คือของคราสได้ โดยการใส่ `this.`name เข้าไป โปรแกรมก็จะเข้าใจว่า `this.name` คือ `name` ของคราส

```java
public class Hero {
    public String name;
    public double hp = 100;
    public double mana = 100;
    public double atk = 12.5;
    public double def = 1.2;
    public static String clan = "สำนักคณะกรรมการข้าราชการศาลยุติธรรม";
    public static int heroNum = 0;

    public Hero() {
        hp = 200;
        heroNum++;
    }

    public Hero(String name) {
        this.name = name;
        heroNum++;
    }

    public Hero(String name, double hp) {
        this.name = name;
        this.hp = hp;
        heroNum++;
    }
}
```

## Encapsulation
แปลว่า การใส่ในแค็ปซูล ในที่นี้คือการทำให้คราสเรา **ปกปิด Attribute ทุกอย่าง** เวลาที่โลกภายนอกต้องการข้อมูล ให้**เรียกผ่าน Behavior**เอา เพื่อที่เราจะได้สามารถควบคุมข้อมูลได้ว่า ส่วนไหนให้คนอื่นรู้ ส่วนไหนที่คนอื่นไม่ควรรู้

```java
public class Hero {
    private String name;
    private double hp = 100;
    private double mana = 100;
    private double atk = 12.5;
    private double def = 1.2;
    private static String clan = "สำนักคณะกรรมการข้าราชการศาลยุติธรรม";
    private static int heroNum = 0;

    public Hero() {
        hp = 200;
        heroNum++;
    }

    public Hero(String name) {
        this.name = name;
        heroNum++;
    }

    public Hero(String name, double hp) {
        this.name = name;
        this.hp = hp;
        heroNum++;
    }

    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
}
```
จะเห็นว่า พวก Attribute เป็น private ทั้งหมด ซึ่งเราก็จะไม่สามารถเรียกข้างนอกได้ละ แต่เราสามารถเรียกผ่าน `getName()` `setName()` ได้

จริง ๆ เราสามรถเขียนได้ทุกอันเลย แต่มันจะยาวเกินไป

## Override
ตอนนี้ถ้าเราลองเรียกใช้

![แมวๆๆๆๆๆ](https://raw.githubusercontent.com/CoE30-KKU/EN811302/master/Java101/Res/5-1.PNG)

จะเห็นว่า เราไม่ได้สร้าง Method `toString()` หรือ `wait()` แต่มันก็โผล่มาให้เราใช้ อยู่ดี เพราะเวลาเราสร้าง class มันจะมี Method ที่ Java มันสร้างมาให้โดยอัตโนมัติ(และเราก็มองไม่เห็นด้วย) แต่ที่ Java มันสร้างมาให้ก็ไม่ค่อยที่จะดีนัก เราจึงมีคอนเซ็ป Override เกิดขึ้น

Override คือการขี่ทับอันเก่า ในที่นี้คือการสร้าง Method อันใหม่มาทับอันเก่า***(ไม่เหมือนกับ Overload นะๆๆๆๆๆ)***

เช่นถ้าเราลอง

```java
public class Meow {
    public static void main(String[] args) {
        Hero kumatora = new Hero("Kumatora",75);
        System.out.System(kumatora);
    }
}
```
มันจะออกประมาณว่า...
```
Hero@73a28541
```
ภาษาเอเลี่ยน! จริงๆมันมีความหมายอยู่ แต่เราจะยังไม่พูดถึงปีนี้

```java
public class Hero {
    private String name;
    private double hp = 100;
    private double mana = 100;
    private double atk = 12.5;
    private double def = 1.2;
    private static String clan = "สำนักคณะกรรมการข้าราชการศาลยุติธรรม";
    private static int heroNum = 0;

    public Hero() {
        hp = 200;
        heroNum++;
    }

    public Hero(String name) {
        this.name = name;
        heroNum++;
    }

    public Hero(String name, double hp) {
        this.name = name;
        this.hp = hp;
        heroNum++;
    }

    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return this.name + " [HP : " + this.hp + "]";
    }
}
```
พอเราลอง

```java
public class Meow {
    public static void main(String[] args) {
        Hero kumatora = new Hero("Kumatora",75);
        System.out.System(kumatora);
    }
}
```
มันจะออก
```
Kumatora [HP : 75]
```

## Inheritance
*Coming soon*
