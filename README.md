# TerraSight

TerraSight 是一个强大的物联网设备监控与数据可视化系统，专为ESP32-S3和STM32系列设备提供全面的管理、控制和数据采集功能。

## 项目概述

TerraSight 提供了一套完整的解决方案，用于实时监控、数据采集、可视化展示和设备管理。系统采用Python与C++混合架构，结合了PyQt5的图形界面能力和C++的高性能通信处理，为工业和研究环境提供可靠的数据监控平台。

## 系统架构

### 技术栈

- **前端界面**：PyQt5
- **数据可视化**：PyQtGraph, NumPy, Pandas
- **后端通信**：C++ (Boost ASIO)
- **设备支持**：ESP32-S3, STM32
- **通信协议**：串口, TCP/IP, WiFi

### 目录结构

```
TerraSight/
├── .vscode/              # VS Code配置文件
├── cpp/                  # C++通信库
│   ├── build/            # 编译输出目录
│   ├── include/          # 头文件
│   └── src/              # 源代码
├── python/               # Python应用程序
│   ├── core/             # 核心功能模块
│   ├── data_analysis/    # 数据分析模块
│   ├── libs/             # 第三方库
│   ├── logs/             # 日志文件
│   ├── main.py           # 主程序入口
│   ├── pet_assistant/    # 宠物助手功能
│   ├── resources/        # 资源文件
│   ├── scripts/          # 脚本文件
│   ├── setup.py          # 安装脚本
│   ├── tests/            # 测试文件
│   ├── ui/               # 用户界面组件
│   │   ├── dialogs/      # 对话框
│   │   │   ├── login_dialog.py
│   │   │   └── user_manager_dialog.py
│   │   ├── displays/     # 显示界面
│   │   │   ├── hologram_view.py
│   │   │   └── main_display.py
│   │   └── widgets/      # 各种控件
│   │       ├── base_widget.py
│   │       ├── device_control_widget.py
│   │       ├── device_status_widget.py
│   │       ├── serial_widget.py
│   │       ├── solar_system_widget.py
│   │       └── tcp_widget.py
│   ├── update_package/   # 更新包目录
│   ├── updater.py        # 自动更新程序
│   ├── user_management/  # 用户管理
│   │   ├── permission_manager.py
│   │   └── user_manager.py
│   ├── utils/            # 工具类
│   │   ├── animation_utils.py
│   │   ├── config_loader.py
│   │   ├── drawing_utils.py
│   │   └── style_manager.py
│   └── visualization/    # 可视化组件
│       ├── data_visualization.py
│       ├── map_visualization.py
│       └── particle_effect.py
└── README.md             # 项目文档
```

## 核心功能

### 1. 设备管理

- **多协议连接管理**：支持串口、TCP和WiFi多种连接方式
- **自动重连机制**：设备断开后自动尝试重新连接
- **心跳监控**：定期发送心跳包，确保设备连接状态
- **设备信息采集**：自动收集设备固件版本、硬件信息等

### 2. 设备专用管理器

#### ESP32-S3 管理器
- 通过串口或TCP连接ESP32-S3设备
- 管理设备配置和状态监控
- 支持固件版本查询和系统信息获取
- 监控STM32连接状态

#### STM32 管理器
- 通过ESP32-S3与STM32通信
- 支持GPIO控制、ADC采样、PWM输出
- 管理定时器和数据采集参数
- 提供设备健康状态监控

### 3. 数据采集与处理

- **实时数据采集**：从设备获取实时数据
- **多格式数据处理**：支持波形、雷达、散点等多种数据格式
- **数据缓冲处理**：优化大量数据的接收和处理
- **异步通信**：非阻塞数据传输确保系统响应性

### 4. 可视化展示

- **波形图显示**：实时绘制设备数据波形
- **雷达图展示**：用于空间数据的可视化
- **散点图分析**：用于数据相关性分析
- **地图可视化**：地理数据展示
- **太阳系背景**：提供宇宙风格的可视化背景

### 5. 通信管理

- **多协议支持**：串口、TCP/IP通信
- **异步通信**：基于Boost ASIO的高性能通信
- **错误处理**：完善的异常捕获和处理机制
- **连接诊断**：网络连接问题诊断功能

### 6. 自动更新系统

- **版本检查**：自动检查软件更新
- **增量更新**：支持部分文件更新，节省带宽
- **智能重启**：更新完成后自动重启应用

### 7. 用户管理

- **用户登录系统**：基于角色的权限管理
- **权限控制**：不同用户角色具有不同操作权限
- **配置管理**：用户偏好设置的保存和加载

## 核心模块说明

### core/ 模块

- **communication.py**：通信管理器，负责串口和TCP通信
- **device_controller.py**：设备控制器，统一管理所有连接的设备
- **device_status_manager.py**：设备状态管理器，监控设备健康状态
- **esp32_manager.py**：ESP32-S3设备管理器
- **stm32_manager.py**：STM32设备管理器

### visualization/ 模块

- **data_visualization.py**：数据可视化组件
- **map_visualization.py**：地图可视化组件
- **plot_manager.py**：绘图管理器
- **solar_system_widget.py**：太阳系背景组件

### ui/ 模块

- **displays/main_display.py**：主显示界面
- **widgets/**：各种UI控件，如串口控件、TCP控件等

## 安装指南

### 环境要求

- Python 3.8+
- PyQt5 5.15.9+
- NumPy 1.26.2+
- PyQtGraph 0.13.3+

### 安装步骤

1. 克隆或下载项目源码
2. 安装Python依赖

```bash
cd python
pip install -r requirements.txt
```

3. 编译C++通信库（如果需要）

```bash
cd ../cpp
# 使用项目中提供的构建脚本
```

4. 运行主程序

```bash
cd ../python
python main.py
```

## 使用说明

### 设备连接

1. 在主界面中选择连接类型（串口/TCP）
2. 配置连接参数（端口/IP地址和端口）
3. 点击连接按钮建立设备连接

### 数据监控

1. 连接设备后，系统自动开始数据采集
2. 在可视化区域可切换不同的显示模式（波形/雷达/散点）
3. 使用工具栏上的按钮调整显示参数

### 设备控制

1. 在设备控制面板中，可以发送命令到设备
2. 可设置设备参数如采样率、数据格式等
3. 监控设备状态和健康信息

## 系统配置

系统配置文件位于`python/resources/`目录下：

- `terrasight_config.json`: 主程序配置
- `device_status_config.json`: 设备状态配置
- `esp32_config.json`: ESP32设备配置
- `role_permissions.json`: 用户权限配置

## 许可证

此项目仅供内部使用，未经授权不得用于商业用途。
