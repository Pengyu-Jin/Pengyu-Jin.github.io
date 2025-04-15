This page is the notes for the book *Reinforcement Learning: An Introduction (Second Edition)* by Sutton and Barto. Some of the contents valuable are transcribed and some are just my own thoughts.🧐

---

### Heuristic search methods -- P66

Many different decision-making methods can be viewed as ways of approximately solving the Bellman optimality equation.

For example, heuristic search methods can be viewed as expanding the right-hand side of the equation below several times, up to some depth, forming a 'tree' of possibilities, and then using a heuristic evaluation function to approximate $v_*$ at the 'leaf' nodes.

$$
v_*(s) = \max_a \sum_{s',r}p(s',r|s,a)\left[ r + \gamma v_*(s') \right]
$$



### DP 与强化学习中的 DP -- P66
在强化学习（尤其是理论部分）中，DP这个概念被“借用”来表示用完整模型来**递推求解最优策略或值函数**的过程。

这和经典算法中的动态规划思想本质一致，只是应用背景不同。

| 普通算法中的 DP         | 强化学习中的 DP                           |
|--------------------------|--------------------------------------------|
| 经典问题：背包、最长公共子序列   | 最优策略、最优值函数                       |
| 通常是数组递推           | 通常是值函数迭代，如 $v(s)$$q(s,a)$|
| 状态转移是已知的公式     | 状态转移由环境模型给出 $P(s'\|s,a)$   |
| 中间结果存到 dp[] 表中   | 中间结果存到值函数 $v(s)$ 或 $q(s,a)$ 中|


强化学习中的值迭代用的公式如下：

$$
v_*(s) = \max_a \sum_{s',r}p(s',r|s,a)\left[ r + \gamma v_*(s') \right]
$$

这很像经典 DP 中的转移方程，例如：

```python
dp[i] = max(choice_1, choice_2, ...)
```
区别在于强化学习的状态是环境的状态，选择的是动作，转移是有概率性，还加了折扣因子$\gamma$



### Online Learning -- P67

The online nature of reinforcement learning makes it possible to approximate optimal policies in ways that put more effort into learning to make good decisions for frequently encountered states, at the expense of less effort for infrequently encountered states. This is one key property that distinguishes reinforcement learning from other approaches.

