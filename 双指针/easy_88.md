# 88.合并两个有序数组

描述：给你两个**非递减**有序整数数组 nums1 和 nums2，请你将 nums2 合并到 nums1 中，使 nums1 成为一个有序数组。

## 方法一：双指针

### 思路

我们可以使用双指针的方法，从后往前遍历，将两个数组中较大的数放到 nums1 的末尾。

```c++
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int i=m-1,j=n-1,k=m+n-1;
        while(k>=0 && i>=0 && j>=0){
            if(nums1[i]>=nums2[j] ){
                nums1[k--]=nums1[i--];
            }
            else nums1[k--]=nums2[j--];
        }
        while(k>=0){
            if(i>=0)
                nums1[k--] = nums1[i--];
            else nums1[k--] = nums2[j--];
        }
    }
};

```
