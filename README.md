LED Toggle Program with FreeRTOS for STM32 Nucleo-767 in STM32CubeIDE
AUTHOR:- Mikhael Sunil

Introduction
This project demonstrates how to toggle an LED using FreeRTOS on the STM32 Nucleo-767ZI board. The STM32CubeIDE is
used to write, compile, and debug the program. The FreeRTOS is utilized to manage task scheduling.

Prerequisites
Hardware: STM32 Nucleo-767ZI board.
Software:
STM32CubeIDE.
STM32CubeMX for project setup (optional).
FreeRTOS library (included in STM32CubeIDE).
Project Structure
The project is structured using STM32CubeIDE with the main program logic contained within main.c. The key components include:

GPIO Initialization: Configures the LED pin.
FreeRTOS Task: A task is created to toggle the LED.
Functionality
The program creates a FreeRTOS task that toggles an LED connected to GPIO pin B14 every 500 milliseconds. The FreeRTOS scheduler manages the task.

Files
main.c: Contains the program's main logic, including the initialization and task creation.
Code Overview
1. System Initialization

HAL_Init();
SystemClock_Config();
MX_GPIO_Init();
These functions initialize the hardware, system clock, and GPIO pins for the LED.

2. FreeRTOS Task Creation

xTaskCreate(LED_blink, "RED_LED", 128, NULL, 1, NULL);
This creates a task called LED_blink with a stack size of 128 words and priority 1.

3. Scheduler Start

vTaskStartScheduler();
This starts the FreeRTOS scheduler, which manages the tasks.

4. LED Toggle Task

void LED_blink(void *pvParameters) {
    while(1) {
        HAL_GPIO_TogglePin(GPIOB, GPIO_PIN_14);
        HAL_Delay(500);
    }
}
This task toggles the LED every 500 milliseconds.

Hardware Configuration
LED Pin: The LED is connected to GPIO Pin B14.
Clock: The system clock is configured to use the HSI (High-Speed Internal oscillator).
Steps to Run the Project
Open STM32CubeIDE and import the project.
Build the project by clicking on the build button.
Flash the project to the STM32 Nucleo-767ZI board.
After flashing, the LED connected to GPIO pin B14 should toggle every 500 milliseconds.

Future Enhancements
Implement more tasks, such as different LED blink patterns.
Use FreeRTOS semaphores or event groups for more complex task synchronization.
