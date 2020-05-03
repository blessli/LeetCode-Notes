# [合并K个排序链表](https://leetcode-cn.com/problems/merge-k-sorted-lists/)
```cpp
struct ListNode{
    int val;
    ListNode *next;
    ListNode(int x):val(x),next(NULL){}
};
struct cmp{
    bool operator () (const ListNode* a,const ListNode* b) const{
        return a->val > b->val;
    }
};
class Solution {
public:
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        priority_queue<ListNode*,vector<ListNode*>,cmp> que;
        for(auto c:lists) if(c!=NULL) que.push(c);
        ListNode* result=new ListNode(0);
        ListNode* ans=result;
        while(!que.empty()){
            result->next=que.top();
            que.pop();
            result=result->next;
            if(result->next!=NULL) que.push(result->next);
        }
        return ans->next;
    }
};
```
