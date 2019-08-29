# leetcode-746
## 思路

动态规划，dp[i]表示登上第i层楼梯最小花费，其中0<= i <= n，所以dp的长度应该为n+1

因为可以从第0层和第1层出发，所以dp[0]=dp[1]=0

状态转移方程：dp[i] = min(dp[i-2]+cost[i-2], dp[i-1]+cost[i-1])

最终返回：dp[n]

## Rust解答

```rust
impl Solution {
    pub fn min_cost_climbing_stairs(cost: Vec<i32>) -> i32 {
        let mut dp = vec![0, 0];
        let n = cost.len();
        for i in 2..n+1{
            dp.push(std::cmp::min(dp[i-2]+cost[i-2], dp[i-1]+cost[i-1]))
        }
        dp[n]
    }
}
```



## Java解答

```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        int n = cost.length;
        int[] dp = new int[n+1];
        dp[0] = 0;
        dp[1] = 0;
        for(int i=2;i<dp.length;i++){
            dp[i] = dp[i-2]+cost[i-2] < dp[i-1]+cost[i-1] ? dp[i-2]+cost[i-2]:dp[i-1]+cost[i-1]; 
        }
        return dp[n];
    }
}
```



