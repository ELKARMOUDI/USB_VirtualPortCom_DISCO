# STM32 USB CDC Virtual COM Port / Tera Term

![STM32](https://img.shields.io/badge/STM32F411-Discovery-03234B?logo=stmicroelectronics&logoColor=white)
![USB](https://img.shields.io/badge/USB-CDC_Device-2496ED?logo=usb&logoColor=white)
![Protocol](https://img.shields.io/badge/Protocol-Virtual_COM_Port-blueviolet)

<img src="https://github.com/user-attachments/assets/7d0d10b5-fbbb-4f97-aea7-ddbb0be63d22" alt="53A6C479-32F1-45D4-82F6-907789DB182C">


## Features
- 📡 **USB CDC ACM** (Abstract Control Model) implementation
- 💻 Virtual COM Port enumeration on host PC
- 🔁 Periodic message transmission (400ms interval)
- ⚡ 96MHz system clock via 8MHz HSE + PLL

## Hardware Requirements
- STM32F411 Discovery Board
- Micro-USB cable (connect to CN5 USB FS port)

## Default Behavior
1. Board enumerates as USB CDC device
2. Sends "Hello from CubeIDE" message every 400ms
3. COM port parameters:
   - 115200 baud (default)
   - 8 data bits, no parity, 1 stop bit
   - No hardware flow control

## Code Highlights
```c
uint8_t message[50] = "Hello from CubeIDE \n";

while (1) {
    CDC_Transmit_FS(message, strlen((char *)message));
    HAL_Delay(400);
}
