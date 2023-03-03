## 闭式电力系统的潮流计算
### 闭式电力系统潮流计算的难点

==Q：闭式网络分为哪两种？==

- 两端供电网络（一般的闭式网络）
- 环形网络（两端供电网络的特殊情况）

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/LI00UH2CGM%7B06HKQFK6%7BAMK.jpg)

==Q：闭式系统潮流计算的难度及解决思路是什么？==

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/87F2NWQZU_EWRFK%60LI~%7D5K.jpg)

### 闭式电力系统潮流计算的步骤
==Q：闭式电力系统潮流计算的基本步骤？==

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/C%7DOFND8YP%5DPGPC%5BKJEWH3.jpg)

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/~%60%7DZ29%5BS%5DCYWIRQO%7B3R%7BZP.jpg)

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/_3VLUH7DZA%5D%7BK12@HVTJA1Y.jpg)

- 上述公式是在全网都是额定电压（且相位相同）的前提下，用功率代替电流进行计算。
- 假设的前提实际上**忽略了电压和功率损耗**，实质：电流分布情况。
- 第一部分称为**基本功率分布**（也有称为自然功率分布，注意区分之前拓展的自然功率），该部分由负荷功率和网络参数决定。
- 第二部分是**循环功率**，仅由电源点电压差和网络参数决定。

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/I%5B6QB%5BF0QZVI_%25%7D%607XH%5D8.jpg)

【注】：若有功功率和无功功率的分点不在一处，为了计算的方便等，常在无功功率分点处分解。这是因为高压网络中电压损耗主要由无功功率的流动引起，无功功率分点处往往是闭式网络的电压最低点，在电压最低点处解开网络对电压计算有利。

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/%7B7L%60%5BM7T$1YVFYV7()%7BEWE2.jpg)

- 拆开后变成两个已知首端电压和末端功率的开式网络。


## 潮流计算例题4：闭式均一网络的潮流计算

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/%E6%BC%94%E8%8D%89-46.jpg)

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/EQG@LE6X63XOB%5BZE5VFRQ$J.jpg)

## 潮流计算例题5：两端供电网络的潮流计算

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/%E6%BC%94%E8%8D%89-48.jpg)

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/3%7BS$B783%5DT9%5DIM92E7TUMBU.jpg)


## 含变压器的简单环网的潮流分析
### 变压器变比不同时的功率分布

==Q：如何确定变比不同变压器并联运行时的功率分布情况？==

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/2X%5BX1E%5B~WQ37~3C%60AUXD9.jpg)

【注】：

- 环路电势：$\Delta \dot E'=\dot U_{A1}-\dot U_{A2}$
- 变压器的功率分布由两部分组成，一是变比相等、供给负荷时的基本功率分布；二是仅由变比不等而产生的、不进入负荷的循环功率
- 循环功率（无功功率性质，因为由压差产生）是环路电势在环路中产生的循环电流而引起的功率。环路电势的方向就是循环功率的方向。

### 环路电势的大小和方向
==Q：如何确定环路电势的大小和方向？==

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/JJG2E84B@M@61%7DR%605ZT5.jpg)

【注】：

- 如果高压侧电压或低压侧电压没有给出，也可以选用相应侧的电压等级的额定电压（标称值）进行计算，此时：
- $S_c\approx \frac{(k_{\Sigma}-1)V_{NH}^2}{Z_{T1}'\ast+Z_{T2}'\ast}=\frac{(k_{\Sigma}-1)V_{NL}^2}{Z_{T1}'\ast+Z_{T2}'\ast}$

==Q：对于更复杂的电网该如何确定环路电势的大小和方向？==

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/A%5B8F8J9_RP5F%7DZ@6@%5D@T00.jpg)

【注】：

- 这个实用的方法要牢记
- 变压器的变比要选为高压/低压
- $k_a=121/10.5,k_b=242/10.5,k_{c1}=220/121$
- 从b点出发，$k_{\Sigma}=\frac{k_b}{k_a×k_{c1}}=1.1$

## 潮流计算例题6：多电压等级环网的潮流计算

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/RS9G5TH7%5DUM@%60G4QE1L%7DKPS.jpg)


## 复杂电力网络的等值简化方法
### 等效电源法

### 负荷置移法

### 星三角（网）变换

