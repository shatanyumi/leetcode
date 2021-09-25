# leetcode-3 无重复字符的最长子串

题目链接：https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/

解题思路：滑动窗口解决，判断当前的字符串内有哪些字符用一个hash表来存储，或者使用一个数组来存储

```c
int lengthOfLongestSubstring(char * s){
    
    int res = 0;
    int l = 0, r = 0;
    int len = strlen(s);
    // 利用ASCII码进行每个字符的映射
    int hash[200];

    for(int i=0;i<200;i++){
        hash[i] = 0;
    }

    while(l<=r){
        while(r<len&&hash[s[r]]==0){
            hash[s[r]] = 1;
            r++;
        }
        int tmp = r-l;
        if(tmp>res){
            res = tmp;
        }
        hash[s[l]] = 0;
        l++;
    }
    return res;
}
```

