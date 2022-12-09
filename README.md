### Task №1(8 kyu)

Note: This kata is inspired by Convert a Number to a String!. Try that one too.

Description
We need a function that can transform a string into a number. What ways of achieving this do you know?

Note: Don't worry, all inputs will be strings, and every string is a perfectly valid representation of an integral number.

~~~ Java
Examples
"1234" --> 1234
"605"  --> 605
"1405" --> 1405
"-7" --> -7
~~~

[Task_link](https://www.codewars.com/kata/544675c6f971f7399a000e79)

#### Solution

~~~ Java
public class StringToNumber {
    public static int stringToNumber(String str) {
        return Integer.parseInt(str);
    }
}
~~~

#### Fav Solution

~~~ Java
public class StringToNumber {
  public static int stringToNumber(String str) {
    int i = 0;
    int num = 0;
    boolean isNeg = false;

    if (str.charAt(0) == '-') {
        isNeg = true;
        i = 1;
    }

    while( i < str.length()) {
        num *= 10;
        num += str.charAt(i++) - '0'; 
    }

    if (isNeg) {
        num = -num;
    }
    
    return num;
  }
}

~~~

### Task №2 (7 kyu)

Task:
Your task is to write a function which returns the sum of following series upto nth term(parameter).

~~~ Java
Series: 1 + 1/4 + 1/7 + 1/10 + 1/13 + 1/16 +...
~~~

Rules:
You need to round the answer to 2 decimal places and return it as String.

If the given value is 0 then it should return 0.00

You will only be given Natural Numbers as arguments.

~~~ Java
Examples:(Input --> Output)
1 --> 1 --> "1.00"
2 --> 1 + 1/4 --> "1.25"
5 --> 1 + 1/4 + 1/7 + 1/10 + 1/13 --> "1.57"
~~~

[Task_link](https://www.codewars.com/kata/555eded1ad94b00403000071)

#### Solution

~~~ Java
public class NthSeries {
    public static String seriesSum(int n) {
        int result = 0;
        int reverage = 1;
        for (int i = 0; i < n; i++) {
            if (i == 0) {
                result = 1;
            } else {
                reverage += 3;
                result = result + (1 / reverage);
            }
        }
        return String.format("%.2f", result);
        // Happy Coding ^_^
    }
}
~~~

#### Fav Solution

~~~ Java
import java.util.stream.IntStream;

public class NthSeries {
	
	public static String seriesSum(int n) {
        return String.format("%.2f", IntStream.range(0, n).mapToDouble(num -> 1.0 / (1 + num * 3)).sum());
    }
}
~~~