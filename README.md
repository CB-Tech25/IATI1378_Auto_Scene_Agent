# Auto Scene Assessment Agent

## ITAI 1378 – Computer Vision Final Project
**Student:** Courtney Bernard  
**Project Tier:** Tier 2 – Multiple Computer Vision Tools

## Project Overview

The Auto Scene Assessment Agent is a computer vision system that analyzes images using two pretrained models: YOLO and CLIP.

Instead of depending on only one model, the agent combines object detection from YOLO with scene-level understanding from CLIP. A rule-based reasoning layer then compares the results and makes a final decision about the image.

The system can also recognize uncertainty. When model confidence is low or YOLO and CLIP disagree, the agent can recommend human review instead of automatically trusting an unreliable prediction.

## System Workflow

The project follows a perceive → reason → act workflow:

1. An image is provided to the system.
2. YOLO detects objects in the image.
3. CLIP analyzes the overall scene.
4. The agent compares both model outputs.
5. Rule-based logic determines the final decision.
6. Results, annotated images, metrics, and execution traces are saved.

## Computer Vision Tools

### YOLO – Object Detection

YOLO provides object-level perception.

For each image, the system records:

- Object labels
- Detection confidence
- Bounding boxes
- Number of detected objects
- Inference time

The system also saves an annotated copy of each image showing YOLO detections.

### CLIP – Scene Understanding

CLIP provides broader scene-level information.

The image is compared against possible scene descriptions, and the system records:

- Selected scene description
- Scene confidence score

Using CLIP with YOLO allows the agent to compare scene context with individual object detections.

## Agent Reasoning

The project uses a rule-based agent rather than an LLM.

The reasoning layer evaluates:

- CLIP scene classification
- CLIP confidence
- YOLO object detections
- Agreement between the two computer vision tools

Examples of agent decisions include:

- LOW-ACTIVITY SCENE
- TRAVEL SCENE DETECTED
- VEHICLE AREA DETECTED
- ANIMAL SCENE DETECTED
- CROWDED PUBLIC AREA DETECTED
- TRAFFIC SCENE DETECTED
- POSSIBLE TRAFFIC SCENE - REVIEW
- MODEL DISAGREEMENT - REVIEW
- MANUAL REVIEW RECOMMENDED

Low-confidence or conflicting results can be sent for human review.

## Test Dataset

The completed system was evaluated using 10 test images representing different scenes and visual conditions.

The test set included:

- Sunset landscape
- Airport
- Parking lot
- Dogs
- Morocco outdoor market
- Road/vehicle scene
- Downtown scene
- Cars at night
- Outdoor scene
- Rainy scene

The test images are available in:

`data/sample/`

## Evaluation Results

The final evaluation produced:

- **Total test images:** 10
- **Successful end-to-end runs:** 10
- **Pipeline completion rate:** 100%
- **Cases flagged for review:** 4
- **Review rate:** 40%
- **Average YOLO inference time:** 0.212 seconds

The 40% review rate does not mean that the pipeline failed. These cases demonstrate the agent's ability to recognize uncertainty, low confidence, or disagreement between computer vision tools.

## Example Failure Cases

Testing revealed several useful limitations.

### Cars at Night

CLIP identified the image as a road or traffic scene with 81.6% confidence, while YOLO incorrectly detected two wine glasses.

The agent recognized that the scene classification and object detections did not support each other and returned:

`POSSIBLE TRAFFIC SCENE - REVIEW`

### Outdoor Scene

For `beautiful.jpg`, CLIP classified the image as a dog scene with 77.0% confidence, but YOLO detected a bench and a potted plant instead of a dog.

The agent returned:

`MODEL DISAGREEMENT - REVIEW`

### Low-Confidence Scenes

The downtown and rain images produced lower CLIP confidence and were sent to manual review instead of being automatically accepted.

These examples demonstrate why human-in-the-loop review can be important in real-world computer vision systems.

## Error Handling

The system includes basic error handling for image inputs.

A valid image returns a success status and continues through the pipeline.

A missing image returns a structured error message instead of causing the complete system to crash.

## Repository Structure

```text
IATI1378_Auto_Scene_Agent/
├── README.md
├── requirements.txt
├── notebooks/
│   └── FinalProject_CourtneyBernard_ITAI1378.ipynb
├── data/
│   └── sample/
├── results/
│   ├── images/
│   ├── traces/
│   ├── agent_results.json
│   ├── clip_results.json
│   ├── metrics.txt
│   └── yolo_results.json
└── docs/
    ├── architecture.md
    ├── AI_usage_log.md
    └── presentation.pdf
