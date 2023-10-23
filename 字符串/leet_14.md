// https://leetcode.cn/problems/longest-common-prefix/

// 最长公共前缀
// 思路：先找到最短的字符串，然后遍历每个字符串的每个字符，如果有不同的字符，则返回前面的字符串
```C
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if(strs.size()==1)
            return strs[0];
        int num=strs[0].length();
        for(int i=1;i<strs.size();i++)
        {
            int j=0;
            for(;j<min(num,int(strs[i].length()));j++)
            {
                if(strs[0][j]!=strs[i][j])
                {
                    break;
                }
            }
            num=j;
            if(!num)
                return "";
        }
        return strs[0].substr(0,num);
    }
};
```


// 优化：纵向扫描时，从前往后遍历所有字符串的每一列，比较相同列上的字符是否相同，如果相同则继续对下一列进行比较，如果不相同则当前列不再属于公共前缀，当前列之前的部分为最长公共前缀。
// 子串函数substr的用法：substr(起始位置，子串长度)
```
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if(!strs.size()) {
            return "";
        }
        int n = strs[0].size();
        int m = strs.size();
        for(int i=0; i<n; i++) {
            char c = strs[0][i];
            for(int j=1; j<m; j++) {
                if(i == strs[j].size() || strs[j][i] != c) {
                    return strs[0].substr(0, i);
                }
            }
        }
        return strs[0];
    }
};
```
