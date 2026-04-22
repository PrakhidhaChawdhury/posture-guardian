# Project: Posture Guardian (AI-Based Ergonomics)

## Overview
A real-time posture monitoring system designed to help me maintain correct ergonomics while studying. It uses computer vision to classify my posture state as 'Good', 'Bad', or 'Absent'.

## System Setup
- **Brain:** Teachable Machine (Pose Project)
- **Eyes:** Samsung phone + DroidCam (Wireless Webcam over Wi-Fi)
- **Setup:** Side-profile view of my study desk to capture spinal/head alignment.

## The Process
I’m building this iteratively. I started with a basic idea and learned that:
1. **Camera Angle matters:** Profile view is best for capturing spinal curvature.
2. **Noise matters:** A 'Null' class is essential to stop the AI from guessing when I'm not at the desk.
3. **Data Quality > Quantity:** 5 seconds of high-contrast, 'exaggerated' poses is better than 5 minutes of messy, subtle footage.

## Troubleshooting Log (Current Status)
**Status:** In Development
**Current Issue:** The model shows a "False Positive" bias for 'Bad Posture'. Even when I am sitting upright (Good Posture), the model often defaults to labeling it as 'Bad'.

**Hypothesis:**
- The 'Bad Posture' class might have too much varied data, or my 'Good Posture' recording might be too short/specific to one exact angle.
- Lighting shift: The model might be reacting to shadows created by my desk lamp.

**Planned Next Steps:**
- Re-record the 'Good Posture' class to include more subtle variations of 'upright' (head movement, shifting in seat) to help the model generalize better.
- Review and trim the 'Bad Posture' data to ensure it doesn't contain accidental 'Good' frames.
- Adjust Confidence Thresholds in the final deployment code.
