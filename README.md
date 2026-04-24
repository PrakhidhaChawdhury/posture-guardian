# Posture Guardian

**Status:** 🚀 MVP (Minimum Viable Product)

## Overview
An AI-powered system that uses Pose Estimation to monitor sitting habits during study sessions. Rather than simple posture tracking, this system acts as a **'Focus-Proximity' monitor**, utilizing physical alignment to proxy for cognitive engagement.

## Live Model
You can access and test the trained model here:
👉 **[Posture Guardian Teachable Machine Link](https://teachablemachine.withgoogle.com/models/98LWmWUw9/)**

## How to Use
To get accurate results, the system requires specific physical setup:
1. **Camera Position:** The webcam **must** be placed in a **side-profile** orientation. The model relies on the skeletal alignment (head, shoulder, and hip) visible from the side.
2. **Alignment:** Ensure your torso and head are clearly visible.
3. **Behavioral Logic:** - **'Good Posture'** is detected when you are sitting straight or leaning slightly forward (engaged in writing/studying).
   - **'Bad Posture'** is detected when you lean back into the chair (disengaged/resting).
4. **Environment:** Best used in consistent lighting for the clearest pose tracking.

## Project Journey
I am documenting the complete development cycle, including troubleshooting, model iterations, and the "Focus-Proximity" discovery in the development log.

👉 **[View the full Development Log and Troubleshooting History](./docs/development_log.md)**

## Tech Stack
- **AI Engine:** Google Teachable Machine (Pose Model)
- **Input:** Wireless Webcam via DroidCam
- **Platform:** Web-based browser classification

## Acknowledgements
- **Development Process:** This project is developed by Prakhidha Chawdhury as part of the YIIC internship program.
- **Tools & Support:** I utilized Google Gemini as an AI-collaborator for architectural guidance, debugging, and documentation strategies.
