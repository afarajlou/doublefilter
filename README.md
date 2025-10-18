# 🤖 PYNQ-Z2 Machine Vision Robot  
*Hardware/Software Co-Design for Real-Time Image Filtering and Motor Control*

---

## 🧩 Project Overview

This repository documents a **machine-vision system implemented on the PYNQ-Z2 board (Zynq-7000 SoC)**.  
The project combines **real-time image processing** and **motor control** using a hybrid **software–hardware** approach.

It demonstrates:
- Acceleration of OpenCV filters using **FPGA overlays** from the `pynq-computer-vision` package  
- Comparison between **software and hardware** execution pipelines  
- Integration of a **MicroBlaze motor controller** for direction and speed control  

This work was completed as a course project at **Amirkabir University of Technology**, supervised by **Dr. Morteza Saheb Zamani**.

---

## ⚙️ System Architecture

**Hardware Platform:** PYNQ-Z2 (Zynq-7000 SoC)  
**Operating System:** PYNQ Linux Image v2.6  
**Languages:** Python 3.6 / C (MicroBlaze firmware)  
**Video Path:** Raspberry Pi → HDMI Input → PYNQ → HDMI Output → Display  

### Functional Blocks
1. **Video I/O** – Captures and displays 720 p grayscale frames through HDMI.  
2. **Image Processing** – Applies filtering (Sobel, Dilate) and motion-detection pipelines.  
3. **Hardware Acceleration** – Offloads key kernels to FPGA overlays (`xv2Filter2DDilate`).  
4. **Motor Control** – Uses a MicroBlaze soft-core to generate PWM and set direction pins.

---

## 📦 Repository Contents

| Folder | Description |
|:--------|:-------------|
| `notebooks/` | Jupyter notebooks for HW/SW comparison and motor control |
| `notebooks/DoubleHWSW.ipynb` | Two-filter pipeline demo (software vs hardware acceleration) |
| `notebooks/MotorDriver.ipynb` | Motor-control demo using MicroBlaze firmware |
| `requirements.txt` | Python dependencies (for PYNQ v2.6) |
| `LICENSE` | MIT license |
| *(optional)* `assets/` | Images, diagrams, or demo GIFs |

---

## 🧰 Dependencies

Add these lines to your **`requirements.txt`**:

```text
numpy
opencv-python
pynq==2.6.*
git+https://github.com/Xilinx/PYNQ-ComputerVision.git

##🚀 Setup (when hardware available)
sudo apt-get update
sudo apt-get install -y libopencv-*
sudo pip3 install --upgrade pip cython
sudo pip3 install -r requirements.txt

##▶️ Usage
1.Clone the repository:
git clone https://github.com/<your-username>/PYNQ-Robot-Vision.git
cd PYNQ-Robot-Vision


2.Launch Jupyter Notebook on the board:
jupyter notebook --no-browser --ip=0.0.0.0

Open the provided URL in your browser.

3.Run the notebooks
DoubleHWSW.ipynb → compare software and hardware filtering pipelines
MotorDriver.ipynb → demonstrate motor PWM and direction control

##📊 Experimental Results
Experiment	                  Software FPS	       Hardware FPS	        Speed-up
Single Filter (Sobel)	          7.4	                50.0	                6.7 ×
Two Filters (Sobel → Dilate)	  9.3	                48.9	                5.2 ×
Motion Detection Partial HW	    4.4	                12.8	                2.9 ×

##🛞 Motor Control Summary
MicroBlaze firmware functions:

void init_ardumoto();
void set_direction(int motor, int dir);
void set_speed(int motor, int speed);
void run();
void stop();
Each motor supports independent PWM duty cycle and direction control.


##👩‍💻 Authors

Fatemeh Farajlou 
Seyed Hossein Malekouti 
