#四旋翼无人机 - 2023	by 离人
##1.硬件
+主控：		STM32F407VET6开发板
+陀螺仪：	MPU6500
+气压计：	BMP280
+电调：		无刷电调 控制PWM协议
+电机：		无刷电机
+接收机：	RF209S SBUS协议接收机
+遥控器：	天地飞ET07 SBUS接收机皆可
<br/>
##2.外设说明
+电调：
	电调使用PWM控制的电调 PWM频率为500HZ

	电机1->右上 PA15
	电机2->左上 PA2
	电机3->左下 PA1
	电机4->右下 PA3
+
+陀螺仪：
	陀螺仪使用MPU6500陀螺仪 三轴加速度计 三轴陀螺仪 无磁力计
	VCC			5V/3.3V
	GND			GND
	SCL			PA5 -> SPI1_SCK
	SDA			PA7 -> SPI1_MOSI
	AD0			PA6 -> SPI1_MISO
	NCS			PA4
+
+气压计：
	气压计使用BMP280
	VCC			5V/3.3V
	GND			GND
	SCL			PB10 -> I2C2_SCL
	SDA			PB11 ->	I2C2_SDA
	----------------------------------
	SDO			GND -> 寄存器地址 0xEC
				VCC -> 寄存器地址 0x76
+
+接收机：
	接收机使用SBUS协议 
	SBUS 总线使用了TTL电平的反向电平，即标准TTL中的1取反为0，0取反为1；
  串口波特率100000 bit/s，8位数据位，2个停止位，偶校验，无控流，25个字节
+
<br/>
##3.程序设计
+程序使用HAL库编写
+使用操作系统freeRTOS
<br/><br/>