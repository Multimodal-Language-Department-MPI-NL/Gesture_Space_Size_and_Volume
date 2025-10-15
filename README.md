# Gesture_Space_Size_and_Volume

> Attribution: Use the script prepared for the focus group session. Attribute to this Envision Box module: [Module](https://www.envisionbox.org/embedded_MergingMultimodal_inPython.html)

Quantitative measures for gesture space analysis using MediaPipe keypoints, including vertical amplitude, McNeillian space classification, and volumetric space calculations.

## 🔬 Research Context

This module shows how to calculate maximum vertical amplitude (i.e., gesture height), characterize the location of gestures based on McNeillian space (McNeill, 1992), and calculate the 2D size or 3D volume of gesture (or sign) space. 

## 🎯 What This Project Does

1. **Vertical Amplitude Analysis**: Calculate maximum hand height relative to body landmarks
2. **McNeillian Space Classification**: Map hand positions to gesture space zones (center, periphery, extra-periphery)
3. **Volumetric Space Calculation**: Measure the 3D space volume utilized by gestures
4. **Multi-file Processing**: Batch analysis across multiple participants and gesture segments

## 📊 Analysis Process

1. **Load Data**: Import MediaPipe keypoint time series
2. **Convert Format**: Transform MediaPipe landmarks to OpenPose-like structure
3. **Calculate Vertical Amplitude**: Determine hand height relative to body reference points
4. **Map McNeillian Space**: Classify hand positions into gesture space zones
5. **Compute Volumetric Space**: Calculate 3D volume/2D area utilized by gestures

## 🔧 Methods

### Vertical Amplitude
- **Body-relative scaling**: Height measured relative to body landmarks (midline, shoulders, face)
- **6-level classification**: 0=below midline, 1=midline to middle-upper body, 2=above middle-upper body, 3=between shoulders and face middle, 4=between face middle and head top, 5=above head
- **Hand selection**: Support for single hand (L/R) or both hands (B)

### McNeillian Space
- **Grid definition**: Dynamic grid based on body landmarks (hips, shoulders, eyes)
- **Zone classification**: Center-center, Center, Periphery, Extra-periphery
- **Subsection mapping**: 8 directional subsections for periphery zones
- **Metrics**: Space usage count, maximum peripheral space, modal space usage

### Volumetric Space
- **3D volume calculation**: X, Y, Z axis ranges for 3D data
- **2D area calculation**: X, Y axis ranges for 2D data
- **Dynamic expansion**: Bounding box grows with gesture movement
- **Hand-specific analysis**: Individual or combined hand volumes

## 📁 Project Structure

```
Macneillian_Space_and_2D_Size/
├── README.md
├── environment.yml
├── notebooks/
│   └── 01-analysis_kinematic_features_module.ipynb
├── data/
│   ├── processed/                     # MediaPipe keypoint CSVs
│   └── raw/                          # Raw input files
├── gesture_space.jpg                 # McNeillian space diagram
└── results/
    └── space_results.xlsx           # Analysis outputs
```

## 🚀 Quick Start

### Prerequisites

```bash
conda env create -f environment.yml
conda activate macneillian
```

### Run the Interactive Notebook

```bash
jupyter lab
# Open notebooks/01-analysis_kinematic_features_module.ipynb
```


## 📈 Data Format

### Input
- **MediaPipe CSVs**: Time series with keypoint coordinates (X, Y, Z) and timestamps
- **ELAN files**: Optional annotation files for gesture segmentation

### Output
- **Excel files**: Per-gesture metrics including space usage, volumes, and classifications
- **Analysis results**: Vertical amplitude, McNeillian space metrics, volumetric measures

## 🎛️ Configuration

### Analysis Parameters
- **Hand selection**: 'L' (left), 'R' (right), or 'B' (both)
- **Data dimensionality**: 2D or 3D analysis
- **Gesture segmentation**: Optional ELAN annotation integration

### McNeillian Space Parameters
- **Grid scaling**: Based on body width and face measurements
- **Zone boundaries**: Dynamic calculation from body landmarks
- **Subsection mapping**: 8-directional classification system

## 🔗 Related Projects

- [Extracting MediaPipe keypoints](https://github.com/Multimodal-Language-Department-MPI-NL/MediaPipe_keypoints_extraction): Extract pose landmarks from video with MediaPipe.
- [Smoothing](https://github.com/Multimodal-Language-Department-MPI-NL/Smoothing): Smooth noise and interpolate missing points.
- [Normalization](https://github.com/Multimodal-Language-Department-MPI-NL/Normalization): Normalize position and scale across files.
- [Speed, Acceleration, and Jerk](https://github.com/Multimodal-Language-Department-MPI-NL/Speed_Acceleration_Jerk): Compute speed, acceleration, and jerk over time.
- [Merging ELAN and MediaPipe](https://github.com/Multimodal-Language-Department-MPI-NL/Merging_Motion_ELAN): Align motion data with ELAN annotations.

## 📖 References

- McNeill, D. (1992). *Hand and Mind: What Gestures Reveal About Thought*
- Pouw, W. (2023). Analysis kinematic features module. [https://envisionbox.org/embedded_Analysis_kinematic_features_module.html](https://envisionbox.org/embedded_Analysis_kinematic_features_module.html)

## 🤝 Contributing

This project is part of the MPI Multimodal Interaction Research framework. For questions or contributions, please refer to the main project documentation.

## 📄 License

This project is part of the MPI research framework. Please refer to the main project license for usage terms.
