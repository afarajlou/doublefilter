# 🤖 PYNQ-Z2 Machine Vision Robot
*Hardware/Software Co-Design for Real-Time Image Filtering and Motor Control*

---

## 🚀 Setup (when hardware available)

```bash
sudo apt-get update
sudo apt-get install -y libopencv-*
sudo pip3 install --upgrade pip cython
sudo pip3 install -r requirements.txt
```

---

## ▶️ Usage

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/PYNQ-Robot-Vision.git
   cd PYNQ-Robot-Vision
   ```

2. **Launch Jupyter Notebook on the board**
   ```bash
   jupyter notebook --no-browser --ip=0.0.0.0
   ```
   Open the provided URL in your browser.

3. **Run the notebooks**
   - `notebooks/DoubleHWSW.ipynb` → compare software and hardware filtering pipelines  
   - `notebooks/MotorDriver.ipynb` → demonstrate motor PWM and direction control  

---

## 📊 Experimental Results

| Experiment                     | Software FPS | Hardware FPS | Speed-up |
|:------------------------------ |:------------:|:------------:|:--------:|
| Single Filter (Sobel)          | 7.4          | 50.0         | 6.7×     |
| Two Filters (Sobel → Dilate)   | 9.3          | 48.9         | 5.2×     |
| Motion Detection (Partial HW)  | 4.4          | 12.8         | 2.9×     |

---

## 🛞 Motor Control Summary

MicroBlaze firmware functions:

```c
void init_ardumoto();
void set_direction(int motor, int dir);
void set_speed(int motor, int speed);
void run();
void stop();
```

Each motor supports independent PWM duty cycle and direction control.

---

## 👩‍💻 Authors

- **Fatemeh Farajlou**  
- **Seyed Hossein Malekouti**

