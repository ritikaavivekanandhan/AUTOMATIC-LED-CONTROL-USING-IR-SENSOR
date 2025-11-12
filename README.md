# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
  <img width="1920" height="1200" alt="Screenshot (78)" src="https://github.com/user-attachments/assets/dd9ec410-f03e-4c24-b531-7727c903cf7a" />



2. Click **File → New STM32 Project**.
 <img width="1920" height="1200" alt="Screenshot (79)" src="https://github.com/user-attachments/assets/25bbfb21-2402-4ab6-95e7-8e83ad169419" />
<img width="1920" height="1200" alt="Screenshot (81)" src="https://github.com/user-attachments/assets/d54a24b0-352c-4972-97f4-ad6730f7b542" />

3. Select the **target microcontroller** or board and click **Next**.
   <img width="1920" height="1200" alt="Screenshot (92)" src="https://github.com/user-attachments/assets/72cd62c2-3abb-48c2-8562-ac03b75ac7c6" />



4. Name the project.
 <img width="1920" height="1200" alt="Screenshot (84)" src="https://github.com/user-attachments/assets/0b3a685e-036d-4a0f-846f-46a8573d4b2a" />


5. The corresponding `.ioc` file will be generated automatically
<img width="1920" height="1200" alt="Screenshot (94)" src="https://github.com/user-attachments/assets/2cfc3a5d-3ac4-4bde-83d1-28a96b548547" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
<img width="1920" height="1200" alt="Screenshot (95)" src="https://github.com/user-attachments/assets/91ace6de-7318-47a9-af79-21e762302952" />


<img width="1920" height="1200" alt="Screenshot (96)" src="https://github.com/user-attachments/assets/16f89f47-38a4-485c-b258-473ec199c01a" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
 <img width="1920" height="1200" alt="Screenshot (96)" src="https://github.com/user-attachments/assets/f884c2cb-82b1-4cac-bbe0-5f624f1dfdaa" />

 
8. Edit the generated main program as required.


<img width="1920" height="1200" alt="Screenshot (89)" src="https://github.com/user-attachments/assets/8fff4a1f-6377-48ba-bef8-298d14fa248e" />


<img width="1920" height="1200" alt="Screenshot (104)" src="https://github.com/user-attachments/assets/7959b883-f09a-434d-a06a-bb1bff390f71" />


9. Click **Project → Build All**.
    <img width="1920" height="1200" alt="Screenshot (103)" src="https://github.com/user-attachments/assets/066ef0d6-5400-4722-8ec8-1345adb000e0" />


10. Link the **HEX file** using the post-build process.

    <img width="1435" height="232" alt="image" src="https://github.com/user-attachments/assets/eb2b3084-c9b8-4775-a43b-8a86f33c6352" />



11. Click **Debug** and connect the **STM Nucleo Board**.

  <img width="1920" height="1200" alt="Screenshot (102)" src="https://github.com/user-attachments/assets/417ef1cc-fb10-4ea3-88c7-1eae4f3b3b32" />

13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

![WhatsApp Image 2025-11-11 at 20 33 49_241f2999](https://github.com/user-attachments/assets/bf8054da-7468-4dc9-a4a1-67c37c37a4bc)


CASE 2: LED OFF

![WhatsApp Image 2025-11-11 at 20 33 50_39c5ac94](https://github.com/user-attachments/assets/efc1854b-1fb6-4412-b157-9199c42b65ec)


---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




