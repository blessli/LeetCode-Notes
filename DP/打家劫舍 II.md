# ![打家劫舍 II](https://leetcode-cn.com/problems/house-robber-ii/)
> 所有的房屋都围成一圈,如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警

```cpp
class Solution {
public:
    int rob(vector<int>& nums) {
        if (nums.size()==1) return nums[0];
        return max(dfs(nums,0,nums.size()-2),dfs(nums,1,nums.size()-1));
    }
    int dfs(vector<int>& nums,int left,int right){
        int pre=0,curr=0;
        for(int i=left;i<=right;i++){
            int tmp=curr;
            curr=max(curr,pre+nums[i]);
            pre=tmp;
        }
        return curr;
    }
};
```