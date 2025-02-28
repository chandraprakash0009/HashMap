## Integer to Roman

Given an integer number. Your task is to convert this integer number into roman number.

### java code 
```

import java.util.*;
public class Main
{
	public static void main(String[] args) {
    Scanner sc=new Scanner(System.in);
    int n=sc.nextInt();
    Map<Integer,String> map = new HashMap<>();
        map.put(1,"I");
        map.put(4,"IV");
        map.put(5,"V");
        map.put(9,"IX");
        map.put(10,"X");
        map.put(40,"XL");
        map.put(50,"L");
        map.put(90,"XC");
        map.put(100,"C");
        map.put(400,"CD");
        map.put(500,"D");
        map.put(900,"CM");
        map.put(1000,"M");
        Stack<Integer> st = new Stack<>();
        st.push(1); st.push(4); st.push(5); st.push(9); st.push(10); st.push(40);
        st.push(50); st.push(90); st.push(100); st.push(400); st.push(500); st.push(900); st.push(1000);
        StringBuilder str = new StringBuilder();
        while(n>0){
            while(n>=st.peek()){
                n=n-st.peek();
                str.append(map.get(st.peek()));
            }
            st.pop();
        }
        System.out.print(str);
	}
}
