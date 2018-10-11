# Arduino

# DHT11 传感器
## DHT11数字传感器概述
DHT11 数字温湿度 传感器是一款含有已校准数字信 号输出的温湿度复合传感器 。 它应用专用的数字模块采集技术和温湿度传感技术 ，确保产品具有极 高的可靠性与卓越的长期稳定性。传感器包括一个电 阻 式 感 湿元件和一 个 NTC 测温元件，并与一个 高性能 8 位单片机相 连接。因此该产品具有品质卓越、超快响应、抗干扰能力强、性价比极高等优点。每个 DHT11 传感器都在极为精确的湿度校验室中进行校准。校准系数以程序的形式储存在 OTP 内存中，传感器内部在检测信号的处理过程中要调用这些校准系数。 单 线制串行接口，使系统 集成变得简易快捷。超小的体积、极低的功耗， 信号传输距离可达 20 米以上， 使其成为各类应用甚至最为苛刻的应用场合的最佳选则。产品 为 4 针单排引脚封装。 连接方便， 特殊封装形式可根据用户需求而提供。DHT11温湿度传感器常应用于暖通空调、汽车 、 消费品 、 湿度调节器 、 除湿器、医疗、自动控制等领域。

---
下面是运用DHT 11的代码
~~~#include <dht11.h>
#define DHT11PIN 8
dht11 DHT11;

void setup() {
  pinMode(DHT11PIN,OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int chk = DHT11.read(DHT11PIN);
  Serial.print("Tep: ");
  Serial.print((float)DHT11.temperature, 2);
  Serial.println("C");
  Serial.print("Hum: ");
  Serial.print((float)DHT11.humidity, 2);
  Serial.println("%");
  Serial.println();
  delay(1000);
}
~~~

---
## DHT11接口说明
建议连接线长度短于20米时用5K上拉电阻，大于20米时根据实际情况使用合适的上电阻：
![image.png](http://note.youdao.com/yws/res/210/WEBRESOURCEcb80f5d2876bc5ae4cf20e0b60b3aaf3)

## 串口通讯
DATA 用于微处理器与 DHT11之间的通讯和同步,采用单总线数据格式,一次通讯时间4ms左右,数据分小数部分和整数部分,具体格式在下面说明,当前小数部分用于以后扩展,现读出为零.操作流程如下:   一次完整的数据传输为40bit,高位先出。 
- 数据格式:
        8bit湿度整数数据+8bit湿度小数数据 
        +8bi温度整数数据+8bit温度小数数据 +8bit校验和 
        数据传送正确时校验和数据等于“8bit湿度整数数据+8bit湿度小数数据+8bi温度整数数据+8bit温度小数数据”所得结果的末8位。
## 接线图
![image.png](http://note.youdao.com/yws/res/225/WEBRESOURCEaa923e0529fca1137e5fdd02757a8b0c)
![image.png](http://note.youdao.com/yws/res/228/WEBRESOURCE2ff3ef3c6f7e901925bf2fdc6d086fe2)
