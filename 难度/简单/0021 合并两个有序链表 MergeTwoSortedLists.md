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
#### 改进：
```C++
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode head(0);
        ListNode* p = &head;
        while(l1&&l2)
        {
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
        p->next = l1 ? l1 : l2;
        return head.next;
    }
};
```
#### 思路：
使用一个新构建的节点，但是返回时不使用它，这样就能避免循环开始对其取值  
需要注意的是这个节点必须真实存在，因此需要new一个返回head作为其地址，也可以像上面这样直接使用head作为节点本身
### 2.递归：
```C++
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        if(l1==NULL) return l2;
        if(l2==NULL) return l1;
        if(l1->val>l2->val) l2->next = mergeTwoLists(l2->next, l1);
        else                l1->next = mergeTwoLists(l1->next, l2);
        return l1->val>l2->val?l2:l1;
    }
};
```
#### 思路：
每次递归，将合并后链表的next指向两个链表中更小的节点，最后返回l1和l2中的较小者
#### 复杂度分析：
- 时间复杂度: O(M+N)
- 空间复杂度: O(M+N)
