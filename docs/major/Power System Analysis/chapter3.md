## 电力系统的标幺制
### 有名制和标幺制
==Q：为什么要采用标幺制？==

- 标幺制的定义
- 
<center>
![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/20230228185037.png){width="300"}
</center>

- 有名制的问题：采用有名值的计算结果可比性差，不同电压等级、不同容量、不同设备的有名值参数差异大
- 标幺制的优点：
    - 便于比较、分析元件特性与参数（变压器短路阻抗）
    - 直观掌握电力系统的运行状态（发电机的运行）
    - 对称三相电路的计算与单相计算一致，简化了计算

### 基准值的选取
==Q：如何选定标幺值的基准值？==

- 在电力系统中，我们习惯于用功率和电压作为变量。所以基准值都是先选定功率和电压，然后电流、阻抗、导纳等都可以由功率和电压进行计算
 
![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/20230228185541.png)

- 对三相电路

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/20230228190627.png)

==Q：基准值发生变化时标幺值怎么变？==

- 把标幺阻抗还原成有名值：$X_{(有名值)}=X_N*·\frac{U_N^2}{S_N}$
- 新基准值下的标幺值：$X_{B}*=X_{(有名值)}·\frac{S_B}{U_B^2}=X_N*·\frac{U_N^2}{S_N}·\frac{S_B}{U_B^2}$
- 电抗器的换算公式：
    - $X_{R(有名值)}=X_{R(N)}*·\frac{U_N}{\sqrt{3}I_N}$
    - $X_{R(B)}*=X_{R(有名值)}·\frac{S_B}{U_B^2}=X_{R(N)}*·\frac{U_N}{\sqrt{3}I_N}·\frac{S_B}{U_B^2}$

【注】：

- 设备按照各自额定电压、容量，计算标幺值，系统按照统一原则选，两者不一样
- 电抗器一般没有额定容量，而是考虑额定电流（作用：限流）

### 多电压等级网络中的标幺值计算

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/3P0U%25G~$34Q~$P6W4O4MN9.jpg)

- 方法一：归算有名值（正）
    - 指定基本级，将其它级有名值归算到基本级
    - 指定基本级下的基准值
    - 用标幺值定义求标幺值

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/W0%7DVR%60%5D%25CY0RP%60C%7D24~2I.jpg)

- 方法二：归算基准值（逆）
    - 在基本级下指定一套基准值
    - 将基准值归算到各电压级，形成相应基值
    - 各电压级参数除以本级下的基值

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/T%7D_43Z0%5DA7%5BM3PUK_RV1OO.jpg)

==Q：逐级归算法在应用中存在什么问题？==

<center>
![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/%60SV75I0KSR_T%5BQ%25%7BSLJYCRW.jpg){width="300"}
</center>

==Q：如何解决上述问题？==

- 考虑各选电压法

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/X7WO%25FB1%7D@%5B34NJ5BH4%5D3XJ.jpg)

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/2G1V%7BTE%7BU%5DTTCC7EP%60F$W8.jpg)

【注】扩充：潮流计算的计算机算法

- 在计算机求解潮流的时候，一般都取个电压等级对应的系统额定电压（标称额定电压），然后计算出来的结果都是标幺值。

==Q：各选电压法的优缺点？==

- 避免了逐级归算法在多电压等级环网，标幺值精确计算中面临的变比选择难题
- 采用各选电压法获得的标幺值等值电路可能包含标幺变比不等于1的变压器

==Q：逐级归算法在环网遇到困难以及各选电压法出现非标准变比的本质原因是什么？==

- 升、降压变压器在同一电压等级下的额定电压不等

因此引出了平均额定电压法

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/4RW3BYL94%7BU%7B%7BGE6$7L0UCI.jpg)

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/20230228203320.png)


- 其他电压等级
    - 3——3.15
    - 6——6.3
    - 35——37
    - 330——345
    - 750——787.5


![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/Z%7D33V%7B95%25A6OJ_DNR0Z4A.jpg)

- 电抗器不能直接认为两个电压可以约掉，就理解成一种习惯即可。其余情况都可以约去。
- 平均额定电压法多用于短路电流的计算，潮流计算很少用这种

## 标幺值计算实例

![](https://image-bed-1316693164.cos.ap-shanghai.myqcloud.com/9I%7D50M$X64WV%7BH69A%60NOW45.jpg)
