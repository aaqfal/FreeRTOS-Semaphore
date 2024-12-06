#  Semaphore
This project is an implementation of a system based on STM32 that analyze contention problems when tasks accessing shared resource function in a multitasking system and how to eliminate it using semaphore.

## Description
This project provides practical examples to understand how to eliminate contention problems with better actions in the project Sharing Resources before. This exercise introduces a more focused mutual exclusion mechanism that minimizes disruptions in system behavior, ensuring only the necessary tasks are affected. That involves:
1. Learn how to use semaphores for managing access to critical resources in real-time multitasking systems.
2. Replace nterrupt disabling mechanisms with semaphores to achieve mutual exclusion in a selective manner.
3. Compare system performance with and without semaphore-based protection.

The concept of semaphore is:
1. State: semaphore has 2 main states, release (free) and locked (taken). Release means the resource is available and locked means the resources is currently in use.
2. Count: that involves binary and counting. In binary semaphore, counter is either 0 (locked) or 1 (release) used for single-resource protection. While in counter    
   semaphore, counter can range from 0 to a maximum value, useful when managing multiple instances of a resource.
3. Blocking: tasks waiting for semaphore can either blocked (paused until the semaphore is released) or timeout (wait for a specific time before continuing if the semaphore    remains locked).

Semaphore works like when a task need to access shared resource, it calls osSemaphoreWait(). Then checking if the semaphore is free the task locks it and enters the critical section to use the resource. If there is another task tries to using semaphore while first task is still using the resource, this task blocked or wait for timeout. When first task finish, it calss osSemaphoreRelease() to unlock semaphore. The other task can now acquire the semaphore and proceed with its execution.

## Task Overflow
1. **Initialization**
   - Configure GPIO of LED
   - Create semaphore in FreeRTOS	Configuration	section, by selecting 'Timers and Semaphores'
   - Configure semaphores by adding binary	semaphore	and	give	it	a	name 'CriticalResourceSemaphore'
   - Create tasks, with orange LED task having highest priority
2. **Start Green Flashing Task**
   - Turn the Green LED ON
   - Accessing shared data function
   - Turn the Green LED OFF
   - Delay for 0.2 seconds
3. **Start Red Flashing Task**
   - Turn the Red LED ON
   - Accessing shared data function
   - Turn the Red LED OFF
   - Delay for 0.55 seconds
4. **Start Orange Flashing Task**
   - Toggle the Orange LED at 10Hz
5. **Access Shared Data**
   - osSemaphoreWait(CriticalResourceSemaphoreHandle,WaitTimeMilliseconds)
   - Check StartFlag
   - If StartFlag up (1), put it down (0)
   - Else show an alert
   - Simulate read/write operation
   - Set back StartFlag up
   - osSemaphoreRelease(CriticalResourceSemaphoreHandle)

**Added Exercise**
Set the WaitTimeMilliseconds value to zero and execute the resulting	software

## Hardware Used
- STM32 Microcontroller
- LED
- Resistor

## Demo Video
![VIDEO](https://github.com/aaqfal/FreeRTOS-Semaphore/blob/main/video/video_exercise8.mp4)
