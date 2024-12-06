#  Semaphore
This project is an implementation of a system based on STM32 that analyze contention problems when tasks accessing shared resource function in a multitasking system and how to eliminate it using semaphore.

## Description
This project provides practical examples to understand how to eliminate contention problems with better actions in the project Sharing Resources before. This exercise introduces a more focused mutual exclusion mechanism that minimizes disruptions in system behavior, ensuring only the necessary tasks are affected.  That involves:
1. Learn how to use semaphores for managing access to critical resources in real-time multitasking systems.
2. Replace nterrupt disabling mechanisms with semaphores to achieve mutual exclusion in a selective manner.
3. Compare system performance with and without semaphore-based protection.

## Task Overflow
1. **Initialization**
   - Configure GPIO of LED
   - Create semaphore in FreeRTOS	Configuration	section, by selecting 'Timers and Semaphores'
   - Configure semaphores by adding binary	semaphore	and	give	it	a	name 'CriticalResourceSemaphore'
   - Create tasks, with orange LED task having highest priority
3. **Start Green Flashing Task**
   - Turn the Green LED ON
   - Accessing shared data function
   - Turn the Green LED OFF
   - Delay for 0.5 seconds
5. **Start Red Flashing Task**
   - Turn the Red LED ON
   - Accessing shared data function
   - Turn the Red LED OFF
   - Delay for 0.1 seconds
7. **Access Shared Data**
   - taskENTER_CRITICAL()
   - Check StartFlag
   - If StartFlag up (1), put it down (0)
   - Else show an alert
   - Simulate read/write operation
   - Set back StartFlag up
   - taskEXIT_CRITICAL()

## Hardware Used
- STM32 Microcontroller
- LED
- Resistor

## Demo Video
![VIDEO](https://github.com/aaqfal/FreeRTOS-Semaphore/blob/main/video/video_exercise8.mp4)
