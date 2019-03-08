# 选择设备:
  * 新建 或选择  Project -> Option... -> Device -> ARM -> ARMCM3
  * 确定后添加 Run Time Environment:
    * CMSIS -> CORE
    * Device -> Startup


# 项目结构
    /User
    /Doc
    /FreeRTOS/Source/include
    /FreeRTOS/Source/portable/RVDS
    /RTE
    
    
# 添加依赖:
  * 将 FreeRTOSv9.0.0\FreeRTOS\Source\include 下的文件拷贝到 FreeRTOS\Source\include 下
  * 将 FreeRTOSv9.0.0\FreeRTOS\Source\portable\RVDS\ARM_CM3 下文件拷贝到 FreeRTOS\Source\portable\RVDS\ARM_CM3 下
  * 设置 Project -> Option... -> C/C++ -> Include paths，将以上两个目录加入列表.


# 新建 FreeRTOSConfig.h

    #ifndef FREERTOS_CONFIG_H
    #define FREERTOS_CONFIG_H
    
    #define configUSE_PREEMPTION		1
    #define configUSE_IDLE_HOOK			0
    #define configUSE_TICK_HOOK			0
    #define configCPU_CLOCK_HZ			( ( unsigned long ) 72000000 )	
    #define configTICK_RATE_HZ			( ( TickType_t ) 1000 )
    #define configMAX_PRIORITIES		( 5 )
    #define configMINIMAL_STACK_SIZE	( ( unsigned short ) 128 )
    #define configTOTAL_HEAP_SIZE		( ( size_t ) ( 17 * 1024 ) )
    #define configMAX_TASK_NAME_LEN		( 16 )
    #define configUSE_TRACE_FACILITY	0
    #define configUSE_16_BIT_TICKS		0
    #define configIDLE_SHOULD_YIELD		1
    
    #define configUSE_CO_ROUTINES 		0
    #define configMAX_CO_ROUTINE_PRIORITIES ( 2 )
    
    #define INCLUDE_vTaskPrioritySet		1
    #define INCLUDE_uxTaskPriorityGet		1
    #define INCLUDE_vTaskDelete				1
    #define INCLUDE_vTaskCleanUpResources	0
    #define INCLUDE_vTaskSuspend			1
    #define INCLUDE_vTaskDelayUntil			1
    #define INCLUDE_vTaskDelay				1
    
    #define configKERNEL_INTERRUPT_PRIORITY 		255
    
    #define configMAX_SYSCALL_INTERRUPT_PRIORITY 	191
    
    #define configLIBRARY_KERNEL_INTERRUPT_PRIORITY	15
    
    #endif /* FREERTOS_CONFIG_H */


# 新建 main.c

    #include<FreeRTOS.h>
    ...
