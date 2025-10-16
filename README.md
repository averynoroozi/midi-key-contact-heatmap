# 🎹 MIDI-to-Video Conditioning & Verification Pipeline

This repository contains a full pipeline that transforms MIDI files and piano performance videos into structured heatmaps — representing both key contact activations and hand skeleton motion. These multimodal representations are designed as conditioning inputs for diffusion or generative models, enabling future systems that can synthesize realistic concert videos directly from MIDI, and then verify their correctness with computer vision. Early stages of a University project.

## ⚙️ Pipeline Overview
From MIDI files, we extract precise note-on/off timing and convert it into a time–pitch piano roll using PrettyMIDI. This is then blurred with Gaussian filters to simulate pedal sustain and legato, resulting in a smooth key-contact heatmap. In parallel, piano performance videos are processed with MediaPipe Hands and OpenCV to extract 3D hand landmarks per frame. These keypoints are converted into Gaussian hand-skeleton heatmaps that show the spatial and temporal motion intensity of the pianist’s hands. Both modalities are aligned over time and combined with a static keyboard template into a single 4-channel tensor: (1) MIDI contact map, (2) left-hand skeleton heatmap, (3) right-hand skeleton heatmap, and (4) keyboard mask. This tensor serves as conditioning input for diffusion-based video generation or as a structured representation for visual verification tasks.

## 🧠 Conceptual Flow
🎵 MIDI File → 🎼 Piano Roll Extraction (PrettyMIDI) → 🔥 Gaussian Contact Heatmaps → 🎥 Hand Keypoint Extraction (MediaPipe) → 🖼️ Hand Skeleton Heatmaps + Keyboard Template → 📊 Control Tensor Construction → ✅ Verification: MIDI ↔ Video Alignment (Accuracy, Precision, Recall, F1)

## 🧰 Installation
```bash
pip install mediapipe opencv-python pretty_midi matplotlib pandas numpy scipy


