## Assignment Title: หุ่นยนต์กู้ภัยอัจฉริยะ (Rescue Robot)

## Student Information
- Name:นายณัฏฐนัน นามสกุล เอ่งฉ้วน
- Student ID:68122250001
- Submission Date:19/02/2569
---

## Problem Description
อธิบํายโจทย์โดยย่อ:
หน่วยกู้ภัยต้องกําร “RescueRobot” 1 ตัว ที่มีหลํายบทบําทพร้อมกัน:
- บินได้ เพื่อเข้ําถึงพื้นที่ยําก
- วิ่งบนพื้นได้ เพื่อขนของ
- ตรวจจับควํามร้อน เพื่อหําเหยื่อ
- สื่อสําร เพื่อส่งพิกัด

---

## Learning Objectives
- เข้าใจแนวคิด OOP เช่น Encapsulation, Inheritance, Polymorphism, Composition
- ออกแบบ class และ relationship
- เขียนโปรแกรมเชิงวัตถุอย่ํางเป็นระบบ

---

## System Design
# Flyable
- void takeOff();
- void land();
- double maxAltitude();
# Drivable
- void startEngine();
- void stopEngine();
- double maxSpeed();
# ThermalSensor
- double readTemperatureC();
- boolean detectHuman(double thresholdC);
# Communicable
- void send(String message);
- String getDeviceId();

### Key Classes
- Class A → หน้ําที่
- Class B → หน้ําที่
- Class C → หน้ําที่

---

## OOP Concepts Used
- Encapsulation:
- Inheritance:
- Polymorphism:
- Abstraction:
- Composition (ถ้ํามี):
อธิบายว่าใช้ตรงไหนและทำไม

---

## How to Compile and Run

### Java Example
```bash
javac *.java
java Main