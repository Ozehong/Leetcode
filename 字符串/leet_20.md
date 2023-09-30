// https://leetcode.cn/problems/valid-parentheses/description/

// 20. 有效的括
// 栈,时间复杂度低，空间复杂度低
// 栈常用函数，pop、push、top、empty
class Solution {
public:

    bool isValid(string s) {
        stack<char> str;
        if(s.length()%2)
            return false;
        for(int i=0;i<s.length();i++)
        {
            if(s[i]=='(' || s[i]=='{' || s[i]=='[')
            {
                str.push(s[i]);//左括号入栈
            }
            else
            {   if(!str.empty())
                {
                   if(s[i]==')'&& str.top()=='(' ||s[i]==']'&& str.top()=='[' || s[i]=='}'&& str.top()=='{')//匹配
                    str.pop();//出栈
                    else
                        return false; 
                }
                else return false;
              
            }      
        }
        if(!str.empty())
            return false;
        else return true;

    }
};

