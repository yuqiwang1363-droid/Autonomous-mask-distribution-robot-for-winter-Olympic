# Control Logic and State Machine

## Overview

The control logic of the autonomous mask distribution and recycling robot
is designed using a **Finite State Machine (FSM)** framework.
This approach ensures safe, predictable, and robust behavior during
human–robot interaction in public environments.

The FSM-based design simplifies coordination between sensing, actuation,
and navigation subsystems.

---

## Design Philosophy

- Event-driven state transitions based on sensor feedback  
- Clear separation of navigation and service behaviors  
- Safety-oriented handling of abnormal conditions  
- Modular logic design for future extension  

---

## Main System States

### 1. Navigation State

**Description**  
The robot autonomously navigates along a predefined or planned path
within the public venue.

**Active Components**
- Mobile platform
- Obstacle detection sensors

**Exit Conditions**
- Human detected near the robot  
- Service request triggered  
- Low battery / system alert  

---

### 2. Temperature Measurement State

**Description**  
The robot performs non-contact body temperature measurement
using an infrared temperature sensor.

**Logic**
- If temperature is within normal range → proceed to mask dispensing  
- If abnormal temperature is detected → trigger warning and safety handling  

---

### 3. Mask Dispensing State

**Description**  
The robot dispenses a single mask to the user.

**Logic**
- Stop robot motion  
- Activate motor-driven roller mechanism  
- Infrared sensor confirms successful mask output  
- Resume navigation after mask is taken  

---

### 4. Hand Sanitization State

**Description**  
Automatic hand sanitization is performed when hands are detected
near the sanitization outlet.

**Logic**
- Infrared proximity sensor detects hand presence  
- Time-based condition ensures sufficient dwell time  
- Sanitization pump is activated  
- System returns to navigation state after completion  

---

### 5. Mask Recycling State

**Description**  
The robot collects used masks through a dedicated recycling port.

**Logic**
- Used-mask input detected  
- Mask stored in internal collection bin  
- UV disinfection activated  
- Bin capacity monitored  

---

### 6. Return-to-Base State

**Description**  
The robot returns to its base station for maintenance or recharging.

**Trigger Conditions**
- Low battery level  
- Mask supply depleted  
- Recycling bin full  

---

## State Transition Summary

- Navigation → Temperature Measurement → Mask Dispensing  
- Navigation → Hand Sanitization  
- Navigation → Mask Recycling  
- Any State → Return-to-Base (upon system alert)  

This FSM structure ensures smooth and safe transitions between
navigation and service-related behaviors.

---

## Advantages of FSM-Based Control

- Improved system reliability  
- Simplified debugging and testing  
- Clear behavior definition  
- Enhanced safety during human interaction  

---

---

# 控制逻辑与状态机设计（中文版）

## 总体说明

本自动化口罩发放与回收机器人采用**有限状态机（Finite State Machine, FSM）**
作为核心控制逻辑框架，用于管理机器人在不同工作模式下的行为切换。
该设计能够有效提升系统的安全性、可靠性与可维护性。

---

## 设计思想

- 基于事件触发的状态切换机制  
- 将巡航行为与服务行为进行明确区分  
- 对异常情况进行安全优先处理  
- 便于后续功能扩展与系统升级  

---

## 系统主要状态

### 1. 自主巡航状态

**说明**  
机器人在场馆内按照规划路径进行自主移动。

**主要功能**
- 移动底盘驱动  
- 避障与环境感知  

**状态切换条件**
- 检测到用户接近  
- 触发服务请求  
- 电量或系统异常  

---

### 2. 测温状态

**说明**  
机器人使用红外传感器进行非接触式体温检测。

**逻辑**
- 体温正常 → 进入口罩发放状态  
- 体温异常 → 触发报警与安全处理流程  

---

### 3. 口罩发放状态

**说明**  
机器人向用户发放单个口罩。

**逻辑**
- 停止底盘运动  
- 启动电机驱动的口罩发放机构  
- 红外传感器确认口罩成功发放  
- 用户取走口罩后恢复巡航  

---

### 4. 手部消毒状态

**说明**  
当检测到用户手部靠近时，自动进行消毒操作。

**逻辑**
- 红外传感器检测手部存在  
- 满足时间条件后启动消毒装置  
- 消毒完成后返回巡航状态  

---

### 5. 口罩回收状态

**说明**  
机器人回收已使用口罩并进行消毒处理。

**逻辑**
- 检测到废弃口罩投入  
- 口罩进入回收盒  
- 启动紫外线消毒  
- 实时监测回收盒容量  

---

### 6. 自动回仓状态

**说明**  
机器人返回基站进行维护或补给。

**触发条件**
- 电量不足  
- 新口罩耗尽  
- 回收盒已满  

---

## 状态切换总结

- 巡航 → 测温 → 口罩发放  
- 巡航 → 手部消毒  
- 巡航 → 口罩回收  
- 任意状态 → 自动回仓（异常或维护需求）  

该状态机结构保证了系统行为的清晰性与安全性，
适用于实际公共场所的人机交互场景。

---

## FSM 控制优势

- 行为逻辑清晰，便于理解与调试  
- 提高系统运行稳定性  
- 降低多模块协同复杂度  
- 提升人机交互安全性  
