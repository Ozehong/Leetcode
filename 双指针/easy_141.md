https://leetcode.cn/problems/linked-list-cycle/description/

# 快慢指针

```C
/**

* Definition for singly-linked list.
* struct ListNode {
* int val;
* ListNode *next;
* ListNode(int x) : val(x), next(NULL) {}
* };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if(head ==nullptr || head->next==nullptr)//只有一个节点或者没有节点,用nullptr不用NULL是因为nullptr是c++11的新特性，用NULL会报错
            return false;
        ListNode *slow=head;
        ListNode *fast=head->next;
        while(slow!=fast)
        {
            if(fast==nullptr || fast->next==nullptr)
                return false;
            slow=slow->next;
            fast=fast->next->next;
        }
        return true;
  
    }
};
```