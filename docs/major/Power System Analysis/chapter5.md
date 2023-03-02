## 潮流的基本概念及运算负荷
### 潮流计算的基本概念
==Q：什么是潮流？为什么称之为潮流？==

- 潮流是指电力系统中**各节点的电压**和**各支路的功率**的**稳态分布**。
- 电力系统中的电力网络覆盖广袤的地理区域，承担巨大的功率传输分配任务。电力网络中功率的汇集、输送、分配，恰似在电网中流动的潮流。
- 与海洋潮流类似，电力系统中的功率传输于电压间有密切的关系。

==Q：什么是潮流计算？潮流计算有什么用？==

- 潮流计算是指在已知的电力网络中，给定发电机、负荷功率和部分节点电压（系统运行条件），求解全部节点电压相量和支路功率的计算（系统运行状态）。其**本质**是分析电力网络中的电压于功率间的相互影响。
- 掌握运行状态，为电力系统的运行和规划提供依据。
- 评价电网的安全性（功率是否越限）、经济性（损耗计算）、质量（电压是否合格）。
- 为短路计算和稳定性计算提高系统的初始稳定运算条件，是电力系统中最最基本的计算。

### 运算负荷
==Q：如何应用运算负荷概念来等值系统？==

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/@YAXZ%25%7BR51K1045I_BRCH0.jpg)

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/96N1VRM@ZJGRF%60SEUZ%25HX.jpg)

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/%5D9UMX_3@7GV8Z%7BXBXSC_TR.jpg)

- 如果某个节点连接一个发电机，且该发电机的功率已经给定的话，可以把发电机当作一个负的负荷。

## 变压器损耗的计算例题
### 预备知识：标幺值与实验数据对应关系

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/Y%5B15%7DNBJ%60T@U%7BVKWD2%60~%5D4.jpg)

### 变压器损耗的计算例题

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/HX7%25PLEK%5BKVH_ZI@%25KWSWS.jpg)

## 辐射形电网的潮流计算
### 已知同一点的电压和功率
==Q：已知同一点的电压和功率如何计算潮流？==

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/%7B%6052XGYKE1N5%7D7%5DXFXRNM%7BX.jpg)

### 已知不同点的电压和功率
==Q：已知电源点电压和负荷节点功率该如何计算？==

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/8YC37XRGAI%7B0AL%25MN.jpg)

==Q：对于多个负荷节点的复杂辐射状网络该如何计算？==

1. 从叶节点开始向着根节点计算功率损耗，当某非叶节点作为开始节点的所有支路都计算完毕后，该节点成为新的叶节点。
2. 按顺序依次计算步骤1
3. 利用支路首段功率和给定电压，从电源点即根节点开始逐条支路计算电压，最终求得各支路终节点电压。

<center>
![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/T%7BW@_ZRL2Z25CY%601HY3J.jpg){width="300"}
</center>

- 顺序：dc-cb-fe-ge-eb-hb-bA

### 辐射型电网的潮流计算步骤
==Q：计算辐射型电网潮流的规范步骤？==（要严格遵循！）

1. 计算网络中各元件的参数
2. 由已知系统接线图作出系统的等值网络图
3. 求各节点的运算功率或运算负荷
4. 根据已知条件的具体情况，在简化的等值电路上，选用前述“两类过程”之一，计算网络的功率和电压分布

==Q：多电压等级的系统应该如何处理？==

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/20230301174355.png)

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/20230301174441.png)

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/20230301174502.png)

## 潮流计算例题1：已知末端电压和功率
![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/L%7BGYCAI553~2SWE%5BPNKGR%7B9.jpg)

## 潮流计算例题2：已知首端电压和末端功率
![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/TR1ZAB0K%253Q$ZYRSUBZTW8.jpg)

学习标准解答过程：
![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/7RSZGZ6LIRML4NXUMLU5V7W.jpg)

## 潮流计算例题3：多电压等级的潮流计算

方法一：将变压器前面元件的参数折算到高压侧

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/%60%60%60CU%5DAM%60%25A%5DW07IFI@FU.jpg)

方法二：保留理想变压器

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/LIZYZ~9R%5D9F8%256ZZ5T8QRX.jpg)