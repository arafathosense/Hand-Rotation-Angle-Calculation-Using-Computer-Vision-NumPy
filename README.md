# 🖐️ Hand Rotation Angle Calculation Using Computer Vision NumPy  
Real-Time Computer Vision System for Palm Orientation, Gesture Analytics & Interactive UI Rendering. This project implements a **high-performance real-time hand-tracking system** that calculates **palm rotation angle** using pure NumPy vector math, combined with **MediaPipe** and **OpenCV** for hand detection and visualization.  

It includes a **futuristic HUD (Heads-Up Display)** with animated radial UI, fingertip gears, palm openness metrics, 21-point hand skeleton styling, and a gesture-aware cube/grid visualization. This repository serves as a complete example of integrating **vector geometry**, **signal smoothing filters**, **3D-like visual effects**, and **Computer Vision pipelines** in Python.

# Output
<img width="1365" height="726" alt="image" src="https://github.com/user-attachments/assets/8db8241e-bdf9-42b8-b299-8d6380788cb8" />
<img width="1365" height="727" alt="image" src="https://github.com/user-attachments/assets/4f5ab329-685d-44d2-b5cd-c08aa5b4d285" />
<img width="1365" height="726" alt="image" src="https://github.com/user-attachments/assets/9fafc875-61df-4230-a294-f71d7461f632" />
<img width="1365" height="728" alt="image" src="https://github.com/user-attachments/assets/79cbf1ea-c460-4043-aaa4-0534049f5653" />
<img width="1365" height="725" alt="image" src="https://github.com/user-attachments/assets/af89a2eb-ae21-451a-9295-c7ee8f326b54" />
<img width="1365" height="728" alt="image" src="https://github.com/user-attachments/assets/ae3b2dc6-4d9b-4997-8614-cc51abf9768c" />


# 🔥 Key Highlights

✔ Real-time Hand Tracking (21 Landmarks)  
✔ Palm Rotation Angle (0°–360°) using NumPy  
✔ Openness % based on fingertip–palm distances  
✔ Dynamic Animated Radial UI & Gears  
✔ Exponential Smoothing (No Jittering!)  
✔ Fully Modular Code (Overlay + Utils + Main loop)  
✔ Works Smoothly at 25-40 FPS  


# 🧠 **1. How Palm Rotation Angle is Calculated**

Palm rotation is computed using **vector orientation math**:

- Use **wrist landmark (0)**  
- Use **middle finger MCP (9)**  
- Create a vector:  
  \[
  v = m-w
  \]
- Compute angle using `atan2(y, x)`  
- Normalize to **0°–360°**

### 👉 Formula (NumPy)

```python
def compute_palm_rotation(landmarks):
    w = np.array(landmarks[0][:2])
    m = np.array(landmarks[9][:2])
    v = m-w
    angle = np.degrees(np.arctan2(v[1], v[0]))
    return float(angle % 360)
