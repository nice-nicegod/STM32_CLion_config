# 📜 CLion + 嘉立创天空星开发板 (STM32F407VET6) 完整配置指南

> 基于 B 站 UP 主 [0XBB8](https://space.bilibili.com/3493142393260061) 教程优化 | 适配 CLion 2024.3+
> 现在已经更新了 STM32F103C8 开发板,并且 clion 正在 25.1 版本中支持原生 stlink，现在配置也已经上传

---

## 🚀 环境准备清单

| 类别         | 要求                                                                        |
| ------------ | --------------------------------------------------------------------------- |
| **开发板**   | 嘉立创天空星开发板 (主控 STM32F407VET6)                                     |
| **调试器**   | ST-Link V2 (建议使用原厂调试器)                                             |
| **软件环境** | Windows 10/11 或 macOS Ventura+                                             |
| **必备工具** | [CLion](https://www.jetbrains.com/clion/) ➜ 建议 2024.3+版本                |
|              | [ARM Toolchain](https://developer.arm.com/downloads/-/gnu-rm) ➜ 12.3.1 版本 |
|              | [OpenOCD](https://gnutoolchains.com/arm-eabi/openocd/) ➜ 0.12.0 版本        |
|              | [STM32CubeMX](https://www.st.com/stm32cubemx) ➜ 6.9.0+版本                  |

---

## 🔧 环境配置详解

### 1. 工具链安装 (MSYS2 集成方案)

**推荐使用 MSYS2 一键式安装**，避免多平台工具混杂问题，操作流程如下：

```bash
# 1. 安装 MSYS2 (https://www.msys2.org/)
# 2. 更新软件包数据库
pacman -Syu

# 3. 安装 ARM GCC 工具链
pacman -S mingw-w64-x86_64-arm-none-eabi-gcc

# 4. 安装 OpenOCD
pacman -S mingw-w64-x86_64-openocd

# 5. 安装 STM32CubeMX (需手动下载)
# 从官网获取安装包后，在 MSYS2 环境运行：
# ./SetupSTM32CubeMX-6.9.0.exe

# 检查编译器版本
arm-none-eabi-gcc -v

# 验证 OpenOCD 支持
openocd -v
openocd -f interface/stlink.cfg -f target/stm32f4x.cfg
```

---

## ⚡ 此模板已针对 **嘉立创天空星开发板** 优化配置，可直接用于实际项目开发。

## 📚 参考资源

### 0XBB8 视频教程

- [【CLion 嵌入式开发环境配置】手把手搭建 STM32 开发环境](https://www.bilibili.com/video/BV1kmcXeyEES/)  
  `CLion + OpenOCD + STM32CubeMX 全流程配置详解`
- [【STM32 项目模板创建】从零构建 HAL 库工程，并用 clion 进行调试](https://www.bilibili.com/video/BV1c8chemE6L/)  
  `包含代码生成、CMake 配置、调试技巧实战演示`

### 开发板资料

- [嘉立创天空星开发板官方文档](https://wiki.lckfb.com/zh-hans/tkx/tkx-stm32f407vxt6/)  
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


```
