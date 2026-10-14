# STM32F030F4P6最小系统板

## 一、概述

基于 STM32F030F4P6 的最小系统板。主控为 ARM Cortex-M0 内核，主频 48 MHz，集成 16 KB Flash 与 4 KB SRAM，TSSOP-20 封装，工作电压 2.4~3.6 V。

**板载资源**

- 供电：USB Type-C 输入 5 V，经 ME6211C33 LDO 稳压至 3.3 V
- 时钟：12 MHz 外部晶振（HSE）
- 调试：SWD 下载接口（SWDIO / SWCLK）
- 复位按键与 BOOT0 选择、2 路 LED 指示
- 扩展：全部 GPIO 经 2×10P 2.54 mm 排针引出

**工程结构**

- `hardware/`：嘉立创 EDA 专业版工程（原理图 + PCB，`.eprj3` 文件夹格式）
- `software/`：Keil 器件支持包（DFP）与 STM32F0 标准外设库

## 二、引脚定义

| 引脚号 | 引脚名称         | 类型 | I/O structure | 主功能 | Alternate functions                                                    | Additional function |
|:------ |:---------------- |:---- |:------------- |:------ |:---------------------------------------------------------------------- |:------------------- |
| 1      | BOOT0            |      |               |        |                                                                        |                     |
| 2      | PF0-OSC_IN(PF0)  | I/O  |               | XIN    | I2C1_SDA                                                               |                     |
| 3      | PF1-OSC_OUT(PF1) | I/O  |               | XOUT   | I2C1_SCL                                                               |                     |
| 4      | NRST             | I/O  |               |        | Device reset input / internal reset output(active low)                 |                     |
| 5      | VDDA             | S    |               |        | Analog power supply                                                    |                     |
| 6      | PA0              | I/O  | TTa           |        | USART1_CTS, USART2_CTS, <br>USART4_TX                                  |                     |
| 7      | PA1              | I/O  | TTa           |        | USART1_RTS, USART2_RTS, <br>EVENTOUT, USART4_RX                        |                     |
| 8      | PA2              | I/O  | TTa           |        | USART1_TX, USART2_TX, <br>TIM15_CH1                                    | ADC_IN2, WKPU4      |
| 9      | PA3              | I/O  | TTa           |        | USART1_RX, USART2_RX, <br>TIM15_CH2                                    | ADC_IN3             |
| 10     | PA4              | I/O  | TTa           |        | SPI1_NSS, USART1_CK,<br>USART2_CK, <br>TIM14_CH1, USART6_TX            | ADC_IN4             |
| 11     | PA5              | I/O  | TTa           |        | SPI1_SCK, USART6_RX                                                    | ADC_IN5             |
| 12     | PA6              | I/O  | TTa           |        | SPI1_MISO, TIM3_CH1, <br>TIM1_BKIN, TIM16_CH1, <br>EVENTOUT USART3_CTS | ADC_IN6             |
| 13     | PA7              | I/O  | TTa           |        | SPI1_MOSI, TIM3_CH2, <br>TIM14_CH1, TIM1_CH1N, <br>TIM17_CH1, EVENTOUT | ADC_IN7             |
| 14     | PB1              | I/O  | TTa           |        | TIM3_CH4,  TIM14_CH1,<br>TIM1_CH3N, USART3_RTS                         | ADC_IN9             |
| 15     | VSS              | S    |               |        | Ground                                                                 |                     |
| 16     | VDD              | S    |               |        | Complementary power supply                                             |                     |
| 17     | PA9              | I/O  | FT            |        | USART1_TX,TIM1_CH2,<br>TIM15_BKIN,I2C1_SCL                             |                     |
| 18     | PA10             | I/O  | FT            |        | USART1_RX,TIM1_CH3,<br>TIM17_BKIN,I2C1_SDA                             |                     |
| 19     | PA13(SWDIO)      | I/O  |               |        |                                                                        |                     |
| 20     | PA14(SWCLK)      | I/O  |               |        |                                                                        |                     |

## BOM表
| No. | Quantity | Comment | Designator | Footprint | Value | Manufacturer Part | Manufacturer | Supplier Part | Supplier |
|---:|---:|---|---|---|---|---|---|---|---|
| 1 | 5 | 100nF | C1,C4,C6,C20,C21 | C0603 | 100nF | CGA0603X7R104K500JT | HRE(芯声) | C6119867 | LCSC |
| 2 | 2 | 18pF | C17,C18 | C0603 | 18pF | CC0603FRNPO9BN180 | YAGEO(国巨) | C527046 | LCSC |
| 3 | 3 | 10uF | C19,C24,C25 | C0603 | 10uF | CL10A106KP8NNNC | SAMSUNG(三星) | C19702 | LCSC |
| 4 | 1 | PH2.54-01-04PZD | H1 | HDR-TH_4P-P2.54-V-M-1 |  | PH2.54-01-04PZD | XUNPU(讯普) | C7501582 | LCSC |
| 5 | 2 | PZ254V-11-10P | H2,H4 | HDR-TH_10P-P2.54-V-M |  | PZ254V-11-10P | XFCN(兴飞) | C492409 | LCSC |
| 6 | 1 | ME6211C33M5G-N | LDO1 | SOT-23-5_L3.0-W1.7-P0.95-LS2.8-BL |  | ME6211C33M5G-N | MICRONE(南京微盟) | C82942 | LCSC |
| 7 | 1 | NCD0603R1 | LED1 | LED0603-RD_RED |  | NCD0603R1 | 国星光电 | C84263 | LCSC |
| 8 | 1 | NCD0603B1 | LED2 | LED0603-RD |  | NCD0603B1 | 国星光电 | C84266 | LCSC |
| 9 | 2 | 5.1kΩ | R1,R2 | R0603 | 5.1kΩ | 0603WAF5101T5E | UNI-ROYAL(厚声) | C23186 | LCSC |
| 10 | 2 | 10kΩ | R3,R10 | R0603 | 10kΩ | 0603WAF1002T5E | UNI-ROYAL(厚声) | C25804 | LCSC |
| 11 | 2 | 1kΩ | R4,R5 | R0603 | 1kΩ | FRC0603J102 TS | FOJAN(富捷) | C2907113 | LCSC |
| 12 | 2 | 1kΩ | R6,R7 | R0603 | 1kΩ | RC0603FR-071KL | YAGEO(国巨) | C22548 | LCSC |
| 13 | 1 | TS-1101-B-W | SW1 | KEY-SMD_2P-L6.0-W3.6-P7.4-LS8.0-L |  | TS-1101-B-W | XKB Connection(中国星坤) | C500065 | LCSC |
| 14 | 1 | STM32F030F4P6TR | U1 | SOP-20_L6.5-W4.4-P0.65-LS6.4-BL |  | STM32F030F4P6TR | ST(意法半导体) | C89040 | LCSC |
| 15 | 1 | TYPE-C 6P(073) | USB1 | TYPE-C-SMD_TYPE-C-6P-073 |  | TYPE-C 6P(073) | SHOU HAN(首韩) | C668623 | LCSC |
| 16 | 1 | 12MHz | X1 | CRYSTAL-SMD_4P-L3.2-W2.5-BL | 12MHz | X322512MOB4SI | YXC(扬兴晶振) | C70565 | LCSC |

## 声明

本项目仅供个人学习、研究和非商业用途。严禁任何个人或实体将本项目及其衍生品用于商业销售、盈利活动。

- 本设计仅供参考与学习，未经量产验证，不保证正确性与完整性；使用者须自行校验，因使用本设计造成的任何损失由使用者自行承担。
- 引用、转载或二次开发时请保留原始出处并注明作者；衍生作品须延续上述非商业使用限制。