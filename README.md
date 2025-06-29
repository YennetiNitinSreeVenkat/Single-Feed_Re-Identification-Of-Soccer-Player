# Single-Feed_Re-Identification-Of-Soccer-Player

This project demonstrates **player re-identification** in a single video feed using a fine-tuned YOLOv11 object detection model. The goal is to ensure that each soccer player maintains a **consistent ID**, even after exiting and re-entering the frame.

---

## Objective

> Identify each player and ensure that players who go out of frame and reappear are assigned the **same identity** as before.

---

## Repository Contents

| File / Folder           | Description |
|-------------------------|-------------|
| `Football_REID.ipynb`   | Main Colab-compatible notebook for detection, tracking, and re-identification |
| `15sec_input_720p.mp4`  | Input video used for processing |
| `results.mp4`           | Output video with detected player IDs visualized |
| `results.csv`           | CSV log of detected player IDs and frame-wise positions |
| `README.md`             | Documentation and usage instructions |

---

## Setup Instructions

### Dependencies

Install the following packages (compatible with Google Colab):

```bash
pip install ultralytics opencv-python scipy numpy

Optional for advanced tracking:

pip install deep_sort_realtime

How to Run

    Open Football_REID.ipynb in Google Colab

    Upload Files:

        15sec_input_720p.mp4

        Your YOLOv11 model (.pt)

    Install dependencies using the above pip commands

    Update paths inside the notebook if needed (especially if using Google Drive)

    Run all cells to:

        Load the model

        Process each frame

        Detect players and assign IDs

        Reassign IDs for re-entering players

        Save the output video

    Download results.mp4 and results.csv for evaluation or submission

Methodology Summary

    Detection: YOLOv11 detects players in each frame (ignores ball and referees)

    Tracking + Re-Identification:

        Frame-wise feature vectors are extracted (e.g., simple embeddings)

        Cosine similarity is used to match players across frames

        Previously assigned IDs are reused if similarity exceeds a threshold

Output Format

    results.mp4: Video with bounding boxes and consistent player IDs

    results.csv: Log file with the format:

    frame_id,player_id,x1,y1,x2,y2
    12,3,245,108,287,192
    13,3,248,111,290,195
    ...

Notes

    The current implementation is basic and can be extended with:

        DeepSORT or ByteTrack for stronger tracking

        CNN-based visual embeddings (e.g., ResNet)

        Temporal smoothing for ID assignment

Contact

Yenneti Nitin Sree Venkat
[nithinsreevenkat1009@gmail.com]


---

