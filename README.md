# 📜 CLion + 嘉立创天空星开发板 (STM32F407VET6) 完整配置指南

> 基于 B 站 UP 主 [0XBB8](https://space.bilibili.com/3493142393260061) 教程优化 | 适配 CLion 2023.3+

---

## 🚀 环境准备清单
| 类别        | 要求                                                                 |
|-----------|--------------------------------------------------------------------|
| **开发板**   | 嘉立创天空星开发板 (主控STM32F407VET6)                                       |
| **调试器**   | ST-Link V2 (建议使用原厂调试器)                                         |
| **软件环境**  | Windows 10/11 或 macOS Ventura+                                  |
| **必备工具**  | [CLion](https://www.jetbrains.com/clion/) ➜ 建议2023.3+版本                |
|           | [ARM Toolchain](https://developer.arm.com/downloads/-/gnu-rm) ➜ 12.3.1版本 |
|           | [OpenOCD](https://gnutoolchains.com/arm-eabi/openocd/) ➜ 0.12.0版本       |
|           | [STM32CubeMX](https://www.st.com/stm32cubemx) ➜ 6.9.0+版本              |

---

## 🔧 环境配置详解

### 1. 工具链安装
1. **ARM GCC 安装**  
   - 下载 `gcc-arm-none-eabi-12.3.1` 并安装至无空格路径（例如：`D:\ArmGCC`）
   - 验证安装：终端执行 `arm-none-eabi-gcc -v` 应显示版本信息

2. **OpenOCD 配置**  
   - 解压下载的OpenOCD至指定目录（例如：`D:\OpenOCD`）
   - 添加环境变量：`Path` ➜ `D:\OpenOCD\bin`

3. **STM32CubeMX 设置**  
   - 安装时勾选`F4系列`软件包
   - 配置路径：`Help → Manage embedded software packages` 安装`STM32F4xx`支持包

---

## ⚡ CLion 项目配置流程

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
