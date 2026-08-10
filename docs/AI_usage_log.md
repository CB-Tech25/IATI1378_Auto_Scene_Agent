# AI Usage Log

## Project: Auto Scene Assessment Agent
**Course:** ITAI 1378 – Computer Vision  
**Student:** Courtney Bernard

AI tools were used during this project as a learning, troubleshooting, and development assistant. I personally ran the code in Google Colab, reviewed the outputs, selected the test images, tested the completed system, and made decisions about how the final project should be organized and evaluated.

---

## Entry 1 – Project Planning

**AI Tool:** ChatGPT

**How AI Was Used:**  
I used ChatGPT to help break the final project requirements into smaller steps and understand the difference between the available project tiers.

**My Role:**  
I reviewed the project requirements and chose to build a Tier 2 system using multiple computer vision tools instead of using an LLM-based agent.

**What I Learned:**  
I learned that an AI agent does not have to use an LLM. A rule-based system can still operate as an agent when it perceives information, makes decisions, and produces actions or outputs.

---

## Entry 2 – YOLO Implementation

**AI Tool:** ChatGPT

**How AI Was Used:**  
ChatGPT helped me organize and troubleshoot the YOLO object detection portion of the notebook.

**My Role:**  
I ran the model in Google Colab, uploaded the images, reviewed the detections, checked confidence scores, and saved the annotated results.

**What I Learned:**  
YOLO focuses on object-level information. It can identify objects, provide confidence scores, create bounding boxes, and count detections.

---

## Entry 3 – CLIP Implementation

**AI Tool:** ChatGPT

**How AI Was Used:**  
ChatGPT helped me integrate CLIP as the second computer vision tool and organize the scene classification output.

**My Role:**  
I ran CLIP on the same test images and reviewed the scene labels and confidence scores.

**What I Learned:**  
CLIP and YOLO solve different computer vision problems. YOLO identifies individual objects, while CLIP can provide broader information about what type of scene an image represents.

---

## Entry 4 – Debugging YOLO Result Structure

**AI Tool:** ChatGPT

**How AI Was Used:**  
I used ChatGPT to troubleshoot a TypeError that occurred when I tried to combine YOLO and CLIP results.

**Problem:**  
The code treated `yolo_results` like a list even though the saved results were stored as a Python dictionary.

**My Role:**  
I inspected the output type in Colab, shared the actual structure, replaced the incorrect code, and reran the cell.

**What I Learned:**  
Before accessing stored results, I need to understand the data structure. Dictionaries are accessed differently from lists, and checking the type can help locate errors quickly.

---

## Entry 5 – Rule-Based Agent Reasoning

**AI Tool:** ChatGPT

**How AI Was Used:**  
ChatGPT helped me develop and organize rules that combine CLIP scene information with YOLO detections.

**My Role:**  
I tested the rules against the model outputs and reviewed whether the final decisions made sense for each image.

**What I Learned:**  
An agent can use explicit rules and thresholds to make decisions. Combining multiple models can also reveal when the models disagree instead of automatically trusting one prediction.

---

## Entry 6 – Expanding the Test Set

**AI Tool:** ChatGPT

**How AI Was Used:**  
ChatGPT helped me organize the second round of testing after I added five additional images.

**My Role:**  
I selected and uploaded five new images representing additional visual conditions, including traffic, nighttime, outdoor, and rainy scenes. This expanded the evaluation set from 5 images to 10.

**What I Learned:**  
Testing on more varied images exposed weaknesses that were not obvious in the first test set.

---

## Entry 7 – Failure Analysis and Human Review

**AI Tool:** ChatGPT

**How AI Was Used:**  
ChatGPT helped me interpret cases where YOLO and CLIP produced unexpected or conflicting results.

**My Role:**  
I reviewed the actual outputs instead of removing unsuccessful examples. I kept cases such as nighttime cars being detected as wine glasses and scenes where CLIP had low confidence.

**What I Learned:**  
Computer vision models can fail because of lighting, image composition, model limitations, or ambiguity. Human review becomes important when confidence is low or multiple models disagree.

---

## Entry 8 – Error Handling and Evaluation

**AI Tool:** ChatGPT

**How AI Was Used:**  
ChatGPT helped me create an error-handling test and organize evaluation metrics for the completed pipeline.

**My Role:**  
I tested both a valid image path and a missing image path. I also ran the complete system across all 10 test images and reviewed the resulting metrics.

**What I Learned:**  
A system should handle invalid input without crashing. Evaluation should also measure whether the complete pipeline works, not only whether every individual model prediction is correct.

---

## Entry 9 – Trace Logging and Structured Results

**AI Tool:** ChatGPT

**How AI Was Used:**  
ChatGPT helped me organize the structured JSON outputs and individual trace files.

**My Role:**  
I executed the code and verified that a separate trace was created for each of the 10 test images.

**What I Learned:**  
Trace logging makes an AI system easier to understand because I can review how an input moved through perception, reasoning, and the final decision.

---

## Entry 10 – Documentation and GitHub Organization

**AI Tool:** ChatGPT

**How AI Was Used:**  
ChatGPT helped me organize the GitHub repository and draft documentation based on the system I built and tested.

**My Role:**  
I created the repository, uploaded the notebook, sample images, results, annotated outputs, traces, and reviewed the documentation before submission.

**What I Learned:**  
A working model is only one part of a technical project. Reproducibility, documentation, organized outputs, and explaining limitations are also important parts of developing a usable computer vision system.

---

## Final AI Use Statement

AI assistance was used throughout this project for planning, code support, debugging, explanations, and documentation. I did not use AI as a replacement for running or evaluating the project. I executed the system in Google Colab, reviewed the model outputs, selected the test data, identified unexpected results, tested error handling, and verified the final pipeline.

One of the most important things I learned from this project was that model confidence does not always mean the model is correct. Using YOLO and CLIP together made this especially clear because the two tools sometimes interpreted the same image differently. Instead of hiding those disagreements, I used them as part of the agent's reasoning and added human review for uncertain cases.
