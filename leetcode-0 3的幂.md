# leetcode-0 3的幂

题目链接：https://leetcode-cn.com/problems/power-of-three/

写一个函数来判断是否是3的幂，进阶说不使用循环或者递归，那直接打表或者就判断2的31次方内的最大的3的幂次方数字，然后能否整除它

```c
bool isPowerOfThree(int n){
    return n > 0 && 3486784401 % n ==0;
}
```

