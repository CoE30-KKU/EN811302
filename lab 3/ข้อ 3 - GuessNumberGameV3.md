# Lab 3 - Problem III : GuessNumberGameV2

ข้อนี้จะต่างจาก GuessNumberGame และ GuessNumberGameV2 เล็กน้อย
โดยผู้ใช้จะสามารถปรับการตั้งค่าของเกมได้ว่า
* ต้องการให้ค่าอยู่ในช่วง [?,?]
* ต้องการให้ลองสุ่มได้กี่ครั้ง
* สามารถเริ่มต้นใหม่ได้เรื่อย ๆ แบบไม่จำเป็นต้องรันใหม่

โดยจะมี Method `configGame()` เพิ่มขึ้นมาใน `main()`
```java
    static int correctNum;
    static int minNum, maxNum;
    static int maxTries;
    public static void main(String[] args) {
        configGame(); //Config the game.
        genAnswer(); //Generate an answer, within range of minNum and maxNum.
        playGames(); //Play it!
    }
```
และต้องประกาศ static int ของ `minNum`, `maxNum`, `maxTries` ด้วยเพื่อให้ Method `configGame()` สามารถปรับค่าแล้วนำไปใช้ต่อใน `genAnswer()` ได้เพื่อนำค่าเหล่านั้นไปเล่นต่อใน `playGames()`


สำหรับ Method `configGame()`
```java
    public static void configGame() {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter the min and the max values:");
        minNum = input.nextInt(); //The minimum range of number.
        maxNum = input.nextInt(); //The maximum range of number.
        //Case min is greater than max
        if (minNum > maxNum) {
            int temp = minNum;
            minNum = maxNum;
            maxNum = temp;
            //Case that minNum is greater than maxNum (maxNum should be the greatest).
        }
        System.out.print("Enter the number of tries:");
        maxTries = input.nextInt(); //The number of tries that user can guess.
    }
```

สำหรับ Method `genAnswer()` ที่มีการปรับให้ใช้ค่า `minNum` และ `maxNum` แทน
```java
    public static void genAnswer() {
        correctNum = minNum + (int) (Math.random() * ((maxNum - minNum) + 1));
        //Assign the correctNum with a random number within range of minNum to maxNum.
    }
```


**ข้อควรระวัง** Method `playGame()` จะเปลี่ยนถูกเรียกผ่าน `playGames()` โดยให้ `playGame()` คงรูปแบบเดิมไว้คือเป็น Method ในการรับค่าแล้วเช็คว่าถูกหรือไม่ ส่วน `playGames()` เป็น Method ในการรันเกมและเช็คหลังจากจบเกมว่าผู้ใช้ต้องการจะเล่นต่อหรือไม่


สำหรับ Method `playGames()` สำหรับรันเกมและถามผู้ใช้ว่าจะเล่นต่อหรือไม่
```java
    public static void playGames() {
        playGame();
        while(true) {
            Scanner input = new Scanner(System.in); //Get User input using Scanner.
            System.out.println("If want to play again? type 'y' to continue or 'q' to quit:");
            System.out.println("Type 'a' to see all your guesses or 'g' to see a guess on a specific play.");
            String command = input.next(); //Get what string that user input.
            if (command.equals("y")) {
                genAnswer(); //Make game generate a new answer on a new game.
                playGames(); //Recursive (loop-calling) itself to run a new game.
            } else if (command.equals("q")) {
                break; //Exit while loop, make program stop asking and exit.
            } else if (command.equals("a")) {
                showGuesses(); //Show all guesses
            } else if (command.equals("g")) {
                showSpecific(); //Show specific guess.
            }
        }
    }
```

สำหรับ Method `playGame()` สำหรับเล่นเกม (ต่อครั้ง)
```java
    public static void playGame() {
        Scanner input = new Scanner(System.in); //Get User input using Scanner.
        for (int tries = maxTries - 1; tries >= 0; tries--) { //Loop tries to make program run as times as user config.
            System.out.print("Please enter a guest (" + minNum + "-" + maxNum + "):");
            int user_guess = input.nextInt(); //Get what number that user input.

            if (user_guess > maxNum || user_guess < minNum) { //Case that user input isn't in range of minNum and maxNum.
                System.out.println("The guess number must be in the range " + minNum + " and " + maxNum);
                tries++; //Give their tries back 1 try. So, this case will not decreased remaining tries.
                continue; //continue statement will break 1 iteration in the loop, and continue with the next iteration in the loop.
            }

            if (user_guess == correctNum) { //User guess the right number
                System.out.println("Congratulations! That's correct");
                break; //Exit loop by break it.
            } else if (user_guess > correctNum) {
                System.out.println("Please type a lower number! Number of remaining tries:" + tries);  //Input is too high, advice him to lower it.
            } else if (user_guess < correctNum) {
                System.out.println("Please type a higher number! Number of remaining tries:" + tries); //Input is too low, advice him to higher it.
            }
        }
    }
```