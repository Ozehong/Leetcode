// https://leetcode.cn/problems/first-unique-character-in-a-string/description/

// 思路：用一个数组记录每个字符出现的次数，然后再遍历一遍字符串，找到第一个出现次数为1的字符
class Solution {
public:
    int firstUniqChar(string s) {
        vector<short> a(26,0);
        for(int i=0;i<s.length();i++)
        {
            if(a[s[i]-'a']<=2)
                a[s[i]-'a']++;        
        }
        for(int i=0;i<s.length();i++)
        {
            if(a[s[i]-'a']==1)
                return i;   
        }
        return -1;

    }
};

// 优化：用一个哈希表记录每个字符是否只出现一次，然后再遍历一遍字符串，找到第一个出现次数为1的字符
// 为什么用哈希表而不用数组？因为数组需要开辟26个空间，而哈希表只需要开辟出现过的字符个数的空间
class Solution {
public:
    int firstUniqChar(string s) {
        unordered_map<char, bool> dic;//记录每个字符是否只出现一次
        for(char c : s)
            dic[c] = dic.find(c) == dic.end();//如果c不在dic中，则dic[c]为true，否则为false
            //dic.find(c)是dic中查找c的迭代器，如果找不到，则返回dic.end()
        for(int i = 0; i < s.size(); i++)
            if(dic[s[i]]) return i;
        return -1;
    }
};