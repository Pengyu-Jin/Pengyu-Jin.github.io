## The World of Power Electronics
[电力电子相关技术学习](https://www.tdk.com/en/tech-mag/){:target=_blank}

notes

### part1
### part2
The differences between the linear and switching methods:



## classes of power amplifier

Class A 放大器
Class A放大器是一种模拟放大器，其中输出器件（如晶体管）在整个输入信号周期内都处于导通状态。这意味着，无论输入信号的大小如何，放大器的输出设备都会持续工作。Class A放大器的主要特点是它们提供非常好的线性响应，也就是说，它们能够非常精确地放大输入信号，几乎不引入任何形式的信号失真。但是，这种类型的放大器效率较低，通常在30%以下，因为输出设备即使在没有输入信号时也消耗功率。

Class B 放大器
相比之下，Class B放大器的输出设备仅在输入信号的一半周期内导通。具体来说，一个输出设备处理正半周期的信号，而另一个输出设备处理负半周期的信号。这种方式可以大大提高放大器的效率，理论上可以达到78.5%，因为在任何给定的时间内，只有一半的输出设备在消耗功率。然而，这种放大器的缺点是在零交叉点处可能会引入失真，这是因为从一个输出设备切换到另一个设备的过程中可能不够平滑，这种失真通常被称为交叉失真。

Summary
总的来说，Class A放大器因其出色的线性表现而被用于对音质要求极高的应用中，尽管其效率较低。而Class B放大器则因其更高的效率而被用于需要较高功率输出但可以容忍一定失真的应用中，如某些无线通信和音频放大器系统。两者各有优势和应用场景。

[classes of power amplifier](https://circuitdigest.com/tutorial/classes-of-power-amplifier-explained){:target=_blank}

## New Energy 并网

依据直流侧电源性质的不同，分为电压型逆变器和电流型逆变器。（从电路拓扑角度上来）。

但逆变器的对外特性，体现为什么，取决于控制。

- 对电压型逆变器采用电流型控制，则特性为电流源；采用电压型控制，则特性为电压源。

- 对电流型逆变器采用电流型控制，则特性为电流源；采用电压型控制，则特性为电压源。

电压型逆变器工业上最为常见99%，主要原因是目前的IGBT不能放在电流型逆变器上使用，具有逆阻能力的IGBT目前没有广泛生产，没有对应的市场生态。

SPWM中单极性谐波特性一般优于双极型调制，EMI(Electromagetic Interference电磁干扰)等特性较优

