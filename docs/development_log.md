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


## Retrospective: The Writing Paradox
- **Finding:** Through testing, I identified that the act of writing requires a natural forward lean that is geometrically similar to poor posture. 
- **Critical Realization:** Attempting to force an AI to distinguish between 'Natural Forward Lean' and 'Slouching' using basic pose estimation creates a conflict of definitions.
- **Project Pivot:** 1. I will redefine the 'Bad Posture' class to look specifically for 'Spinal Collapse' (shoulders caving inward and head dropping below a threshold) rather than simple 'forward leaning'. 
    2. I am officially documenting this as a 'System Limitation'. The model is designed to detect *extreme* slouching, not micro-ergonomic adjustments during active writing.


## Trial 03: The 'Less is More' Breakthrough
- **Result:** High accuracy achieved.
- **Discovery:** I simplified the training dataset to only two core classes: 'Good' (Upright) and 'Bad' (Collapsed).
- **Analysis:** By removing 'null' classes and minimizing data complexity, the model's 'Signal-to-Noise' ratio improved drastically. The AI no longer experiences 'feature overlap' because the boundary between classes is now unambiguous.
- **Key Learning:** Simplicity often outperforms complexity in early-stage ML development.


## System Behavior: The Focus Proxy
- **Observation:** The model effectively discriminates between 'Engaged' (Straight/Forward leaning) and 'Disengaged/Relaxed' (Leaning back) states.
- **Analysis:** Rather than strictly enforcing a perfect 90-degree spinal angle (which is physically uncomfortable and unnatural for long periods), the model acts as a proxy for attention.
- **Conclusion:** By using 'Leaning Back' as the indicator for 'Bad Posture', the system successfully flags moments of low-focus/rest rather than minor postural variations.
