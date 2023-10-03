//https://leetcode.cn/problems/longest-palindromic-substring/description/
//最长回文子串


//暴力法：超时
//时间复杂度：O(n^3)
//空间复杂度：O(1)

class Solution {
public:
    bool Palcheck(string &s,int i,int j)
    {
        for(;i<j;i++,j--)
        {
            if(s[i]!=s[j])
                return false;
        }
        return true;
    }
    string longestPalindrome(string s) {
        vector<int> dp(s.length(),0);
        int maxi=0;
        for(int i=0;i<s.length();i++)
        {
            for(int j=i+1;j<s.length();j++)
            {
                if(s[j]!=s[i])
                    continue;
                if(Palcheck(s,i,j))
                    dp[i]=j-i;
            }
            if(dp[i]>dp[maxi])
                maxi=i;
        }
        return s.substr(maxi,dp[maxi]+1);
    }
};

//动态规划
//时间复杂度：O(n^2)
//空间复杂度：O(n^2)
//dp[i][j]表示s[i]到s[j]是否为回文串
//dp[i][j]=dp[i+1][j-1] && s[i]==s[j]
//边界条件：j-i==2 || j-i==1 || j==i
//注意：dp[i][j]的值依赖于dp[i+1][j-1]，所以i要从大到小遍历，j要从小到大遍历

class Solution {
public:
    string longestPalindrome(string s) {
        int n=s.length();
        int maxi=1,left=0;
        vector<vector<int>> dp(n,vector<int>(n,0));
        for(int i=n-1;i>=0;i--)
        {
            for(int j=i+1;j<n;j++)
            {
                if(s[i]!=s[j] || i>j)//注意：i>j
                    continue;
                if(j-i==2 || j-i==1 || j==i)//边界条件
                    dp[i][j]=1;
                else
                    dp[i][j]=dp[i+1][j-1];//状态转移方程

                if(dp[i][j]&&j-i+1>maxi)//更新最大值
                {
                    left=i;
                    maxi=j-i+1;
                }
            } 
        }
        return s.substr(left,maxi);//返回最长回文子串
    }
};

//中心扩展法
//时间复杂度：O(n^2)
//空间复杂度：O(1)
class Solution {
    // 将字符串s[left:right]向左、向右扩展，得到的回文串左端点和最长长度\
    // 返回值：pair<int,int>，first为左端点，second为最长长度
    // pair是一个结构体，用来存储两个数据，first和second
     pair<int,int> expand(string s,int left,int right){
         while(left>=0 && right<s.length() && s[left]==s[right]){
             left--;
             right++;
         }
         return pair<int,int>{left+1,right-left-1};
     }
public:
    string longestPalindrome(string s) {
        int n=s.size();
        int maxlen=0,left=0;// 最长回文子串的长度及对应的左端点
        for(int i=0;i<n;i++){
            // auto是自动类型推断，可以根据等号右边的值自动推断出左边变量的类型
            auto p1= expand(s,i,i); // 长度为1的字符串扩展
            auto p2=expand(s,i,i+1); // 长度为2的字符串扩展
            if(p1.second>maxlen){
                maxlen=p1.second;
                left=p1.first;
            }
            if(p2.second>maxlen){
                maxlen=p2.second;
                left=p2.first;
            }
        }
        return s.substr(left, maxlen);
    }
};
