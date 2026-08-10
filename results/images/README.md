# Annotated Images

This folder contains the annotated images produced by the YOLO object detection portion of the Auto Scene Assessment Agent.

The agent was tested on 10 images representing different scenes and conditions. YOLO analyzed each image for recognizable objects and produced annotated output images showing the detected objects and their bounding boxes.

These outputs were used along with CLIP scene classifications to support the agent's final rule-based decisions.

Some test images intentionally produced imperfect detections. These results were kept because they demonstrate real-world computer vision limitations and show how the agent handles disagreement or uncertainty between its computer vision tools.
