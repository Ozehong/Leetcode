// https://leetcode.cn/problems/add-strings/solutions/
// 字符串相加

//常规解法：双指针
class Solution {
public:
    string addStrings(string num1, string num2) {
        int n1=num1.length()-1,n2=num2.length()-1;
        int temp=0;
        while(n1>=0 && n2>=0)//两个指针都不到头
        {

            if(n1>=n2)//num1长
            {
                temp=(num1[n1]-'0')+(num2[n2]-'0')+temp/10;//temp/10是进位
                num1[n1]='0'+temp%10;//temp%10是当前位
            }
            else
            {
                temp=(num1[n1]-'0')+(num2[n2]-'0')+temp/10;
                num2[n2]='0'+temp%10;
            }
            n1--;
            n2--;

        }
        if(n1==n2)//两个指针都到头
        {
            if(temp>=10)
                return '1'+num1;
            else
                return num1;
        }
        if(n1>=0)//num1长
        {
            while(n1>=0)//进位
            {
                temp=(num1[n1]-'0')+temp/10;
                num1[n1]='0'+temp%10;
                n1--;
            }
            if(temp>=10)
                return '1'+num1;
            else
                return num1;
        }
        else
        {
            while(n2>=0)
            {
                temp=(num2[n2]-'0')+temp/10;
                num2[n2]='0'+temp%10;
                n2--;
            }
            if(temp>=10)
                return '1'+num2;
            else
                return num2;
        }
    }
};

//天才代码简化解法

class Solution {
public:
    string addStrings(string num1, string num2) {
        int n1=num1.length()-1,n2=num2.length()-1;
        int temp=0;
        string s="";//string可以直接相加,而且可以建立空的string，不用初始化
        while(n1>=0 || n2>=0 || temp/10!=0)
        {
            int x= n1>=0?num1[n1]-'0':0;//三目运算符，直接省去了if else的步骤，天才的简化！
            int y= n2>=0?num2[n2]-'0':0;
            temp=x+y+temp/10;
            s.push_back('0'+temp%10);//string库函数，末尾添加字符

            n1--;
            n2--;
        }
        reverse(s.begin(),s.end());//string库函数，反转
        return s;
    }
};