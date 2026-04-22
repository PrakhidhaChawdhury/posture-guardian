# Development Log

## Trial 01: Initial Setup
- **Date:** 2026-04-23
- **Goal:** Get the basic Pose model running with webcam input.
- **Result:** Functional, but the model has a high 'False Positive' rate.
- **Observation:** Bad posture is being triggered even when sitting straight. 
- **Next Step:** Need to add more 'Good Posture' data to balance the model.


## Trial 02: Troubleshooting 'False Positive' Bias
- **Issue:** Model classifies 'Good Posture' as 'Bad Posture'.
- **Root Cause Analysis:** Using Pose Estimation (keypoints), I discovered that the skeletal geometry of 'writing' (Good) is nearly identical to the geometry of 'slouching' (Bad). The model lacks a clear geometric differentiator.
- **Hypothesis:** By including only 'writing' poses, I gave the model a narrow definition of good posture.
- **Iterative Fix:** 1. Augmenting the 'Good' class with a 'Neutral' posture sample (sitting upright without writing) to provide a clear skeletal baseline.
    2. Reviewing the training dataset to ensure 'Good' class contains zero frames of actual slumping, effectively 'cleaning' the data.
