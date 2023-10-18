https://leetcode.cn/problems/move-zeroes/description/

class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int left=nums[0]?1:0;
        for(int i=1;i<nums.size();i++)
        {
            while(i<nums.size()&&!nums[i])
                i++;
            if(i==nums.size())
                break;
            swap(nums[left++],nums[i]);
        }

    }
};