# Lab 3 - Problem II : GuessNumberGameV2

ข้อนี้จะต่างจาก GuessNumberGame เล็กน้อย

โดยให้สร้าง Method ในการสุ่มเลข และ Method ในการเล่นเกมแยกออกมาจาก `main()`

โจทย์ให้ใน Method `main()` รันแค่สองโค้ตเท่านั้นคือ 
```java
    static int correctNum; //correctNum is a variable used to be an answer of the game.
    public static void main(String[] args) {
        genAnswer(); //Generate the answer.
        playGame(); //Play it!
    }
```
และโจทย์สั่งให้ประกาศ static int ของ `correctNum` ไว้ด้วย


สำหรับ Method ในการสุ่มเลข
```java
    public static void genAnswer() {
        correctNum = 1 + (int) (Math.random() * ((10 - 1) + 1)); //Assign the correctNum with a random number within range of 1 to 10.
    }
```
จะเป็นการเปลี่ยนค่า `correctNum` ที่เป็น static int โดยสุ่มเลขแทนค่าให้ระหว่าง [minNum,maxNum] ตามที่อธิบายฟังก์ชั่น `Math.random()` ไปแล้วก่อนหน้านี้

สำหรับ Method ในการเล่นเกม
```java
    public static void playGame() {
        Scanner input = new Scanner(System.in); //Get User input using Scanner.
        for (int tries = 2; tries >= 0; tries--) { //Loop tries to make program run 3 times.
            System.out.print("Please enter a guest (1-10):");
            int user_guess = input.nextInt(); //Get what number that user input.
            if (user_guess == correctNum) { //User guess the right number.
                System.out.println("Congratulations! That's correct");
                break; //Exit loop by break it.
            } else if (user_guess > correctNum) {
                System.out.println("Please type a lower number! Number of remaining tries:" + tries); //Input is too high, advice him to lower it.
            } else if (user_guess < correctNum) {
                System.out.println("Please type a higher number! Number of remaining tries:" + tries); //Input is too low, advice him to higher it.
            }
        }
    }
```
ก็คล้ายกับใน GuessNumberGame แต่จะใช้ค่า `correctNum` จาก static int ที่ประกาศไว้และได้รับการสุ่มจาก `genAnswer()` แทน
