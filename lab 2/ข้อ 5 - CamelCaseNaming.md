# Lab 2 - Problem V : CamelCaseNaming

ข้อนี้เป็นการเปลี่ยนตัวอักษรตัวแรกของแต่ละคำให้เป็นพิมพ์ใหญ่ แล้วนำมาต่อกันตามกฎ Camel Case

```java
public class CamelCaseNaming {
    public static void main(String[] args) {
        if (args.length > 0 && args.length <= 2) {
            String firstWord = args[0];
            String camelCaseNaming = "";
            if (args.length == 1) { //กรณีมี 1 คำ
                System.out.println(camelCaseConvertor(firstWord));
            } else { //กรณีมี 2 คำ
                String secondWord = args[1];
                System.out.println(camelCaseConvertor(firstWord) + camelCaseConvertor(secondWord));
            }
        } else {
            System.err.println("CamelCaseNaming <first word> <second word> ...");
        }
    }

    public static String camelCaseConvertor(String str) {
        char[] ch = str.toCharArray(); //แปลง String ให้เป็น Char Array
        if (str.length() > 0)
            ch[0] = str.toUpperCase().charAt(0); //ปรับให้ตัวแรกเป็นพิมพ์ใหญ่
        return new String(ch); //ส่งค่ากลับเป็น String
    }
}
```