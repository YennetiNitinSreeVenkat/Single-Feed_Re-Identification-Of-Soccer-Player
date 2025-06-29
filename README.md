# Single-Feed Re-Identification of Soccer Players

This project demonstrates player re-identification in a single video feed using a fine-tuned YOLOv11 object detection model. The goal is to assign consistent IDs to each soccer player, even if they temporarily exit and re-enter the frame. This enables robust tracking for sports analytics applications.

## Objective

Detect and consistently track soccer players in a video, ensuring that players who leave and return to the frame are assigned the same identity.

## Repository Contents

| File / Folder           | Description |
|-------------------------|-------------|
| `Football_REID.ipynb`   | Main Colab-compatible notebook for detection, tracking, and re-identification |
| `15sec_input_720p.mp4`  | Sample input video |
| `results.mp4`           | Output video with visualized player IDs |
| `results.csv`           | CSV log of player IDs and frame-wise positions |
| `README.md`             | Project documentation |
| `football_report.pdf`   | Project summary report |

## Setup Instructions

### Dependencies

Install the required packages using pip:

```
pip install ultralytics opencv-python scipy numpy
# Optional for advanced tracking
pip install deep_sort_realtime
```

How to Run

    Open Football_REID.ipynb in Google Colab.

    Upload the following files:

        15sec_input_720p.mp4

        Your YOLOv11 model (.pt file)

    Install dependencies using the commands above.

    Update file paths in the notebook if needed.

    Run all cells to:

        Load the model

        Process the video

        Detect and track players

        Reassign IDs for players re-entering the frame

        Save the output video and CSV log

Methodology Summary

    Detection: YOLOv11 detects only players in each frame, ignoring other entities such as referees or the ball.

    Tracking and Re-Identification:

        Extract feature vectors using color histograms or similar embeddings

        Use cosine similarity to match current detections with existing player identities

        Reassign previously used IDs if similarity exceeds a threshold

Output Format

    results.mp4: Output video with bounding boxes and consistent player IDs

    results.csv: Frame-wise log in the format:
```
frame_id,player_id,x1,y1,x2,y2
12,3,245,108,287,192
13,3,248,111,290,195
...
```
Notes and Future Work

    Current implementation is basic and works well on short clips

    Planned improvements:

        Use DeepSORT or ByteTrack for better tracking

        Integrate CNN-based embeddings like ResNet or OSNet

        Add temporal smoothing (e.g., Kalman Filter)

        Enable live video processing

        Build an interactive analytics dashboard

        Generate heatmaps and movement trajectories

Contact

Yenneti Nitin Sree Venkat
Email: nithinsreevenkat1009@gmail.com

        
