<div align="center">
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=42&pause=1400&color=00E5FF&center=true&vCenter=true&repeat=true&width=1000&height=90&lines=Hello!;Welcome+to+My+GitHub+Profile" />

# Moez Chagraoui
### Embedded Systems Engineer

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=24&pause=1200&color=7C4DFF&center=true&vCenter=true&repeat=true&width=1000&height=60&lines=Embedded+Systems+Engineer;Embedded+Linux+%7C+Yocto+%7C+OTA;RTOS+%26+Low-Level+Programming;C%2FC%2B%2B+%7C+STM32+%7C+Linux+%7C+FPGA;Secure+Boot+%7C+SWUpdate+%7C+U-Boot;Cloud+OTA+%7C+RSA+%7C+A%2FB+Partition" />

<br>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=Moez-La&color=blue&style=for-the-badge"/>
</p>

</div>

---

# About Me

Embedded Systems Engineer — double degree INP-ENSEEIHT Toulouse / ENIT.  
Specialized in low-level **C/C++**, **RTOS**, and **Embedded Linux** development.  
Experience on **STM32** (Cortex-M), **FPGA** (Nios II), and real-time systems validated on physical hardware.  
Built a production-ready **secure OTA platform** (Yocto + SWUpdate + U-Boot Secure Boot + Cloud) and an **industrial predictive maintenance system** in C bare-metal on STM32 validated in real production.

Currently focused on: **Embedded Linux · Secure OTA · RTOS Internals · Driver Development**

---

# Tech Stack

## Languages

![C](https://img.shields.io/badge/C-00599C?style=flat&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=flat&logo=c%2B%2B&logoColor=white)
![Python](https://img.shields.io/badge/Python-FFD43B?style=flat&logo=python&logoColor=black)
![Bash](https://img.shields.io/badge/Bash-121011?style=flat&logo=gnu-bash&logoColor=white)
![VHDL](https://img.shields.io/badge/VHDL-543978?style=flat)

---

## Embedded & Low-Level
![Yocto](https://img.shields.io/badge/Yocto-0094D6?style=flat)
![SWUpdate](https://img.shields.io/badge/SWUpdate-FF6600?style=flat)
![U--Boot](https://img.shields.io/badge/U--Boot-003366?style=flat)
![OpenSSL](https://img.shields.io/badge/OpenSSL-721412?style=flat&logo=openssl&logoColor=white)
![STM32](https://img.shields.io/badge/STM32-03234B?style=flat)
![Arduino](https://img.shields.io/badge/Arduino-00979D?style=flat&logo=arduino&logoColor=white)
![FreeRTOS](https://img.shields.io/badge/FreeRTOS-00979D?style=flat)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Buildroot](https://img.shields.io/badge/Buildroot-000000?style=flat)
![QEMU](https://img.shields.io/badge/QEMU-FF6600?style=flat)
![FPGA](https://img.shields.io/badge/FPGA-7B1FA2?style=flat)
![Raspberry Pi](https://img.shields.io/badge/RaspberryPi-C51A4A?style=flat&logo=raspberry-pi&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![ROS2](https://img.shields.io/badge/ROS2-22314E?style=flat&logo=ros&logoColor=white)
![CMake](https://img.shields.io/badge/CMake-064F8C?style=flat&logo=cmake&logoColor=white)
![GDB](https://img.shields.io/badge/GDB-A42E2B?style=flat)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)

---

# Featured Projects

## 🔐 Secure OTA Platform — Yocto + SWUpdate + U-Boot + Cloud

Production-ready embedded Linux OTA platform for ARM — from secure bootloader to Cloud server, with zero physical intervention and zero brick risk.

**How it works:** The system maintains two firmware copies (Slot A / Slot B). Updates always install on the inactive slot while the device keeps running. If the new firmware fails to boot 3 times, U-Boot automatically rolls back to the previous slot.

- **U-Boot Secure Boot** — RSA 2048-bit key compiled into U-Boot, FIT image signature verified at every boot — unsigned kernel refused
- **Dynamic A/B slot targeting** — `preinst.sh` detects the active slot from FAT and automatically targets the inactive one via `/dev/target_slot` symlink
- **Automatic rollback** — bootcount/bootlimit=3 via U-Boot
- **RSA 2048-bit + SHA256** — every package signed, every artifact hash-verified
- **OTA Agent C++** (init.d daemon, auto-start) — polls Cloud HTTPS every 60s, downloads firmware, triggers SWUpdate automatically — zero human intervention
- **Cloud FastAPI server** (Render, HTTPS) — version read dynamically from `.swu`, API Key auth, **anti-rollback** (refuses to send older version than installed)
- **3 security scenarios validated** — unsigned rejected, corrupted image auto-rollback, valid update installed and stable
- **Remote OTA from smartphone via 4G** — tested end-to-end
- **CI/CD GitHub Actions** passing

> Same A/B OTA architecture used in automotive ECUs (SOTA), industrial IoT and aerospace embedded systems.

🔗 https://github.com/Moez-La/yocto-ota-swupdate-qemu  
📺 Demo local OTA: https://youtu.be/q1bFOdNw2aE  
📺 Demo remote 4G: https://youtu.be/6k4kBoaxgzM  
📺 Demo Secure Boot + Dynamic A/B: https://youtu.be/ruY73xMhIy8

---

## 🔧 Embedded Linux on QEMU ARM
Minimal embedded Linux system from scratch — kernel cross-compilation, Buildroot rootfs, custom kernel driver.
- Write latency: **459 µs avg** | Read latency: **422 µs avg**
- 1 violation / 100 iterations

🔗 https://github.com/Moez-La/Embedded-linux-qemu

---

## 🚁 Quadrotor Control — PID vs SMC vs LQR
Non-linear quadrotor simulation comparing **PID**, **SMC (Super-Twisting)** and **LQR (Riccati)** controllers on direct force/torque dynamics — Raspberry Pi ready (MPU6050 + PCA9685).
- **3 trajectories** — square, circle, figure-8 with RMSE comparison
- **PyBullet NL simulator** — full 12-state non-linear model
- **Hardware-ready HAL** — IMU/ESC abstraction layer for RPi deployment

🔗 https://github.com/Moez-La/quadrotor-control

---

## ⚙️ Custom RTOS vs FreeRTOS
Lightweight RTOS from scratch in C++17 — scheduler, Queue, Mutex, Semaphore.
- Benchmark against **FreeRTOS v11.1.0** on latency and execution frequency

🔗 https://github.com/Moez-La/Rtos-comparison-study

---

## 🤖 Autonomous Mobile Robot (ROS2)
ROS2 Humble robot simulation — URDF, LiDAR, SLAM, teleoperation, Docker deployment.

🔗 https://github.com/Moez-La/Autonomous-mobile-robot-ros2

---

## 🧠 NASA CMAPSS Predictive Maintenance
RUL prediction on turbofan engines — LSTM vs Transformer+Attention (PyTorch).
- Transformer error: **7 cycles** | LSTM error: 17 cycles

🔗 https://github.com/Moez-La/Predictive-maintenance-nasa-cmapss

---

## 🚗 Autonomous Vehicle Lateral Control
Lateral controllers (Proportional, Pure Pursuit) + ECU safety function — EasyMile project.

🔗 https://github.com/Moez-La/Autonomous-vehicle-lateral-control

---

# Current Focus

- ✅ Secure OTA Platform — Yocto + SWUpdate + U-Boot Secure Boot + Cloud — **COMPLETED**
- 🔵 Embedded Linux & Driver Development
- ⚙️ RTOS Internals & Real-Time Systems
- 📡 STM32 & FPGA Low-Level Programming

---

# Certifications

🏅 **Advanced Techniques in Embedded Software Testing** — Coursera / HurixDigital  
🔗 https://www.coursera.org/account/accomplishments/verify/1S6NQBM482A5

🏅 **Introduction to AUTOSAR** — Coursera / EDUCBA  
🔗 https://www.coursera.org/account/accomplishments/verify/58SA5A0TWBCK

---

# Contact

📧 moezchagraoui@gmail.com  
💼 LinkedIn: https://www.linkedin.com/in/moezchagraoui/  
🌍 GitHub: https://github.com/Moez-La
