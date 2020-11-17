# 1. Java Puzzle Challenges

-[1.1 Logical condition](#11-Logical-condition)
-[1.2 String Problems](#12-String-Problems)

## 1.1 Logical condition



```Java

/**
 * You are driving a little too fast, and a police officer stops you.
 * Write code to compute the fine you would have to pay.
 * If your speed is 60 or less, the result is 0 since there is no fine.
 * If speed is between 61 and 80 inclusive, the fine is 100 dollars.
 * If speed is 81 or more, the result is 200.
 * Unless it is a holiday -- on that day, your speed can be 5 higher in all cases. <br>
 * <br>
 *
 * <b>EXPECTATIONS:</b><br>
 speedingFine(60, false)  <b>---></b> 0 <br>
 speedingFine (65, false)   <b>---></b> 100 <br>
 speedingFine (65, true) <b>---></b> 0 <br>
 */
public static int speedingFine(int speed, boolean isHoliday) {

    int minSpeed = 60;
    int maxSpeed = 80;
    int fine = 0;
    if (isHoliday) {
        minSpeed += 5;
        maxSpeed += 5;
    }

    if (speed <= minSpeed) {
        fine = 0;
    }
    if (speed > minSpeed && speed <= maxSpeed) {
        fine = 100;
    }
    if (speed > maxSpeed) {
        fine = 200;
    }
    return fine;
}

System.out.println(speedingFine(60, false));
System.out.println(speedingFine(65, false));
System.out.println( speedingFine (65, true));
System.out.println( speedingFine (84, true));
System.out.println( speedingFine (86, true));
```


```Java

    /**
     * Given three ints, a b c, return true if it is possible to add two of 
     * the ints to get the third. There should only be a single line of code in the method body.<br>
     * <br> 
     *
     * <b>EXPECTATIONS:</b><br>
     twoSumOne(1, 2, 3)   <b>---></b> true <br>
     twoSumOne(3, 1, 2)    <b>---></b> true <br>
     twoSumOne(3, 2, 2) <b>---></b> false <br>
     */
    public static boolean twoSumOne(int a, int b, int c) {
        return (a + b == c) || (a + c == b) || (b + c == a);
    }
System.out.println(twoSumOne(1, 2, 3));
System.out.println(twoSumOne(3, 1, 2));
System.out.println(twoSumOne(3, 2, 2));
```


```Java
 /**
     The birds in Florida like to sing during favorable temperatures. 
     In particular, they sing if the temperature is between 60 and 90 (inclusive). 
     Unless it is summer, then the upper limit is 100 instead of 90. 
     Given an int temperature and a boolean isSummer, 
     return true if the birds are singing and false otherwise. <br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     birdsSinging(70, false)   <b>---></b> true <br>
     birdsSinging(95, false)    <b>---></b> false <br>
     birdsSinging(95, true) <b>---></b> true <br>
     */
    public static boolean birdsSinging(int temp, boolean isSummer) {
        int minTemp = 60;
        int maxTemp = 90;
         return (isSummer) ? (temp > minTemp && temp <= 100) : (temp >= minTemp && temp <= maxTemp);

    }
System.out.println( birdsSinging(70, false));
System.out.println( birdsSinging(95, false));
System.out.println( birdsSinging(95, true));
```


```Java
/**
     Given three ints, first, second, third, return true if second is greater than first, and third is 
     greater than second. However, with the exception that if the parameter "itsOk" is true, 
     second does not need to be greater than first but still better be less than third.
     <br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     isOrdered(1, 2, 4, false)   <b>---></b> true <br>
     isOrdered(1, 2, 1, false)    <b>---></b> false <br>
     isOrdered(1, 1, 2, true) <b>---></b> true <br>
*/
public static boolean isOrdered(int first, int second, int third, boolean itsOk) {
    return (itsOk && second < third) || (second > first && third > second);

}
System.out.println(isOrdered(1, 2, 4, false));
System.out.println(isOrdered(1, 2, 1, false));
System.out.println(isOrdered(1, 1, 2, false));
```


```Java
/**
 We'll say a number is cool if it's a multiple of 11 or if it is one more than a multiple of 11. 
 Return true if the given non-negative number is cool. Use the % "modulus" operator 
 we spoke about in the prerequisite section. Watch the lesson on modulus if you need to review
 <br>
 <br>
 * <b>EXPECTATIONS:</b><br>
 isCool(22)   <b>---></b> true <br>
 isCool(23)    <b>---></b> true <br>
 isCool(24) <b>---></b> false <br>
 */
 
public static boolean isCool(int n) {
    int reminder = n % 11;
    return (reminder == 0 || reminder == 1);
}

System.out.println(isCool(22));
System.out.println(isCool(23));
System.out.println(isCool(24));

```

## FizzBuzz problem



```Java
    /**
     Given an int n, return the string form of the number followed by "!". 
     So if the int is for example 13 this method should return "13!". 
     However the catch is that if the number is divisible by 3 the method should return "Fizz!" 
     instead of the number, and if the number is divisible by 5 it should return "Buzz!", 
     and if divisible by both 3 and 5, use "FizzBuzz!". You’ll need to use the % "mod" 
     for computing the remainder after division, so 23 % 10 yields 3. 

     <br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     fizzyWizzy(1)   <b>---></b> "1!" <br>
     fizzyWizzy(2)    <b>---></b> "2!" <br>
     fizzyWizzy(3) <b>---></b> "Fizz!" <br>
     */
    public static String fizzyWizzy(int n) {
        boolean fizz = (n % 3 == 0);
        boolean buzz = (n % 5 == 0);

        if (fizz && buzz) {
            return "FizzBuzz!";
        } else if (fizz) {
            return "Fizz!";
        } else if (buzz) {
            return "Buzz!";
        }
        return n + "!";
    }
    
 System.out.println( fizzyWizzy(1));
 System.out.println( fizzyWizzy(2));
 System.out.println( fizzyWizzy(3));
```


```Java

    /**

     Given 3 int arguments - a, b, c, return their sum. However, if one of the arguments 
     is the same as any of the other ones, that number should not count towards the sum. 
     So basically you only sum unique numbers, not duplicates
     <br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     sumUnique(1, 2, 3)   <b>---></b> 6 <br>
     sumUnique(3, 2, 3)    <b>---></b> 2 <br>
     sumUnique(3, 3, 3) <b>---></b> 0 <br>
     */

    public static int sumUnique(int a, int b, int c) {
        if (a == b && b == c && a == c) {
            return 0;
        }
        if (a == b) return c;
        if (a == c) return b;
        if (b == c) return a;
        return a + b + c;
    }
      System.out.println(sumUnique(1, 2, 3));
      System.out.println(sumUnique(3, 2, 3)); 
      System.out.println(sumUnique(3, 3, 3));    
```


```Java

    /**
     Given 2 positive int arguments (a, b), return whichever argument is 
     nearest to the number 21 without going over.
     Return 0 if they both go over 21. 
     <br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     nearestTwentyOne(19, 21)   <b>---></b> 21 <br>
     nearestTwentyOne(21, 19)    <b>---></b> 21 <br>
     nearestTwentyOne(19, 22) <b>---></b> 19 <br>
     nearestTwentyOne(32, 22) <b>---></b> 0 <br>
     */

    public static int nearestTwentyOne(int a, int b) {
        int targetNumber = 21;
        boolean aGoingOver = a > targetNumber;
        boolean bGoingOver = b > targetNumber;
        if (aGoingOver && bGoingOver) {
            return 0;
        }
        if (aGoingOver) {
            return b;
        }
        if (bGoingOver) {
            return a;
        }
        if (targetNumber - a <= targetNumber - b) {
            return a;
        } else {
            return b;
        }
    }
System.out.println(nearestTwentyOne(19, 21));
System.out.println(nearestTwentyOne(21, 19));
System.out.println(nearestTwentyOne(19, 22));
System.out.println(nearestTwentyOne(32, 22));
```


```Java

    /**

     Given 3 int arguments, a b c, return their sum. However, if one of the arguments is 13 
     then it does not count towards the sum and arguments to it's right do not count either. 
     So for example, if b is 13, then both b and c do not count. 
     <br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     partialSum(1, 2, 3)   <b>---></b> 6 <br>
     partialSum(1, 2, 13)    <b>---></b> 3 <br>
     partialSum(1, 13, 3) <b>---></b> 1 <br>
     */

    public static int partialSum(int a, int b, int c) {
		/*int nums[] = new int[] {a, b, c};
		int result = 0;
		for(int num: nums) {
			if(num == 13) {
				break;
			}
			result += num;
		}
		return result;
*/
        if (a == 13) return 0;
        if (b == 13) return a;
        if (c == 13) return a + b;
        return a + b + c;
    }

System.out.println(partialSum(1, 2, 3));
System.out.println(partialSum(1, 2, 13));
System.out.println(partialSum(1, 13, 3));
```

## 1.2 String Problems

### 1.2.1 Return middle 3 character from a string


```Java
 /**
     Given a string of odd length, return the middle 3 characters from the string, 
     so the string <b>"Monitor"</b> yields <b>"nit"</b>. 
     If the string length is less than 3, return the string as is. <br> <br>

     <b>EXPECTATIONS:</b><br>
     middleThree("bunny") <b>---></b> "unn" <br>
     middleThree("peter") <b>---></b> "ete" <br>
     middleThree("Jamaica") <b>---></b>"mai" <br>
     */

    public static String middleThree(String str) {
        String result = str;
        if (str.length() > 3) {
            int startIndex = (str.length() / 2) - 1;
            int endIndex = startIndex + 3; //Substring excludes endIndex so its +3
            result = str.substring(startIndex, endIndex);
        }
        return result;
    }

System.out.println(middleThree("bunny"));
System.out.println( middleThree("peter"));
```

### 1.2.2 Find the first non-repating char in a string


```Java
//String word = "hhll"; 
public void findFirstNonRepeatedChar(String word) {
Map<Character, Integer> wordCount = new LinkedHashMap<>();
char firstNonRepeatedChar=' ';
for (char ch: word.toLowerCase().toCharArray()) {
    wordCount.put( ch, wordCount.containsKey(ch) ? wordCount.get(ch) + 1: 1); 
}

for (Map.Entry<Character, Integer> entry  : wordCount.entrySet()) {
  if ( entry.getValue() == 1) {
     firstNonRepeatedChar =  entry.getKey();
     break;
  }
}
System.out.println("The first non-repeated char in the word '"+ word + "' is  "+ firstNonRepeatedChar);
}

findFirstNonRepeatedChar("hello");
findFirstNonRepeatedChar("lhlhhe");

```

    The first non-repeated char in the word 'hello' is  h
    The first non-repeated char in the word 'lhlhhe' is  e
    


```Java

```

### 1.2.3 String Recursive ("The") <b>---></b> "TThhee" <br>


```Java
/**

     Given a string, return a string where for every char in the original, append another. 
     <br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     repeatChar("The")  <b>---></b>"TThhee"<br>
     repeatChar("AAbb")    <b>---></b> "AAAAbbbb" <br>
     repeatChar("Hi-There") <b>---></b> "HHii--TThheerree" <br>
     */

    public static String repeatChar(String str) {
        if (str.length() <= 0) {
            return str;
        }
        return str.charAt(0) + String.valueOf(str.charAt(0)) + repeatChar(str.substring(1));
    }
System.out.println(repeatChar("Hi-There"));
```

### 1.2.4 String remove * and other chars immediately to it left and right "ab**cd" <b>--></b>"ad"


```Java
/**
     *
     Return a version of the given string, where for every star (*) 
     in the string the star and the chars immediately to its left and right are gone. 
     So "ab*cd" yields "ad" and "ab**cd" also yields "ad". 	<br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     starKill("cd*zq")  <b>---></b>"cq"<br>
     starKill("ab**cd")    <b>---></b> "ad" <br>
     starKill("wacy*xko") <b>---></b> "wacko" <br>
     */

    public static String starKill(String str) {
        // ab*cd
        String result = "";
        int len = str.length();
        for (int i = 0; i <= len - 1; i++) { //4
            if (i == 0 && str.charAt(i) != '*') {
                result += str.charAt(0);
            }
            if (i > 0 && str.charAt(i) != '*' && str.charAt(i - 1) != '*') {
                result += str.charAt(i);
            }
            if (i > 0 && str.charAt(i) == '*' && str.charAt(i - 1) != '*') { //a
                result = result.substring(0, result.length() - 1);
            }
        }
        return result;
    }

System.out.println(starKill("cd*zq"));
System.out.println(starKill("ab**cd"));
System.out.println(starKill("wacy*xk*"));
```


```Java


    /**
     *
     Given a string, return the length of the longest streak of the same chars in the string. 

     <br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     longestStreak("hayyeu") <b>---></b> 2<br>
     longestStreak("XPNzzzddOOOxx")  <b>---></b> 3 <br>
     longestStreak("")  <b>---></b> 0 <br>
     */

    public static int longestStreak(String str) {
        int max = 0;
        for (int  i = 0; i < str.length(); i++) {
            int count = 0;
           for (int j = 1; j < str.length(); j++ ) {
               if ( str.charAt(i) == str.charAt(j)) {
                   count++,
               } else {
                   break;
               }
           }
           if (count > max) {
               max = count;
           }
        }
        return max;
    }
    
System.out.println( longestStreak("hayyeu"));
System.out.println(longestStreak("XPNzzzddOOOxx"));
System.out.println( longestStreak("") );
   
```

## Compute no of times "yo" comes in a string (recursively)


```Java
  /**
     *
     Given a string, compute recursively (no loops) the number of times 
     lowercase "yo" appears in the string.
     <br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     yoYo("xhyoxx") <b>---></b> 1<br>
     yoYo("nyonnyon")<b>---></b> 2 <br>
     yoYo("yo")  <b>---></b> 1 <br>
     */
    public static int yoYo(String str) {
     
      if (str.length() < 2)
        return 0;
      
      if (str.substring(0, 2).equalsIgnoreCase("yo"))
        return 1 + yoYo(str.substring(1));
      else
        return yoYo(str.substring(1));  
        
    }
     
    System.out.println(yoYo("xhyoxx"));
    System.out.println(yoYo("nyonnyon"));
    System.out.println(yoYo("yo"));
```


```Java
    /**
     *
     Given a string, compute recursively a new string where all the 
     lowercase 'o' chars have been moved to the end of the string.

     <br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     endoo("oore") <b>---></b> reoo<br>
     endoo("oohoi") <b>---></b> hiooo <br>
     endoo("oanotgo") <b>---></b> antgooo <br>
     */

    public static String endoo(String str) {
        if (str.equals(""))
            return str;

        if (str.charAt(0) == 'o') {
            return endoo(str.substring(1)) + 'o';
        } else {
            return str.charAt(0) + endoo(str.substring(1));
        }
    }
    
    System.out.println( endoo("oore") );
    System.out.println(  endoo("oohoi"));
    System.out.println( endoo("oanotgo") );

```


```Java
  /**
     *

     Given a string, compute recursively a new string where identical chars 
     that are adjacent in the original string are separated from each other by a "-".

     <br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     repeatHyphen("hello") <b>---></b> hel-lo<br>
     repeatHyphen("xxyy") <b>---></b> x-xy-y <br>
     repeatHyphen("aaaa") <b>---></b> a-a-a-a <br>
     */

    public static String hyphenSplit(String str) {

         if ( str.length() < 2) {
             return str;
         }
        if (str.charAt(0) == str.charAt(1)) {
           return   (str.charAt(0) + "-" ) + hyphenSplit(str.substring(1));
        } else {
          return str.charAt(0) + hyphenSplit(str.substring(1));
        }
            
    }

System.out.println(hyphenSplit("hello"));
System.out.println(hyphenSplit("xxyy"));
System.out.println(hyphenSplit("aaaa"));
```

    hel-lo
    x-xy-y
    a-a-a-a
    


```Java
/**
     *

     Given a string that contains a single pair of brackets, compute recursively a new string made of 
     only of the brackets and their contents, so "xyz[abc]123" yields "[abc]".

     <br>
     <br>
     * <b>EXPECTATIONS:</b><br>
     insideBrackets("xyz[abc]123") <b>---></b> [abc]<br>
     insideBrackets("x[hello]") <b>---></b> [hello] <br>
     insideBrackets("[xy]1") <b>---></b> [xy] <br>
     */

    public static String insideBrackets(String str) {
        if (str.charAt(0) != '[' ) {
            return insideBrackets(str.substring(1));
        }

        if (str.charAt(str.length() - 1) != ']') {
            return insideBrackets(str.substring(0, str.length() - 1));
        }
        return str;
    }
    
System.out.println(insideBrackets("xyz[abc]123")); 
System.out.println( insideBrackets("x[hello]")); 
System.out.println(insideBrackets("[xy]1"));
    
```

    [abc]
    [hello]
    [xy]
    


```Java

```
