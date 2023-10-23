https://leetcode.cn/problems/longest-substring-without-repeating-characters/description/


# 描述
给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。

```C
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        unordered_map<char, int> dic;# 哈希表，记录每个字符的索引
        int res = 0, tmp = 0, len = s.size(), i;
        for(int j = 0; j < len; j++) {
            if (dic.find(s[j]) == dic.end()) i = - 1;// 未找到，i = -1
            else i = dic.find(s[j])->second; // 获取索引 i# 找到，i = dic[s[j]]
            dic[s[j]] = j; // 更新哈希表
            tmp = tmp < j - i ? tmp + 1 : j - i; // dp[j - 1] -> dp[j]// tmp = min(tmp + 1, j - i)
            res = max(res, tmp); // max(dp[j - 1], dp[j])
        }
        return res;
    }
};
```

