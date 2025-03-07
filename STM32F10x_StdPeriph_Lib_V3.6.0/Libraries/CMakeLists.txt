# CMake Minimum Required Version Information
cmake_minimum_required(VERSION 3.15)

# Describe project information.
project(
    # Project Name
    STM32F1xx_StdPeriph_Driver_V3.6.0
    # Version <Major>.<Minor>.<Patch>.<Tweak>
    VERSION         0.0.0.1
    # Project Description
    DESCRIPTION     "Standard Periph Platform Library"
    # Project Language
    LANGUAGES       C ASM
)

#  Assembler Compile Definitions
#使用前面模块定义的${ADEFINES}变量定义汇编宏ADEFINES
set(ADEFINES ${ADEFINES}

)

# C Compile Definitions
#使用前面模块定义的${CDEFINES}变量定义C宏CDEFINES
set(CDEFINES ${CDEFINES}
  USE_STDPERIPH_DRIVER
  STM32F10X_HD
)

# Assembler Compile Options
#使用前面模块定义的${AFLAGS}变量定义汇编器编译器选项AFLAGS
set(AFLAGS ${AFLAGS}

)

# C Compiler Options
#使用前面模块定义的${CFLAGS}变量定义C编译器器编译器选项CFLAGS
set(CFLAGS  ${CFLAGS}
  -std=c11
  -O1
)


# Compile Include Paths
set(INCS
  CMSIS/CM3/CoreSupport
  CMSIS/CM3/DeviceSupport/ST/STM32F10x

  STM32F10x_StdPeriph_Lib_V3.6.0/Libraries/STM32F10x_StdPeriph_Driver/inc
  STM32F10x_StdPeriph_Driver/inc
)

set(STM32F1_STDLIB_CSRCS
  CMSIS/CM3/DeviceSupport/ST/STM32F10x/system_stm32f10x.c

  STM32F10x_StdPeriph_Driver/src/misc.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_adc.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_bkp.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_can.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_cec.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_crc.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_dac.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_dbgmcu.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_dma.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_exti.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_flash.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_fsmc.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_gpio.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_i2c.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_iwdg.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_pwr.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_rcc.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_rtc.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_sdio.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_spi.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_tim.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_usart.c
  STM32F10x_StdPeriph_Driver/src/stm32f10x_wwdg.c
)

set(STM32F1_STDLIB_ASRCS
  CMSIS/CM3/DeviceSupport/ST/STM32F10x/startup/arm/startup_stm32f10x_hd.s
)

# FMC/FSMC only defined for some F4 families
# if (DEVICE_FAMILY STREQUAL STM32F427_437xx OR DEVICE_FAMILY STREQUAL STM32F429_439xx OR DEVICE_FAMILY STREQUAL STM32F446xx OR DEVICE_FAMILY STREQUAL STM32F469_479xx)
#   set(sources ${sources} Src/stm32f4xx_fmc.c)
# else()
#   set(sources ${sources} Src/stm32f4xx_fsmc.c)
# endif()

set(LIBSRC
  ${STM32F1_STDLIB_CSRCS}
  ${STM32F1_STDLIB_ASRCS}
)

# To Generate Library, Include Template
#此模块使用此前定义的变量设置编译目标的源码文件、包含路径、编译宏定义以及编译选项
include(${CMAKE_SOURCE_DIR}/CMakeTools/armclang/Template/Library.cmake)
