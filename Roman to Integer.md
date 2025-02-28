## Roman to Integer

Given a roman number in the form of string, your task is to find out the integer(decimal) number from roman number.

### java code
```

import java.io.*;
import java.util.*;
class Main {
    public static void main(String[] args) throws InterruptedException {
        Scanner sc = new Scanner(System.in);
        String s = sc.next();
        Map<Character, Integer> map = new HashMap<>();
        map.put('I',1);
        map.put('V',5);
        map.put('X',10);
        map.put('L',50);
        map.put('C',100);
        map.put('D',500);
        map.put('M',1000);
        int sum=0;
        for(int i=0; i<s.length()-1; i++){
            char ch = s.charAt(i);
            char ch2 = s.charAt(i+1);
            if(map.get(ch)<map.get(ch2)){
                sum-=map.get(ch);
            }else{
                sum+=map.get(ch);
            }
        }
        sum+=map.get(s.charAt(s.length()-1));
        System.out.print(sum);
    }
}
