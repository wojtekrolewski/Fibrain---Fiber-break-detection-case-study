# Fiber-break-detection-case-study

## 1. Project Context
This project was conducted during an internship in an industrial manufacturing environment and focused on automated analysis of fiber break sources using SEM (Scanning Electron Microscope) images.

Due to confidentiality constraints, proprietary data, images, and source code are not publicly disclosed.
This repository presents the methodology, system design, and engineering decisions behind the solution.

## 2. Problem Definition
Fiber breakage during optical fiber manufacturing may originate from multiple physical mechanisms, each leaving distinct patterns on fracture surfaces visible in SEM images.

Manual inspection:
- is time-consuming,
- requires expert knowledge,
- is difficult to scale.

The objective of the project was to explore whether computer vision and machine learning techniques could:
- automatically detect characteristic fracture patterns,
- classify potential break sources,
- support quantitative analysis by extracting physically meaningful parameters.

## 3. Data Characteristics (Abstracted)
- grayscale SEM images,
- varying magnification levels,
- strong class imbalance (one dominant break type),
- rare and visually similar defect categories,
- presence of unidentified or ambiguous cases.
  
(Exact datasets and images are omitted due to confidentiality.)

## 4. Initial Analysis and Class Definition
Based on domain analysis and image review, multiple fracture-related patterns were initially considered, including:
- mirror region,
- internal defects,
- coating damage,
- rare defects such as wallner lines or non-concentricity.

Due to data imbalance and visual ambiguity, the final solution focused on a reduced set of reliably detectable classes, which significantly improved classification performance.

This design decision reflects a trade-off between model complexity and practical reliability.

## 5. Approach
The developed pipeline consisted of the following stages:

5.1. Image Preprocessing
- normalization and contrast enhancement,
- noise reduction,
- handling variability in SEM magnification.

5.2 Annotation and Training Data Preparation
- manual annotation using tools such as CVAT,
- mask-based labeling for selected defect classes,
- dataset preparation using external annotation pipelines.

5.3 Model Selection
A YOLO-based architecture (YOLOv8) was selected due to:
- efficient inference,
- ability to detect multiple structures in a single image,
- support for segmentation masks,
- relatively low hardware requirements.

5.4 Model Training and Evaluation
- local model training on annotated datasets,
- iterative refinement of class definitions,
- qualitative and quantitative evaluation of detection accuracy.
