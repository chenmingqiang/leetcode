# 回溯算法

一个问题的解如果可以看成一个n维向量。 那么这个问题一般可以转换成回溯算法来做。回溯算法可以求解可行解，也可以穷举所有解。如果求最优解，则可以转换成分之限界算法。如数独问题，八皇后问题，3色问题，集合问题都可以转换成回溯法来做。回溯法有自己特有的模版。

## 递归回溯
递归回溯的模版如下

    Input  : A implict or explicit description of set(X1, X2, ... Xn)
    Output : A solution vector v=(x1, x2, ..., xn), xi in Xi 

    1. v <- ()
    2. flag <- false
    3. advance(1)
    4. if flag then output v
    5. else Output "no solution"

    Procedure advance(k)
    1. for each x in Xk
    2.    xk <- x; append xk to v;
    3.    if v is a final solution, then set flag <- true and exit
    4.    else if v is partial then advance(k+1)
    5. end for

## 非递归回溯
非递归回溯的模版如下

    Input  : A implict or explicit description of set(X1, X2, ... Xn)
    Output : A solution vector v=(x1, x2, ..., xn), xi in Xi 

    1. v <- ()
    2. flag <- false, k <- 1
    3. while k >= 1
    4.     while Xk not exhausted 
    5.         xk <- next element in Xk; append xk to v
    6.         if v is a final solution then set flag <- true, exit from two while
    7.         else if v is a partial solution set k <- k + 1
    8.     end while            
    9.     reset Xk so that next element in Xk is the first
    10.    k <- k - 1
    11. end while
    12. if flag then output v;
    13. else output "no solution"

上述两个模版稍加改变即可求所有解,还可以加上一个剪枝函数来加速求解过程.

## leetcode problem
1. <https://oj.leetcode.com/problems/sudoku-solver/>
2. <https://oj.leetcode.com/problems/subsets/>
3. <https://oj.leetcode.com/problems/subsets-ii/>
4. <https://oj.leetcode.com/problems/n-queens/>
5. <https://oj.leetcode.com/problems/n-queens-ii/>
6. <https://oj.leetcode.com/problems/letter-combinations-of-a-phone-number/>
7. <https://oj.leetcode.com/problems/combinations/>
8. <https://oj.leetcode.com/problems/combination-sum/>
9. <https://oj.leetcode.com/problems/combination-sum-ii/>
