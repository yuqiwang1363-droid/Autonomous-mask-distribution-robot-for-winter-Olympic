# System Architecture Overview

## Overall System Design

The autonomous mask distribution and recycling robot is designed as a modular
mechatronic system intended for operation in large public venues.
The system integrates mobility, sensing, actuation, and control to enable
autonomous mask management and health-related interactions with humans.

To improve robustness, maintainability, and scalability, the robot is decomposed
into several functionally independent but tightly coordinated subsystems.

---

## Subsystem Decomposition

### 1. Mobile Platform

The mobile platform serves as the physical carrier of the entire system.

- Mecanum-wheel chassis enabling omnidirectional motion
- Four independently driven DC gear motors
- Designed to operate in crowded environments with limited maneuvering space

The omnidirectional mobility allows the robot to approach users from different
directions without requiring large turning radii.

---

### 2. Mask Dispensing Module

The mask dispensing module is responsible for reliable single-mask delivery.

- Motor-driven roller mechanism
- Infrared sensor for detecting mask presence and successful dispensing
- Modular and detachable mask box design for easy replenishment

This design ensures that only one mask is delivered per interaction and
prevents jamming or multiple-mask output.

---

### 3. Mask Recycling and Disinfection Module

The recycling module handles used-mask collection and contamination reduction.

- Dedicated used-mask input port
- Removable collection bin for maintenance
- UV disinfection unit to reduce secondary contamination risks
- Full-capacity detection triggering return-to-base behavior

---

### 4. Health Screening and Hand Sanitization Module

This module enables non-contact health-related interaction.

- Infrared temperature sensor for non-contact body temperature measurement
- Automatic hand sanitization triggered by infrared proximity sensing
- Designed to minimize direct human–robot contact

Abnormal temperature readings trigger warning and system-level safety handling.

---

### 5. Control System

The control system coordinates all subsystems through centralized logic.

- Central microcontroller managing sensors and actuators
- Event-driven control based on sensor feedback and timing conditions
- Finite state machine structure governing system behavior

The control system ensures safe interaction, reliable sequencing of actions,
and smooth transitions between navigation and service states.

---

## System Integration Philosophy

The system architec


---

# 系统总体架构说明（System Architecture）

## 系统总体设计

本自动化口罩发放与回收机器人被设计为一个**模块化的机电一体化系统**，
面向大型公共场所（如冬奥会场馆）运行。系统通过集成移动底盘、传感器、
执行机构与集中控制逻辑，实现口罩管理与健康防护相关的人机交互功能。

为提高系统的可靠性、可维护性与可扩展性，整体系统被拆分为若干
**功能相对独立、接口清晰、相互协同的子系统**。

---

## 子系统划分

### 1. 移动底盘系统

移动底盘系统作为整机的物理载体，负责机器人在场馆内的自主移动。

- 采用麦克纳姆轮结构，实现全向移动能力  
- 四个独立驱动的减速直流电机  
- 适用于人员密集、转向空间受限的公共环境  

全向移动能力使机器人无需大幅转向即可接近目标用户，
提高了在复杂环境中的机动性与安全性。

---

### 2. 口罩发放模块

口罩发放模块负责实现**单口罩、可靠、可控**的发放过程。

- 基于电机驱动胶轮的口罩输送机构  
- 红外传感器用于检测口罩是否成功发放  
- 模块化、可拆卸口罩盒设计，便于补充与维护  

该设计可有效避免多口罩同时掉落或卡滞等问题，
保证发放过程的稳定性。

---

### 3. 口罩回收与消毒模块

该模块用于处理已使用口罩并降低二次污染风险。

- 独立的废弃口罩投放入口  
- 可拆卸式回收盒，便于集中清理  
- 内置紫外线消毒装置，用于杀菌处理  
- 回收盒满载检测，用于触发自动回仓逻辑  

---

### 4. 健康检测与手部消毒模块

该模块用于实现非接触式的人体健康相关交互。

- 非接触式红外测温传感器  
- 基于红外感应的人手靠近检测  
- 自动触发的手部消毒喷洒装置  

当检测到体温异常时，系统将进入安全处理流程，
以保障人员与设备安全。

---

### 5. 控制系统

控制系统作为系统核心，负责协调各子系统的运行。

- 中央控制器统一管理传感器与执行机构  
- 基于事件触发的控制逻辑设计  
- 采用有限状态机（FSM）对系统行为进行管理  

控制系统保证了机器人在巡航、服务与回仓等状态之间
平稳、安全地切换。

---

## 系统集成设计思想

系统整体采用模块化设计思想：

- 各子系统可独立设计、调试与测试  
- 明确的接口定义降低系统集成复杂度  
- 模块化结构便于后续功能扩展，如多机器人协同  

该系统架构适用于真实公共场景部署，并支持后续迭代与优化。
