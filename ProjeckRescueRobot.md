Rescue Robot – Multi-Inheritance in Java (Interfaces + Composition)
แนวคิดของงาน

โปรเจกต์นี้แสดงการทำ Multi-Inheritance ใน Java อย่างถูกต้อง
เนื่องจาก Java ไม่สามารถ extends ได้มากกว่า 1 class
จึงใช้แนวทางดังนี้

Multiple Interfaces

Default Method + Override (แก้ปัญหาเมธอดชื่อชนกัน)

Composition (ประกอบคลาสย่อยเป็นชิ้นส่วน)

เป้าหมายการเรียนรู้

อธิบายได้ว่า Java ไม่รองรับ Multiple Inheritance ของ Class

ใช้ Multiple Interfaces เพื่อจำลองหลายบทบาท

แก้ปัญหา default method ชื่อชนกันด้วย @Override

ใช้ Composition รวมความสามารถหลายอย่างในคลาสเดียว

ทดสอบการทำงานผ่าน main()

สถานการณ์

สร้างหุ่นยนต์กู้ภัย RescueRobot ที่มีหลายบทบาทพร้อมกัน:

บินได้ (Flyable)

ขับบนพื้นได้ (Drivable)

ตรวจจับความร้อน (ThermalSensor)

ส่งข้อความและพิกัด (Communicable)

โครงสร้างโปรเจกต์
rescue-robot/
│
├─ Main.java
├─ RescueRobot.java
├─ Flyable.java
├─ Drivable.java
├─ ThermalSensor.java
├─ Communicable.java
│
├─ Battery.java
├─ GPSTracker.java
└─ ThermalCamera.java
1. Multiple Interfaces
Flyable

takeOff()

land()

maxAltitude()

default status() → "FLY MODE"

Drivable

startEngine()

stopEngine()

maxSpeed()

default status() → "DRIVE MODE"

ThermalSensor

readTemperatureC()

detectHuman(thresholdC)

Communicable

send(message)

getDeviceId()

2. การแก้ปัญหาเมธอดชื่อชนกัน

Flyable และ Drivable มี default method ชื่อเดียวกันคือ status()

ดังนั้นใน RescueRobot ต้อง Override เอง:

@Override
public String status() {
    return "ROBOT: "
        + Flyable.super.status()
        + " + "
        + Drivable.super.status();
}

ผลลัพธ์:

ROBOT: FLY MODE + DRIVE MODE
3. Composition (Multi-Inheritance เชิงออกแบบ)

แทนที่จะสืบทอดหลาย class
ใช้การประกอบคลาสย่อยเข้าไปแทน

Battery

เก็บเปอร์เซ็นต์แบตเตอรี่

drain()

charge()

GPSTracker

updatePosition()

currentPosition()

ThermalCamera

readTemperatureC()

detectHuman()

ใน RescueRobot มี field ดังนี้

private Battery battery;
private GPSTracker gps;
private ThermalCamera thermal;
กติกาการทำงาน

ทุก action ต้อง drain battery

send() ต้องส่งพิกัดปัจจุบันไปด้วย

รูปแบบข้อความ:

ID=RR-01, POS=(lat,lon), MSG=Found hotspot...
4. Scenario Test (Main)

ลำดับการทำงาน:

สร้าง RescueRobot("RR-01")

updatePosition(...)

takeOff → status → land

startEngine → maxSpeed → stopEngine

readTemperatureC → detectHuman(36.5)

send("Found hotspot...")