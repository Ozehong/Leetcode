
https://leetcode.cn/problems/multiply-strings/description/


// 字符串相乘
// 思路：模拟乘法，时间复杂度O(m*n)，空间复杂度O(m+n)
// 注意：f[i+j+1]+=x*y; f[i-1]+=f[i]/10; f[i]=f[i]%10;
class Solution {
public:
    string multiply(string num1, string num2) {
        if(num1=="0" || num2=="0")
            return "0";
        int m=num1.length(),n=num2.length();
        vector<int> f(m+n,0);
        for(int i=m-1;i>=0;i--)
        {
            int x=num1[i]-'0';
            for(int j=n-1;j>=0;j--)
            {
                int y=num2[j]-'0';
                f[i+j+1]+=x*y;
            }   
        }

        for(int i=m+n-1;i>=0;i--)//进位
        {
            if(f[i]/10!=0)
            {
                f[i-1]+=f[i]/10;
                f[i]=f[i]%10;
            }
        }
        string ans="";
        int i=0;
        while(f[i]==0)
            i++;
        while(i<m+n)
            ans.push_back('0'+f[i++]);//

        return ans;
    }
};