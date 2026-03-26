# 🫀 Cardiac Cine MRI Phantom with Respiratory Motion Simulation

## 📌 Overview

This project provides a **fully synthetic cardiac cine MRI phantom generator** with optional **respiratory motion simulation and k-space artifact modeling**.

It enables the generation of:

* **Breath-Hold (BH)** clean cine MRI data (ground truth)
* **Free-Breathing (FB)** motion-corrupted cine MRI data

The simulation combines:

* Anatomically inspired **cardiac phantom (LV, RV, myocardium, septum)**
* **Cardiac contraction dynamics**
* **Non-rigid respiratory motion (via deformation fields)**
* **k-space acquisition modeling (line-by-line inconsistency)**

---

## 🎯 Key Features

* 🫀 **Realistic anatomical phantom**

  * Elliptical Left Ventricle (LV)
  * Myocardial wall (thickness preserved)
  * Crescent-shaped Right Ventricle (RV)
  * Septum region

* 🔁 **Cardiac cine simulation**

  * Time-resolved contraction (end-diastole → end-systole)

* 🌬️ **Respiratory motion modeling**

  * Continuous breathing signal
  * Non-rigid deformation using `imregdemons`
  * Motion localized to heart region

* ⚡ **k-space artifact simulation**

  * Line-by-line acquisition
  * Temporal inconsistency → realistic blurring

* 🎛️ **Fully controllable parameters**

  * Motion amplitude
  * Respiration rate
  * Acquisition timing
  * Cardiac dynamics

---

## 🚀 Usage

### 1. Run the script

Simply run:

```matlab
phantom_generator.m
```

---

### 2. Select simulation mode

```matlab
p.enable_respiration = 0;   % Breath-Hold (clean)
p.enable_respiration = 1;   % Free-Breathing (artifact)
```

---

## 📂 Outputs

The script generates:

* **Clean cine (BH)** → ground truth
* **Corrupted cine (FB)** → motion artifacts

These can be used for:

* Algorithm validation
* Motion correction studies
* Deep learning training

---

## ⚙️ Parameter Guide

### 🫁 Respiration Parameters

| Parameter         | Description              | Recommended          |
| ----------------- | ------------------------ | -------------------- |
| `p.resp_rate_Hz`  | Breathing frequency      | 0.18 Hz (~10–12/min) |
| `p.resp_harmonic` | Non-sinusoidal breathing | 0.2 – 0.4            |

---

### ❤️ Cardiac Parameters

| Parameter | Description    | Recommended |
| --------- | -------------- | ----------- |
| `p.HR`    | Heart rate     | 60 bpm      |
| `Nf`      | Cardiac phases | 25–30       |

---

### 🧠 Motion Parameters

| Parameter        | Description              | Recommended |
| ---------------- | ------------------------ | ----------- |
| `p.shift_SI_px`  | Superior-inferior motion | 20–40 px    |
| `p.motion_scale` | Deformation strength     | 1.2 – 2.0   |

---

### ⚡ k-space Parameters

| Parameter    | Description                  | Recommended |
| ------------ | ---------------------------- | ----------- |
| `p.TR_ky_ms` | Time per phase-encoding line | 4–6 ms      |

---

## 🧠 Model Assumptions

* Respiration affects the heart via **non-rigid deformation**
* Motion is applied **before Fourier transform (k-space)**
* Each k-space line is acquired at a **slightly different time**
* Resulting inconsistency produces **realistic MRI blurring**

---

## 🔬 Applications

* Motion artifact simulation
* MRI reconstruction validation
* Deep learning (denoising / motion correction)
* Synthetic dataset generation
* Method development for cardiac MRI

---

## 🧪 Example Modes

### 🟢 Breath-Hold (BH)

* No motion
* Clean cine
* Ground truth reference

### 🔴 Free-Breathing (FB)

* Respiratory deformation
* k-space inconsistency
* Realistic motion artifacts

---

## 🚧 Future Improvements

* 3D short-axis stack simulation
* Slice-dependent anatomy
* Diaphragm-driven motion
* Segmentation mask generation
* Quantitative blur metrics

---

## 📜 License

This project is intended for research and educational purposes.

---

## 🤝 Contributions

Feel free to fork, improve, and contribute to enhance realism or extend functionality.

---

