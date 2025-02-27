## 342. Max Sum of a Pair With Equal Sum of Digits

You are given a 0-indexed array nums consisting of positive integers. You can choose two indices i and j, such that i != j, and the sum of digits of the number nums[i] is equal to that of nums[j].

Return the maximum value of nums[i] + nums[j] that you can obtain over all possible indices i and j that satisfy the conditions.

 

Example 1:

Input: nums = [18,43,36,13,7]  
Output: 54  
Explanation: The pairs (i, j) that satisfy the conditions are:  
- (0, 2), both numbers have a sum of digits equal to 9, and their sum is 18 + 36 = 54.  
- (1, 4), both numbers have a sum of digits equal to 7, and their sum is 43 + 7 = 50.  
So the maximum sum that we can obtain is 54.

Example 2:

Input: nums = [10,12,19,14]  
Output: -1  
Explanation: There are no two numbers that satisfy the conditions, so we return -1.  
 

Constraints:  

1 <= nums.length <= 105  
1 <= nums[i] <= 109    


### APPROACH : 
SINCE WE ONLY NEED THE SUM OF DIGIT AND NUMBER, SO PUT IT IN THE HASHMAP. IF ANY SUM IF ENCOUNTERD OF EHICH NUMBER IF GREATER THAN STORED ONE THEN UPDATE THE NUMBER FOR THIS SUM.


### JAVA CODE 

```
class Solution {  
    public int maximumSum(int[] nums) {  
        ### // MAP STORE THE SUM OF THE DIGIT OF NUMBER AS KEY AND NUMBER AS VAL;   
        HashMap<Integer,Integer> map = new HashMap<>();   
        int max=-1;  
        for(int i=0; i<nums.length; i++){  
            int n=nums[i];  
            int sum=0;  
            while(n>0){  
                sum+= n%10;  
                n/=10;  
            }  
            if(map.containsKey(sum)){  
                int num=map.get(sum);  
                max=Math.max(max, num+nums[i]);  
                ##// IF NUMBER IF BIGGER THAN PREVIOUS ONE WHOSE DIGIT SUM IS SAME THEN UPDATE THE NUMBER  
                if(num < nums[i]){  
                    map.put(sum,nums[i]);  
                }  
            }else{  
                map.put(sum,nums[i]);  
            }  
        }  
        return max;  
    }  
}  
