# 全排列问题

## 无重复数字的全排列 
例子：生成1,2,3的全排列

    1 2 3
    1 3 2
    2 1 3
    2 3 1
    3 1 2
    3 2 1

### 递归方法
从1到n的全排列可以分为n类，分别以1,2,..n 开头的全排列,每一类有(n-1)!个。

代码如下： 

    class Solution {
      public :
        vector<vector<int> > permute(vector<int> &num)
        {
            vector<vector<int> > permutations;
            int sz = num.size() - 1;

            perm(num, 0, sz, permutations); 
        
            return permutations;
        }
    
       private :
        void perm(vector<int>& num, int m, int n, vector<vector<int> >& permutations)
        {
            if (m >= n) { 
                permutations.push_back(num);
            } else {
                for (int i = m; i <= n; ++i) {
                   swap(num[m], num[i]);
                   perm(num, m + 1, n, permutations);
                   swap(num[m], num[i]);
                }
            }
        }
    };

### 字典序法
本方法的核心就是根据当前序列找到当前序列在字典序种的下一个或者前一个序列. 
next permutation的核心思想（假设输入为a[1..n])： 

1. 从n开始到1，找到第一个满足条件的a[i] < a[i + 1]，如果找不到，返回fasle，并reverse(a[1..n]), 如果找到，goto 2
2. 从n..i+1中找到第一个大于a[i]的数，假设为j即a[j] > a[i], 并交换a[i]和a[j],然后reverse(a[i+1..n]),返回true.

代码如下:

    class Solution {  
      public: 
        vector<vector<int> > permute(vector<int> &num) { 
            vector<vector<int> > permutations;
            sort(num.begin(), num.end());
            permutations.push_back(num);
            while(next_permutation(num.begin(), num.end())) {
                permutations.push_back(num); 
            }
        
            return permutations;
        }   
    };

### 两种方法的比较
1. 第一种方法使用与无重复数字的全排列，因为不需要进行比较
2. 第二种方法可以解决有重复数字的全排列，但是会多一个排序以及很多比较的时间

## leetcode problems
1. <https://oj.leetcode.com/problems/permutations/>
2. <https://oj.leetcode.com/problems/next-permutation/>
3. <https://oj.leetcode.com/problems/permutations-ii/>
4. <https://oj.leetcode.com/problems/permutation-sequence/>
