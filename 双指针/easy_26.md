https://leetcode.cn/problems/remove-duplicates-from-sorted-array/submissions/475293218/

class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int left=0,right=0;
        while(++right<nums.size())
        {
            if(nums[right]!=nums[left])
                nums[++left]=nums[right];
        }
        return left+1;

    }
};