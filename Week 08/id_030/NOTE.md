# 高级动态规划
<h2>1.递归</h2>
函数自己调用自己，时间复杂度和空间复杂度没有任何加工或者处理
<h2>2.分治</h2>
提升维度降低时间复杂度，提升递归效率，需要处理结果集
<h2>3.动态规划</h2>
在分治的过程中，筛选最优解，提前排除不合适的答案，进一步提升效率
# 字符串相关处理
<h2>字符串在高级语言中是被定义之后就不可改变</h2>
    //Java 版本
   
    public int myAtoi(String str) {
        int index = 0, sign = 1, total = 0;
    
        //1. Empty string
        if(str.length() == 0) return 0;

        //2. Remove Spaces
        while(str.charAt(index) == ' ' && index < str.length())
           index ++;

        //3. Handle signs
           if(str.charAt(index) == '+' || str.charAt(index) == '-'){
              sign = str.charAt(index) == '+' ? 1 : -1;
            index ++;
           }
    
         //4. Convert number and avoid overflow
         while(index < str.length()){
              int digit = str.charAt(index) - '0';
              if(digit < 0 || digit > 9) break;

             //check if total will be overflow after 10 times and add digit
             if(Integer.MAX_VALUE/10 < total ||            
             	Integer.MAX_VALUE/10 == total && Integer.MAX_VALUE %10 < digit)
                 return sign == 1 ? Integer.MAX_VALUE : Integer.MIN_VALUE;

             total = 10 * total + digit;
             index ++;
             }
             return total * sign;
    }
