---
layout: page
title: Markerless Motion Capture
description: For Gait Recognition
main_title: <h1 align=center>Markerless Motion Capture Based Gait Recognition</h1><hr>
main_description: <h2 align=center>Recognising People by How they Walk, Not How They Look </h2>
img: assets/img/GaitRecognition/joints.png
importance: 3
category: PhD
related_publications: true
---

<style>
h2   {
     color: #429435;
     font-size:180%;
     }
</style>

---


Most biometric systems rely on faces, fingerprints, or iris scans. Even existing gait recognition techniques depend on body shape or silhouette-based features, which can easily be thrown off by clothing, lighting, or camera angle.

I wanted to build something different: a system that looks only at **movement**, not appearance. A way to identify people through their motion, using their walk as a digital signature.

*Based on my paper “Gait Recognition from Markerless 3D Motion Capture” {% cite rainey2019gait %}*

<br>

## Goal
---

The main goal of this project was to create a **movement-only gait recognition system** that uses standard camera footage without relying on depth sensors or marker based cpature for gait recognition.

The approach focuses purely on **body motion**, not shape or looks, which is derived from a standard statisitical body model, with the aim being to work reliably across people and walking conditions.  

The ultimate ambition was to develop a system that performs **competitively** with methods using advanced motion capture systems, without requiring expensive capture equipment.  

<br>
## How It Works
---
Here’s the full pipeline:

1. **2D Pose Detection**  
   I used **DeeperCut**, a convolutional neural network (CNN), to find key joints (hips, knees, ankles, etc.) in each video frame.  

2. **3D Model Fitting**  
   Using **SMPL** (Skinned Multi-Person Linear model) and **SMPLify**, I fit a realistic 3D human body model to those 2D joints, turning regular video into accurate 3D motion data.  

3. **Gait Cycle Extraction**  
   I identified complete walking cycles (roughly 25 frames per cycle) based on stride length and silhouette changes.  

4. **Feature Representation**  
   Each gait cycle becomes a **motion signature**: a flattened vector of joint rotations describing the unique way someone walks.  

5. **Automated Classification**  
   I used **Auto-sklearn**, an AutoML framework, to automatically test, tune, and combine the best machine learning models for classifying these gait signatures.  

<br>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/GaitRecognition/deepercut_joints_cropped.png" title="Joint Extraction" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/GaitRecognition/joints.png" title="Joint Model Fitting" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/GaitRecognition/SMPLify_example_090_cropped.png" title="Image to 3D model" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Joints extracted from an image (left), joints fitted to a synthetic body model (centre) and a model extracted from an image (right).  
</div>

<br>

## Tech Stack
---

A variety of tools were required to make this possible:

<div align=center markdown=1>

| Area | Tools |
|------|-------|
| Pose Estimation | DeeperCut (CNN) |
| 3D Modeling | SMPL & SMPLify |
| Machine Learning | Auto-sklearn |
| Dataset | CASIA-B Gait Dataset (124 subjects, 90° view) |
| Languages | Python, NumPy, scikit-learn |
| Output | ROC, AUC, and rank-based identification metrics |

</div>
<br>

## Challenges & Solutions
---

Throughout the project, numerous challenges emerged but none proved beyond reach. Each obstacle demanded patience, experimentation, and creative thinking, turning setbacks into valuable learning experiences. In the end, every issue found a solution, reinforcing the project’s success and the adaptability of the approach.
<br>

|Challenge | My Approach |
|----------|--------------|
| **Slow fitting with SMPLify** | Optimised frame sampling and processed only gait cycles, not every frame. |
| **Cycle detection** | Used stride length and silhouette changes to detect full gait loops automatically. |
| **Algorithm selection** | Let Auto-sklearn handle model and hyperparameter search with Bayesian optimisation. |
| **Explaining the final results** | Compared against methods using Kinect and marker-based skeleton data to contextualise performance. |

<br>

## Results
---

Even though the model only used 2D video, it performed on par with systems using 3D Kinect depth data or traditional motion capture setups to extract skeleton information, a big win for accessibility and scalability.
<br>

<div align=center markdown=1>

| Metric | Score |
|--------|-------|
| Equal Error Rate (EER) | **18.4%** |
| Area Under ROC Curve (AUC) | **0.90** |
| Mean Average Precision (MAP) | **0.90** |
| Rank-1 Identification Accuracy | **46.7%** |

</div>

<br>

## Why This Matters
---
**Non-intrusive:**
This method operates without requiring the subject’s active participation or awareness. Unlike other biometric systems that need fingerprints, iris scans, or facial alignment, motion-based analysis can identify and track individuals naturally as they go about their activities. This makes it ideal for real-world scenarios where cooperation cannot be expected, such as forensic video analysis.

**Hardware-free:**
It relies solely on standard video cameras or existing footage rather than specialised sensors, wearable devices, or motion-capture suits. This not only reduces cost and complexity but also makes the technology easier to deploy in everyday environments.

**Clothing-robust:**
The system focuses on body movement and dynamics rather than surface appearance. Because it analyses the underlying motion patterns, it remains effective regardless of what the person is wearing, be it casual clothes, uniforms, or loose-fitting garments. This robustness ensures reliable performance even in diverse, uncontrolled settings.

**Scalable:**
The same underlying technology can be extended to multiple fields and at different scales. In surveillance, it can help identify individuals based on gait; in healthcare, it can monitor mobility or detect early signs of disorders; in sports, it can enhance performance analysis; and in animation, it can drive realistic character motion.

Together, these points demonstrate that our movement patterns, *how* we walk and move, are as unique and informative as our facial features. This insight opens up powerful possibilities for recognition, behavioral analysis, and creative applications across a wide range of industries.

<br>
## Key Takeaways
---
**Movement is identity:**
The way we move says more about us than we realise. Our gait carries subtle, deeply personal signatures, tiny variations in stride, rhythm, and posture that make each of us instantly recognisable. Just as a face can tell who we are, so can the way we walk, turn, or gesture. Movement, in this sense, becomes an extension of identity, an invisible fingerprint in motion.

**AutoML saves time:**
Building a great machine learning model used to mean hours or days of trial and error. Now, tools like Auto-sklearn can do the heavy lifting for us. They automatically test algorithms, tune parameters, and find the best combination for the data at hand.

**3D from 2D is possible:**
<!-- Who needs expensive motion-capture suits anymore? -->
Expensive motion capture suits still have a role to play in high precision application. However, today’s computer vision systems can reconstruct surprisingly accurate 3D movement from simple 2D video and it will only get better. Markerless motion capture takes ordinary footage and brings it to life in three dimensions, estimating joint angles, depth, and dynamics with impressive precision. It’s a leap that makes advanced motion analysis accessible to anyone with a camera.

<br>
## Looking Ahead

---
Future directions for this research include:

**Combining shape and motion cues for higher accuracy.**
While gait alone can reveal a lot about a person, combining it with body shape information could make recognition even more reliable. This hybrid approach could significantly boost accuracy, especially in challenging or low-visibility scenarios.This topic is examined in greater detail in our subsequent gait recognition research. <!--, found [here](GaitRecognition2). -->

**Using real-time SMPL models for live gait analysis.**
By integrating the SMPL (Skinned Multi-Person Linear) model with real-time video processing, the system could analyse and visualise gait as it happens. This opens exciting possibilities, from live health monitoring and sports coaching to interactive animation and security applications where immediate feedback matters.

**Further testing under realistic conditions.**
To ensure the system works beyond controlled lab environments, it needs to be tested more extensively in the real world, where people wear different clothes, carry bags, move in crowds, or walk under changing lighting. Evaluating performance under these natural variations will help make the technology more robust, adaptable, and ready for deployment in everyday situations.

**Adding automatic gender estimation for better model fitting.**
Incorporating a gender estimation module could help improve model calibration and body-shape fitting, since male and female body structures differ in proportion and movement dynamics. This doesn’t aim to categorise people socially, but rather to enhance the underlying biomechanical modeling, making gait reconstruction and identity recognition more accurate and anatomically consistent.

<br>

## Reflection
---
This project was a fascinating intersection of biomechanics, computer vision, and machine learning. It taught me how deeply *motion* defines identity, and how technology can uncover those patterns invisibly.

It also reminded me that innovation doesn’t always need more data or sensors, sometimes it just takes a smarter way to look at what we already have.

<br>


