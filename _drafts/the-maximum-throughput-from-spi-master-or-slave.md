#  (转)SPI最大传输速率 

转自：[https://www.silabs.com/community/mcu/8-bit/knowledge-base.entry.html/2017/01/13/spi_-asc0](https://www.silabs.com/community/mcu/8-bit/knowledge-base.entry.html/2017/01/13/spi_-asc0)

## 问题

SPI作为master或slave时可以达到的最大传输速率是多少 ？

## 答案

## SPI最大传输速率受以下几个条件影响：

    SPI的最大时钟频率
    CPU处理SPI数据的能力
    输出端驱动能力（PCB所允许的最大信号传输速率）

## SPI的最大时钟频率

一般情况下，SPI模块的最大时钟频率为系统时钟频率的1/2。虽然SPI的传输速率主要受限于CPU处理SPI数据的能力，但在同另一个非常高速率的SPI设备通讯时，SPI的最大时钟频率将有可能制约其传输速率。

## CPU处理SPI数据的能力

通常情况下，考虑到系统中CPU有可能需要处理其他任务，以及对所接收SPI数据的具体运算处理方法，CPU处理SPI数据的能力将影响到整体的传输速率。

例如，系统在收到SPI数据后只是作简单的累加。如果当前SPI模块的时钟频率是1/2系统时钟频率，接收每一个SPI byte将需要16个系统时钟周期。那么在下一笔SPI数据接收到之前CPU有足够的时间来处理当前数据，此时SPI的最大传输速率即为系统时钟的1/2。

接下来考虑另外一种情形，假设CPU有50%的时间用于处理其他任务，同时对所接收到的每byte SPI数据，需要100个系统时钟周期来作运算处理。每接收1 byte SPI数据，CPU需要100个时钟周期来作处理，同时需要100个时钟周期来处理其他任务，因此总共需要消耗200个系统时钟周期。用公式表达如下：

200 *Tsysclk = 8 * Tspiclk;

spiclk = sysclk/25;

因此，在这个例子中，我们可以看出SPI的最大传输速率由CPU处理SPI数据的能力所决定。

## 输出端驱动能力

最后要考虑的因素是输出节点的驱动力。PCB上的微量电容和器件引脚的输出阻抗相结合，将会形成一个低通滤波器，限制设备间信号的传输速度。通常该滤波器的截止频率可以近似为：

Fmax = 1 /（2 × π × Rdrive * Ctrace）；

其中Rdrive是所驱动的最大阻抗值，Ctrace表示输出节点所驱动的所有微量电容的总和。

在固定阻抗条件下，电路的微量电容将成为制约SPI传输速率的因素。系统中如果设备间的距离非常短（Ctrace较小值），那么CPU的处理能力或SPI的时钟频率将是主要限制因素。如果系统中总线上有多个SPI设备，同时设备间的连线很长（Ctrace较大值），那么输出驱动能力将制约SPI的传输速率。

Topics: 8-bit MCUs Knowledge Base Articles Interface 

英文版：[https://www.silabs.com/community/mcu/8-bit/knowledge-base.entry.html/2011/12/06/spi_throughput-Qr7y](https://www.silabs.com/community/mcu/8-bit/knowledge-base.entry.html/2011/12/06/spi_throughput-Qr7y)