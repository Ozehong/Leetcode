https://leetcode.cn/problems/valid-palindrome/submissions/475310229/

class Solution {
public:
    bool isPalindrome(string s) {
        int left=0,right=s.length()-1;
        while(left<right)
        {
            if(s[left]>='A' && s[left]<='Z' ||s[left]>='a' && s[left]<='z' || s[left]>='0' && s[left]<='9')
            {
                if(s[left]>='A' && s[left]<='Z' )
                    s[left]=s[left]-'A'+'a';
            }
            else
            {
                left++;
                continue;
            }

            if(s[right]>='A' && s[right]<='Z' ||s[right]>='a' && s[right]<='z'|| s[right]>='0' && s[right]<='9')
            {
                if(s[right]>='A' && s[right]<='Z' )
                    s[right]=s[right]-'A'+'a';
            }
            else
            {
                right--;
                continue;
            }
            if(s[right]==s[left])
            {
                right--;
                left++;
            }
            else return false;  
        }
        return true;

    }
};