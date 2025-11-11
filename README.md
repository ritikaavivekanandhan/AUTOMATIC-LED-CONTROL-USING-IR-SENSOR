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
  <img width="1920" height="1200" alt="Screenshot (78)" src="https://github.com/user-attachments/assets/ae38c4af-9231-4700-ab13-f104fdfb6fad" />


2. Click **File → New STM32 Project**.
 <img width="1920" height="1200" alt="Screenshot (67)" src="https://github.com/user-attachments/assets/08c1ba50-a985-4954-a980-07dccfede27f" />

<img width="1920" height="1200" alt="Screenshot (65)" src="https://github.com/user-attachments/assets/2d1b8929-50c3-4dbf-858e-105d678d4b39" />

3. Select the **target microcontroller** or board and click **Next**.
   <img width="1920" height="1200" alt="Screenshot (92)" src="https://github.com/user-attachments/assets/802f6791-6d35-4aa0-a35e-42d508fe83e7" />



4. Name the project.
  <img width="1920" height="1200" alt="Screenshot (84)" src="https://github.com/user-attachments/assets/561f8982-fae5-4894-8078-2ec532480e73" />


5. The corresponding `.ioc` file will be generated automatically.
  <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/8900847c-6745-43e2-9ecf-2e66877fdc49" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
<img width="1920" height="1200" alt="Screenshot (70)" src="https://github.com/user-attachments/assets/8a441143-e01b-4443-a043-0c6c6b7c9749" />

<img width="1920" height="1200" alt="Screenshot (95)" src="https://github.com/user-attachments/assets/8c03a1b3-2996-4191-8aa7-7190b6ddabe0" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
  <img width="1920" height="1200" alt="Screenshot (96)" src="https://github.com/user-attachments/assets/aba7de9f-4857-4583-850b-ef8dd7baf817" />

 
8. Edit the generated main program as required.
<img width="1920" height="1200" alt="Screenshot (98)" src="https://github.com/user-attachments/assets/79b966d3-55af-4f4d-a8ca-66129e16bd50" />

<img width="1920" height="1200" alt="Screenshot (105)" src="https://github.com/user-attachments/assets/e23ae543-fe4a-4a02-b3bb-5914bac93a85" />


9. Click **Project → Build All**.
    <img width="1920" height="1200" alt="Screenshot (103)" src="https://github.com/user-attachments/assets/066ef0d6-5400-4722-8ec8-1345adb000e0" />


10. Link the **HEX file** using the post-build process.
    <img width="1617" height="265" alt="image" src="https://github.com/user-attachments/assets/caeaeda0-2382-490a-a511-178665dfaa73" />


11. Click **Debug** and connect the **STM Nucleo Board**.
   <img width="1920" height="1200" alt="Screenshot (103)" src="https://github.com/user-attachments/assets/4207d3fa-c353-4f85-9265-87da6ca784ad" />


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
![WhatsApp Image 2025-11-11 at 20 33 49_60dad78f](https://github.com/user-attachments/assets/45a03d60-1f80-46ff-8cdf-eafa2fb48ae5)


CASE 2: LED OFF
![WhatsApp Image 2025-11-11 at 20 33 50_4f1b79cf](https://github.com/user-attachments/assets/b5d627d9-9a48-4dbd-b5b2-fc52ad357ed5)


---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




