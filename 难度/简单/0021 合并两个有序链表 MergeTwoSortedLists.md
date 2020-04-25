# 题目地址：
https://leetcode-cn.com/problems/merge-two-sorted-lists/
## 代码：
### 1.迭代：
```C++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        if(l1==NULL) return l2;
        if(l2==NULL) return l1;
        ListNode* head;
        if(l1->val>l2->val) 
        {
            head=l2;
            l2=l2->next;
        }
        else 
        {
            head=l1;
            l1=l1->next;
        }
        ListNode* p = head;
        while(l1!=NULL||l2!=NULL)
        {
            if(l1==NULL)
            {
                p->next = l2;
                break;
            }
            if(l2==NULL)
            {
                p->next = l1;
                break;
            }
            if(l1->val>l2->val) 
            {
                p->next=l2;              
                l2=l2->next;
            }
            else 
            {
                p->next=l1;
                l1=l1->next;
            }
            p=p->next;
        }
        return head;
    }
};
```
#### 思路：
比较两个链表的下一个节点，取小的作为p->next，需要注意的是首先要取head并保留，用于返回  
另外需要考虑的是一个链表取完了的情况
#### 复杂度分析：
- 时间复杂度: O(M+N)
- 空间复杂度: O(1)
