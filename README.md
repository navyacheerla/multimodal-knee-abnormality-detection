# Multimodal AI for 12 Knee Abnormalities Detection

An end-to-end Multimodal Deep Learning pipeline designed to detect 12 major knee abnormalities by fusing **Magnetic Resonance Imaging (MRI)** scans with **Unstructured Clinical Radiology Reports**.

---

## 📌 Project Overview
Isolated analysis of knee MRI slices often misses subtle ligament tears or micro-fractures without clinical context. This project leverages a **Late Cross-Modal Fusion** approach that aligns visual feature maps with clinical semantic text to improve diagnostic sensitivity across 12 distinct knee pathologies.

### Target Abnormalities (12 Classes)
1. **ACL Tear** (Anterior Cruciate Ligament)
2. **PCL Tear** (Posterior Cruciate Ligament)
3. **MCL Injury** (Medial Collateral Ligament)
4. **LCL Injury** (Lateral Collateral Ligament)
5. **Medial Meniscus Tear**
6. **Lateral Meniscus Tear**
7. **Extensor Mechanism / Tendon Injury**
8. **Medial Compartment Cartilage Defect**
9. **Lateral Compartment Cartilage Defect**
10. **Patellofemoral Cartilage Defect**
11. **Joint Effusion (Fluid Collection)**
12. **Bone Contusion / Marrow Edema**

---

## 🏗️ Architecture Pipeline

* **Vision Backbone:** Pretrained `ResNet-18` fine-tuned to extract structural anatomical representations (128-dim embeddings).
* **Text Backbone:** `Bio_ClinicalBERT` (`emilyalsentzer/Bio_ClinicalBERT`) specialized in clinical medical terminology and entity relations (128-dim embeddings).
* **Multimodal Fusion:** Feature-level late fusion combining visual and textual embeddings into a joint classification layer (256-dim fused vector).
* **Loss Function:** `BCEWithLogitsLoss` optimized for multi-label clinical co-occurrence.

---

## 📊 Live Inference Output Example

```text
==================================================
PATIENT MULTIMODAL DIAGNOSIS REPORT
==================================================
Clinical Note: "Severe ACL fiber tear noted with joint fluid accumulation..."
--------------------------------------------------
Abnormality                  | Probability | Status
--------------------------------------------------
ACL_Tear                     |  89.40%     | POSITIVE (Detected)
Joint_Fluid_Collection       |  76.12%     | POSITIVE (Detected)
Bone_Contusion               |  61.05%     | POSITIVE (Detected)
Medial_Meniscus_Tear         |  14.20%     | Negative
--------------------------------------------------
