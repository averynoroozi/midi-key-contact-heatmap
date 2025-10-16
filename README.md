# 🎹 MIDI-to-Video Conditioning & Verification Pipeline

This repository contains a full pipeline that transforms **MIDI files** and **piano performance videos** into structured **heatmaps** — representing both **key contact activations** and **hand skeleton motion**.  

These multimodal representations are designed as **conditioning inputs for diffusion or generative models**, enabling future systems that can **synthesize realistic concert videos directly from MIDI**, and then **verify their correctness with computer vision**.

---

## 🧭 Project Direction

### 🎯 Goal
To build a **generative AI system** that can:
1. **Generate realistic piano performance videos** (e.g., rendered in Unreal Engine) conditioned on MIDI input.
2. **Use computer vision** to verify that the resulting visual keypresses and hand motions **match the musical content**.

This repository focuses on the **representation learning stage** — producing accurate, aligned, and interpretable **conditioning data** that can drive and evaluate the generative model.

---

## ⚙️ What This Repository Does

### ✅ From MIDI to Heatmaps
- Converts MIDI files into **time-pitch contact maps (piano rolls)**.
- Smooths with Gaussian filters to simulate **pedal sustain and legato**.
- Produces **key contact heatmaps** representing note activations over time.

### ✅ From Video to Skeleton Heatmaps
- Uses **MediaPipe Hands** and **OpenCV** to extract 3D hand landmarks per frame.
- Converts normalized keypoints into **Gaussian hand-skeleton heatmaps**.
- Produces **left- and right-hand activation maps** showing pianist motion.

### ✅ Combined Conditioning Tensor
- Stacks:
  1. MIDI contact map heatmap  
  2. Left-hand skeleton heatmap  
  3. Right-hand skeleton heatmap  
  4. Keyboard template mask  
- This 4-channel tensor can condition a **diffusion model** for video generation or be used for **alignment verification**.

---

## 🧠 Conceptual Pipeline

🎵 MIDI File
   ↓
🎼 Piano Roll Extraction (PrettyMIDI)
   ↓
🔥 Gaussian Contact Heatmaps
   ↓
🎥 Hand Keypoint Extraction (MediaPipe)
   ↓
🖼️ Hand Heatmap + Keyboard Template
   ↓
📊 Control Tensor Construction
   ↓
✅ Verification: MIDI ↔ Video Alignment (Accuracy, Precision, Recall, F1)


---

## 🧰 Installation

```bash
pip install mediapipe opencv-python pretty_midi matplotlib pandas numpy scipy

