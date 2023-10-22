https://leetcode.cn/problems/container-with-most-water/description/


# 方法1：暴力，复杂度n^2(略)

# 方法2：双指针，复杂度n
# 右指针大于左指针时，左指针右移
# 右指针小于左指针时，右指针左移

class Solution {
public:
    int maxArea(vector<int>& height) {
        int left=0,right=height.size()-1;
        int maxi=0;
        while(left<right)
        {
            int temp=(right-left)*min(height[left],height[right]);
            maxi=max(maxi,temp);
            if(height[left]<=height[right])
                ++left;
            else --right;
        }
        return maxi;

    }
};