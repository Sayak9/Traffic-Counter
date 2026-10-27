# Real-Time Traffic Counter using YOLOv8 & OpenCV

A computer vision pipeline designed to track and count directional human movement (entries vs. exits) across designated boundary zones in real-time video streams.

## Features
- **Object Detection**: Powered by YOLOv8 (`yolov8m`) for person detection.
- **Centroid Tracking**: Custom Euclidean distance tracker for persistent ID assignment without heavy Re-ID overhead.
- **Directional Counting**: Dual polygon Region-of-Interest (ROI) gate testing to distinguish between entering and exiting subjects.
- **Performance Optimization**: Frame subsampling logic to ensure smooth real-time video rendering.

## Tech Stack
- **Python**
- **OpenCV**
- **Ultralytics YOLOv8**
- **Pandas & NumPy**

## How It Works
1. **Detection**: Each processed frame is passed to YOLOv8 to extract bounding boxes for target classes.
2. **ID Tracking**: Centroids are calculated and matched against existing IDs within a spatial distance threshold ($d < 35$ px).
3. **Zone Crossing Validation**: OpenCV's `pointPolygonTest` monitors state transitions across two spatial zones (`Area 1` and `Area 2`) to determine directional movement.

## Quick Start
```bash
# Clone the repository
git clone [https://github.com/Sayak9/Traffic-Counter.git](https://github.com/Sayak9/Traffic-Counter.git)
cd Traffic-Counter

# Install dependencies
pip install opencv-python ultralytics pandas numpy

# Run the counter
python main.py
