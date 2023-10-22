https://leetcode.cn/problems/3sum/description/

# 方法1：暴力，复杂度n^3(略)

# 方法2：双指针，复杂度n^2
# 先排序，然后固定一个数，双指针扫描剩下的数
# 当两个指针指向的数相加和大于目标值时，右指针左移
# 当两个指针指向的数相加和小于目标值时，左指针右移


class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> ans;
        sort(nums.begin(),nums.end());
        for(int i=0;i<nums.size();i++)
        {
            if(i && nums[i]==nums[i-1])
                continue;

            int left=i+1,right=nums.size()-1;
            for(;left<right;left++)
            {
                if(left>i+1&&nums[left]==nums[left-1])
                    continue;
                while(right>left && nums[left]+nums[right]+nums[i]>0)
                    right--;
                if(right==left)
                    break;
                if(nums[left]+nums[right]+nums[i]==0)
                    ans.push_back({nums[i],nums[left],nums[right]});
            }
        }
        return ans;

    }
};