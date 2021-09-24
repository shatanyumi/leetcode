# leetcode-2 两数相加

题目链接：https://leetcode-cn.com/problems/add-two-numbers/

解题思路：模拟数字相加的过程，链表处理头尾，然后注意进位

```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */


struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2){
    struct ListNode* res = malloc(sizeof(struct ListNode));
    struct ListNode* ret = malloc(sizeof(struct ListNode));
    ret->next = res;
    res->next = NULL;

    int inc = 0;

    while(l1 || l2){
        struct ListNode* tmpnode = malloc(sizeof(struct ListNode));
        int a = 0;
        int b = 0;
        int tmpnum = 0;
        
        if(l1){
            a = l1->val;
            l1 = l1->next;
        }
        if(l2){
            b = l2->val;
            l2 = l2->next;
        }
        tmpnum = a + b +inc;
        inc = 0;
        if(tmpnum>=10){
            inc = tmpnum / 10;
            tmpnum = tmpnum % 10;
        }
        tmpnode->val = tmpnum;
        tmpnode->next = NULL;
        res->next = tmpnode;
        res = res->next;
    }
    if (inc){
        struct ListNode* tmpnode = malloc(sizeof(struct ListNode));
        tmpnode->val = inc;
        tmpnode->next = NULL;
        res->next = tmpnode;
        res = res->next;
    }

    return ret->next->next;
}
```

