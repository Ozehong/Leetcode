// https://leetcode.cn/problems/length-of-last-word/description/


// 思路：从后往前找到第一个空格，然后计算空格后面的单词长度
class Solution {
public:
    int lengthOfLastWord(string s) {
        int n=s.length();
        int left=n-2,right=n-1;
        int key=-1;//最后一个字符是否是空格
        if(s[right]!=' ')//最后一个字符不是空格
        {
            key=0;
        }
            
        while(left>=0)//从后往前找到第一个空格
        {
            if(s[left]!=' ')
                left--;
            else{
                if(!key && left==n-2)
                    return 1;//最后一个字符不是空格，且只有一个单词
                if(right-left==1 )//连续两个空格
                {
                    left--;
                    right--;
                }
                else//找到了最后一个单词
                {
                    return right-left+key;
                }
            }
        }
        return right-left+key;

    }
};

// 优化：从后往前找到第一个非空格字符，然后计算空格后面的单词长度
class Solution {
public:
    int lengthOfLastWord(string s) {
        int tmp = s.length() - 1;
        while(tmp >= 0 && s[tmp] == ' ') tmp--;//找到第一个非空格字符
        int n = 0;//计算单词长度
        while(tmp >= 0 && s[tmp] != ' ') {//计算单词长度
            tmp--; n++;
        }
        return n;
    }
};