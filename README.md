# MacV Object Tracker

A computer vision application for tracking objects in video streams, calculating metrics, and visualizing movement trails. This project was developed as part of the MacV Object Tracker Task.


## Project Overview

This repository implements a complete object tracking solution that:
- Tracks objects in video streams using YOLOv8 and ByteTrack
- Calculates and displays specific tracking metrics
- Visualizes object movements with trails
- Exports processed video viewable in any web browser

The system provides a complete pipeline from detection to visualization, with browser-compatible output for easy sharing and analysis.

## Features

- **Advanced Object Tracking**: Real-time detection and tracking using YOLOv8 and ByteTrack
- **Comprehensive Metrics**:
  - Total time each object spends in the video
  - Total number of unique object IDs detected
  - FPS performance statistics
- **Rich Visualization**:
  - Bounding boxes around detected objects
  - Centroids for precise position tracking
  - Movement trails showing object paths over time
  - Unique ID labels for each tracked object
- **Browser-Compatible Output**: Processed video saved in web-friendly format

## Requirements

- Python 3.8+
- PyTorch
- OpenCV
- Ultralytics (YOLOv8)
- ByteTrack
- NumPy
- Supervision

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yogeshwaran245/Object_tracking.git
   cd Object_tracking
   cd "Object Tracking"
   ```

2. Create a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. Place your input video in the `input/` directory or use the default test video provided.

2. Run the object tracker:
   ```bash
   python object_tracker.py --input input/your_video.mp4 --output output/processed_video.mp4
   ```

3. View the output:
   - Open `output/processed_video.mp4` to see the video with object tracking
   - Check `results.json` for tracking metrics and statistics
   - Open `index.html` in a browser to view the embedded video result

### Command Line Usage

```bash
python track.py --source path/to/video.mp4 --show-trail --save-html
```

### Viewing Results

Open the generated HTML file in any web browser to view the tracking results:

```bash
# On Linux/macOS
open output_viewer.html

# On Windows
start output_viewer.html
```

## Implementation Details

### Tracking Approach

The tracking algorithm follows these steps:
1. Object detection using YOLOv8
2. Object association with ByteTrack
3. Trail generation for each unique object ID
4. Metric calculation (time on screen, unique IDs, etc.)
5. Visualization rendering (boxes, trails, centroids)
6. Output encoding to browser-compatible format

### Metrics Calculation

- **Object Time Tracking**: The system records the first and last frame each object appears in, calculating total time based on video FPS.
- **Unique ID Counting**: A running count of unique object IDs is maintained throughout the video.

### Visualization Features

- **Bounding Boxes**: Colored rectangles around each detected object
- **Centroids**: Center points calculated for each detection
- **Movement Trails**: Historical positions of each object connected by lines
- **ID Labels**: Persistent unique identifiers for each tracked object


## HTML Output

The project generates an HTML file that includes:
- The processed video with tracking visualizations
- A summary of tracking metrics
- Basic playback controls

## Performance Optimization

For better performance:
- Use GPU acceleration if available
- Reduce input frame resolution for faster processing
- Consider using smaller YOLOv8 variants (nano or small)
- Adjust detection confidence threshold based on video quality
  
## Future Improvements

- Implement more advanced tracking algorithms (DeepSORT, ByteTrack)
- Add classification capabilities to identify specific object types
- Enhance the web interface with interactive controls
- Incorporate activity recognition based on tracked movement patterns
- Optimize for real-time performance on edge devices
  
## Contributing

Contributions to this project are welcome! Please feel free to submit a Pull Request.

## Acknowledgments

- [Ultralytics](https://github.com/ultralytics/ultralytics) for YOLOv8
- [ByteTrack](https://github.com/ifzhang/ByteTrack) algorithm
- [Supervision](https://github.com/roboflow/supervision) library for visualization

## Contact

For questions or support, please open an issue on the GitHub repository or contact [yogeshwaran245](https://github.com/yogeshwaran245).
