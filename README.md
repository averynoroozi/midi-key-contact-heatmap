# MIDI Visualization Prototype

## Overview
This project preprocesses MIDI files to generate Gaussian heatmaps representing note intensity over time. It is an early-stage university project aiming to transform MIDI data into animated visualizations of piano performances.

## Features
- Converts MIDI files to piano roll matrices  
- Generates Gaussian heatmaps to visualize note activity  
- Provides static visualizations of time vs. pitch intensity  

## Skills Demonstrated
- Python programming and data manipulation (`NumPy`, `pretty_midi`)  
- Time-series visualization (`Matplotlib`)  
- Understanding of MIDI file structure and piano roll representation  

## Future Work
- Batch processing of multiple MIDI files  
- Animated performance video generation  
- Interactive web-based visualizations  
- Predictive modeling or style analysis  

## Usage
1. Install dependencies:
```bash
pip install numpy matplotlib pretty_midi

from task_a import midi_to_pianoroll, piano_roll_to_heatmap

pianoroll = midi_to_pianoroll('path_to_your_midi_file.mid')
heatmap = piano_roll_to_heatmap(pianoroll)
