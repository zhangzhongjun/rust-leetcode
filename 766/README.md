# leetcode-766
## 思路

如果数组是一行或者一列，直接返回true

如果是二维数组，则按照下面的思路：

* 对于第一列的每个元素：从某一个元素出发，将其行坐标 列坐标都加1即可获得对角线上下一个元素
* 对于第一行的每个元素：从某一个元素出发，将其行坐标 列坐标都加1即可获得对角线上下一个元素

## Rust解答

```rust
impl Solution {
    pub fn is_toeplitz_matrix(matrix: Vec<Vec<i32>>) -> bool {
        let n = matrix.len();
        let m = matrix[0].len();
        
        if(n<=1 || m<=1){
            return true
        }
        for i in 0..n{
            let t = matrix[i][0];
            let mut x = i;
            let mut y = 0;
            while x<n && y<m{
                if matrix[x][y] != t{
                    return false
                }
                x = x + 1;
                y = y + 1;
            }
        }
        
        for i in 0..m{
            let t = matrix[0][i];
            let mut x = 0;
            let mut y = i;
            while x<n && y<m{
                if matrix[x][y] != t{
                    return false
                }
                x = x + 1;
                y = y + 1;
            }
        }
        true
    }
}
```

PS: 时间和内存上均击败了100%的用户，个人推测原因是没有人用Rust刷Leetcode

## Java解答

```java
class Solution {
    public boolean isToeplitzMatrix(int[][] matrix) {
        int n = matrix.length;
        int m = matrix[0].length;
        if(n<=1 || m<=1){
            return true;
        }
        
        for(int i=0;i<n;i++){
            int t = matrix[i][0];
            int x = i;
            int y = 0;
            while(x<n && y<m){
                if(matrix[x][y]!=t){
                    return false;
                }
                x++;
                y++;
            }
        }
        
        for(int i=0;i<m;i++){
            int t = matrix[0][i];
            int x = 0;
            int y = i;
            while(x<n && y<m){
                if(matrix[x][y]!=t){
                    return false;
                }
                x++;
                y++;
            }
        }
        
        return true;
    }
}
```



