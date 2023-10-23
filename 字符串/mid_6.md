https://leetcode.cn/problems/zigzag-conversion/description/


// N字形变换
```C
class Solution {
public:
    string convert(string s, int numRows) {
        
        if(numRows==1)//特殊情况
            return s;
        string str="";
        for(int k=0;k<numRows;k++)//k表示行数，思路：按行遍历
        {   int i=0;

            while(i<s.length())
            {
                if((i+k)<s.length() )//注意：(i+k)<s.length()
                    str+=s[i+k]; 
                i+=2*numRows-2;//注意：i+=2*numRows-2
                if(k!=numRows-1 && k && i-k<s.length())//注意：k!=numRows-1 && k
                    str+=s[i-k];
            }        
        }
        return str;
    }
};
```