# Auto Scene Assessment Agent – System Architecture

## Project Overview

The Auto Scene Assessment Agent is a Tier 2 computer vision system that analyzes images using two pretrained computer vision tools: YOLO and CLIP.

The purpose of the agent is not only to identify what is present in an image, but also to combine information from multiple computer vision models and make a rule-based decision about the scene.

## System Architecture

The system follows a perceive → reason → act workflow.

### 1. Input

The agent receives an image from the test dataset.

Ten images were used to evaluate the completed system. The images represent different environments and visual conditions, including airports, traffic scenes, animals, outdoor markets, landscapes, nighttime scenes, and rainy conditions.

### 2. YOLO Object Detection

YOLO is the first computer vision tool.

YOLO analyzes each image and returns:

- Detected object labels
- Confidence scores
- Bounding boxes
- Total object count
- Inference time

Annotated versions of the images are also saved so the detections can be visually reviewed.

### 3. CLIP Scene Classification

CLIP is the second computer vision tool.

Instead of focusing on individual objects, CLIP compares the entire image against possible scene descriptions.

It returns:

- The most likely scene description
- A confidence score for the selected scene

This gives the agent additional context that may not be available from object detection alone.

### 4. Rule-Based Reasoning

The reasoning layer combines the YOLO detections with the CLIP scene classification.

The agent uses rules and confidence thresholds to decide how the image should be interpreted.

Possible decisions include:

- LOW-ACTIVITY SCENE
- TRAVEL SCENE DETECTED
- VEHICLE AREA DETECTED
- ANIMAL SCENE DETECTED
- CROWDED PUBLIC AREA DETECTED
- TRAFFIC SCENE DETECTED
- POSSIBLE TRAFFIC SCENE - REVIEW
- MODEL DISAGREEMENT - REVIEW
- MANUAL REVIEW RECOMMENDED

The agent does not automatically trust every model prediction. Low-confidence classifications and disagreements between YOLO and CLIP can cause the image to be flagged for human review.

### 5. Output and Trace Logging

The system saves structured outputs for later review.

Outputs include:

- YOLO results
- CLIP results
- Final agent decisions
- Annotated images
- Evaluation metrics
- Individual execution traces

Each trace provides a record of how the agent moved from image input to computer vision analysis and finally to its decision.

## Architecture Flow

Input Image
↓
YOLO Object Detection
↓
Object Labels + Confidence + Bounding Boxes
↓
CLIP Scene Classification
↓
Scene Description + Confidence
↓
Rule-Based Reasoning
↓
Agent Decision
↓
Structured Results + Annotated Image + Trace

## Human-in-the-Loop Design

Human review is an important part of this system.

Computer vision models can produce incorrect or uncertain predictions. Instead of hiding those failures, the agent identifies situations where its tools disagree or confidence is low and recommends manual review.

This design makes the system more transparent and prevents uncertain model predictions from automatically becoming final decisions.

## Tier 2 Design

This project meets the Tier 2 architecture by using a single agent with multiple computer vision tools.

YOLO provides object-level perception while CLIP provides scene-level understanding. Their outputs are combined by a rule-based reasoning system that produces structured decisions and includes error handling and trace logging.
