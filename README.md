
***

# Project Summary: Enhanced Document Binarization using Fundamental DIP Techniques

This project's core technical achievement is the custom implementation of a **Digital Image Processing (DIP) pipeline** to restore highly degraded historical manuscripts (DIBCO 2012/2014). We rigorously focus on the mechanics of **Spatial Filtering** and **Adaptive Thresholding**, using an external AI model (RoBIN-UNet) only as a specialized benchmark.

## 1. Objective and Problem Justification

The primary goal is to **produce a machine-readable binary image** by implementing robust, custom-coded DIP algorithms.

| Focus | Rationale for DIP Implementation |
| :--- | :--- |
| **OCR Necessity** | Grayscale degradation prevents accurate **Optical Character Recognition (OCR)**. Binarization is the required step to provide the high-contrast input needed by OCR engines. |
| **Project Focus**| The project emphasizes the **custom implementation** of core image processing algorithms to demonstrate mastery of image transformation principles. |
| **Output Goal**| The output is optimized for **maximal text-background separation** (machine accuracy), showcasing the power of algorithmic control over pixel values. |

---

## 2. Technical Core: Custom DIP Pipeline Implementation

Our main technical contribution is the design and custom implementation of the traditional baseline pipeline to provide two distinct, measurable outputs.

| Pipeline Component | Method Implemented | DIP Justification |
| :--- | :--- | :--- |
| **Spatial Filtering** | **Manual Gaussian Filter** | Custom construction and application of a **convolution kernel** (our **DIP code**) to suppress high-frequency noise and stabilize uneven backgrounds. |
| **Binarization 1 (Global)**| **Manual Otsu Thresholding** | Custom calculation of the image histogram and the **between-class variance** to find the globally optimal threshold. |
| **Binarization 2 (Adaptive)**| **Custom Adaptive Thresholding** | Used to counter **non-uniform illumination** by calculating a localized, self-adjusting threshold for every small region. |
| **Post-Processing** | **Morphological Closing** | Applied to repair character strokes by filling small breaks and holes introduced by the thresholding process. |

---

## 3. Comparative Analysis and Key Findings

We contrast our custom DIP pipelines against the RoBIN-UNet, a pre-trained Deep Learning model, to highlight the limits and strengths of traditional algorithms.

### Successes of the Custom DIP (Our Achievement)

| Success Area | Observation | Technical Proof |
| :--- | :--- | :--- |
| **Noise Mitigation** | The **Manual Gaussian Filter** effectively cleans the background texture and reduces speckle noise, leading to much cleaner thresholding inputs. | Validates the principle of **spatial domain preprocessing** to stabilize data statistics. |
| **Baseline Effectiveness**| Our **Manual Otsu** output is highly effective on well-preserved sections (uniform backgrounds), successfully isolating the foreground text. | Proves competence in **global statistical thresholding** and its inherent limitations. |

### Limitations and Justifying the AI Benchmark

| Failure Mode | DIP Pipeline Performance | Justification for AI |
| :--- | :--- | :--- |
| **Complex Degradation** | Our DIP methods **failed dramatically** on massive, dark stains or severe ink bleed-through (high-intensity noise). The entire stain is incorrectly classified as text. | The **RoBIN-UNet** is necessary as it utilizes complex **contextual features** (learned stroke patterns) that simple pixel-based thresholds cannot access to resolve these failures. |
| **Over-Segmentation**| The DIP output is highly susceptible to **fragmenting very faded text** or creating thick, rough outlines, often requiring sensitive parameter tuning. | This proves the need for an **image-to-image translation** approach (AI) to generate more structurally natural-looking character strokes. |
