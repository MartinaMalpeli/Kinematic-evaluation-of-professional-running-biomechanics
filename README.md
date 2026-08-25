# Evaluation of Running Techniques from a Biomechanical Point of View 🏃‍♂️⚙️

![Politecnico di Milano](https://img.shields.io/badge/Politecnico_di_Milano-Biomechanics-blue)
![MATLAB](https://img.shields.io/badge/Made_with-MATLAB-orange)

## 📌 Project Description
This project explores the biomechanical analysis of running performance through the combined use of wearable inertial measurement units (IMU) and surface electromyography (EMG). The main objective is to analyze spatiotemporal, kinematic, symmetry, and neuromuscular parameters to describe individual running patterns, optimize performance, and identify biomechanical features relevant to injury prevention.

## 🎯 Objectives
* **Technique Optimization:** Analysis of performance parameters such as cadence, contact time, step length, vertical oscillation, and trunk inclination.
* **Injury Prevention:** Risk assessment for common running-related injuries (Achilles tendinopathy, iliotibial band syndrome, patellofemoral pain, tibial stress fracture) by analyzing hip and knee adduction/abduction, internal rotation, and contralateral pelvic drop.
* **Symmetry Analysis:** Quantification of kinematic asymmetries (sagittal plane) and muscle activation between the left and right lower limbs during the gait cycle.

## 🛠 Tools and Technologies
* **Kinematics (IMU):** Xsens Awinda (17 wireless sensors at 60 Hz) positioned for full-body tracking.
* **Muscle Activity (EMG):** BTS FREEEMG (8 wireless electrodes at 1000 Hz) for bilateral monitoring of the *Tibialis anterior*, *Gastrocnemius medialis*, *Rectus femoris*, and *Biceps femoris*.
* **Test Environment:** Technogym Skillrun TX500 motorized treadmill.
* **Data Processing:** MATLAB R2026a (Signal processing, filtering, normalization, symmetry index calculation).

## 📊 Experimental Protocol
1. **Preparation:** Acquisition of anthropometric parameters and sensor placement (following the SENIAM protocol for EMGs).
2. **Calibration:** Maximum Voluntary Contraction (MVC) trials for EMG signal normalization, and static/dynamic calibration of the IMUs.
3. **Acquisition:** Running on a treadmill at a controlled speed (3.6 m/s, corresponding to a 4:37 min/km pace).
4. **Synchronization:** Execution of a vertical jump at the end of the trial to generate a common trigger event, identifiable by both the inertial sensors (minimum vertical position of the pelvis prior to take-off) and the electromyographic sensors (peak activation of the gastrocnemius).

## 📁 Repository Structure
```text
├── data/                   # Raw and pre-processed data (omitted for privacy reasons)
│   ├── raw_emg/            # Files exported from BTS EMG-Analyzer
│   └── raw_imu/            # Files exported from Xsens MVN
├── src/                    # MATLAB source code
│   ├── preprocessing/      # Scripts for filtering (Butterworth), linear envelope (6Hz), and normalization
│   ├── sync/               # Script for temporal alignment of EMG-IMU via the jump event
│   └── analysis/           # Extraction of kinematic parameters and Symmetry Index (SI) computation
├── docs/                   # Full reports, presentation slides, and documentation
├── results/                # Generated plots (joint kinematics, muscle activation)
└── README.md               # This file
```

## ⚙️ Data Analysis Pipeline
The MATLAB code in this repository executes the following pipeline:
1. **EMG Pre-processing:** Band-pass filtering (15-450 Hz) to remove artifacts, full-wave rectification (absolute value), low-pass linear envelope filtering (6 Hz), and normalization with respect to the MVC value (or the maximum peak during the running trial).
2. **Synchronization:** Temporal alignment of the EMG (1000 Hz) and IMU (60 Hz) data by applying the time delay calculated during the synchronization jump event.
3. **Gait Cycle Selection:** Isolation of representative gait cycles for each limb (defined from one foot-strike to the subsequent ipsilateral foot-strike) based on the characteristic pattern of the knee flexion-extension angle.
4. **Parameter Calculation:** Extraction of joint angle peaks, spatiotemporal performance indices, and calculation of the Symmetry Index (SI) integral across the main planes of movement.

## 👥 Authors
Project developed as part of the Master of Science degree in Mechanical Engineering at **Politecnico di Milano** (Human Performance Lab).

**Working Group:**
* Lanzoni Giorgio, Malpeli Martina, Setti Viola, Testoni Veronica, Traverso Filippo, Gianatti Luigi, Riva Giulia.

**Advisors:**
* Prof.ssa Manuela Galli
* Ing. Carlalberto Francia

## 📜 License
This project was created for academic purposes.

