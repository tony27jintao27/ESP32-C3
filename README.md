# ESP32-C3#include <Arduino.h>

int port = 9;

// 中断函数
void blink()
{
  Serial.println("IRQ");
  //delay(1);
}

void setup()
{
  // 初始化日志打印串口
  Serial.begin(115200);  
  // 配置中断引脚
  pinMode(port, INPUT|PULLUP );
  // 检测到引脚 26 下降沿，触发中断函数 blink
  attachInterrupt(port, blink, FALLING);
  Serial.println("\nstart irq test");
}

void loop()
{
  delay(100);
}
