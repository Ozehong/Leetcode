https://leetcode.cn/problems/best-time-to-buy-and-sell-stock/description/

//0(n^2)会内存爆了，有很多位置多次遍历过了，应该考虑动态规划


//动态规划：dp[i]表示第i天卖出的最大利润
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int n = prices.size();
        if (n == 0) return 0; // 边界条件
        int minprice = prices[0];
        vector<int> dp (n, 0);//dp[i]表示第i天卖出的最大利润

        for (int i = 1; i < n; i++){
            minprice = min(minprice, prices[i]);//记录前i天的最小值
            dp[i] = max(dp[i - 1], prices[i] - minprice);//第i天卖出的最大利润
        }
        return dp[n - 1];
    }
};

//优化空间复杂度：profit表示第i-1天卖出的最大利润
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int low=10001,profit=0;
        for(int i=0;i<prices.size();i++)
        {
            low=min(low,prices[i]);//记录前i天的最小值
            profit=max(profit,prices[i]-low);//第i天卖出的最大利润

        }
        return profit;
    }
};