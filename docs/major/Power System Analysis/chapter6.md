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


## 闭式均一网络的潮流计算

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/%E6%BC%94%E8%8D%89-46.jpg)

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/EQG@LE6X63XOB%5BZE5VFRQ$J.jpg)

## 两端供电网络的潮流计算

![]()