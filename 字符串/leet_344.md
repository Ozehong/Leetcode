//https://leetcode-cn.com/problems/reverse-string/
//344. 反转字符串
//常规解法：双指针

```C
class Solution {
public:
    void reverseString(vector<char>& s) {
        char temp='0';
        int i=0;
        while(i<s.size()-i-1)
        {
            temp=s[i];//交换
            s[i]= s[s.size()-i-1];
            s[s.size()-i-1]=temp;
            i++;

        }
    }
};
```
