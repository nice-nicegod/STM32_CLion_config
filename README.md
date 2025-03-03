# 📜 CLion + 嘉立创天空星开发板 (STM32F407VET6) 完整配置指南

> 基于 B 站 UP 主 [0XBB8](https://space.bilibili.com/3493142393260061) 教程优化 | 适配 CLion 2024.3+

---

## 🚀 环境准备清单
| 类别        | 要求                                                                 |
|-----------|--------------------------------------------------------------------|
| **开发板**   | 嘉立创天空星开发板 (主控STM32F407VET6)                                       |
| **调试器**   | ST-Link V2 (建议使用原厂调试器)                                         |
| **软件环境**  | Windows 10/11 或 macOS Ventura+                                  |
| **必备工具**  | [CLion](https://www.jetbrains.com/clion/) ➜ 建议2024.3+版本                |
|           | [ARM Toolchain](https://developer.arm.com/downloads/-/gnu-rm) ➜ 12.3.1版本 |
|           | [OpenOCD](https://gnutoolchains.com/arm-eabi/openocd/) ➜ 0.12.0版本       |
|           | [STM32CubeMX](https://www.st.com/stm32cubemx) ➜ 6.9.0+版本              |

---

## 🔧 环境配置详解

### 1. 工具链安装
1. **ARM GCC 安装**  
2. **OpenOCD 配置**  
3. **STM32CubeMX 设置**
###均可以使用msys2进行一步到位进行安装，具体参考视频教程
---


## ⚡此模板已针对 **嘉立创天空星开发板** 优化配置，可直接用于实际项目开发。

## 📚 参考资源

### 0XBB8 视频教程
- [【CLion 嵌入式开发环境配置】手把手搭建 STM32 开发环境](https://www.bilibili.com/video/BV1kmcXeyEES/)  
  `CLion + OpenOCD + STM32CubeMX 全流程配置详解`
  
- [【STM32 项目模板创建】从零构建 HAL 库工程，并用clion进行调试](https://www.bilibili.com/video/BV1c8chemE6L/)  
  `包含代码生成、CMake 配置、调试技巧实战演示`

### 开发板资料
- [嘉立创天空星开发板官方文档](https://wiki.lckit.com/)  
  `➜ 含原理图、PCB 引脚图、硬件设计指南`
  
- [STM32F407VET6 数据手册](https://www.st.com/resource/en/reference_manual/dm00031020-stm32f405-415-stm32f407-417-stm32f427-437-and-stm32f429-439-advanced-arm-based-32-bit-mcus-stmicroelectronics.pdf)  
  `➜ ST 官方参考手册（寄存器级开发必备）`

### 扩展工具
- [STM32CubeMX 配置技巧大全](https://www.st.com/stm32cubemx)  
- [OpenOCD 调试命令速查表](https://openocd.org/doc/html/General-Commands.html)


### 1. 全局工具链配置
```plaintext
File → Settings → Build, Execution, Deployment
├─ Toolchains
│  ├─ Name: ARM Embedded
│  ├─ C Compiler: D:/ArmGCC/bin/arm-none-eabi-gcc.exe
│  └─ C++ Compiler: D:/ArmGCC/bin/arm-none-eabi-g++.exe
└─ Embedded Development
   ├─ OpenOCD Config: D:/OpenOCD/bin/openocd.exe
   └─ Board Config: stm32f4discovery.cfg (或自定义配置文件)


