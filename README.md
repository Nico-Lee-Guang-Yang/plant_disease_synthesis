# plant_disease_synthesis
FYP: Plant Disease Synthesis using Enhanced CycleGAN with Sobel filtering and Contour Loss. Generates synthetic diseased leaf images for data augmentation — evaluated on Tomato, Bell Pepper, and Peach (PlantVillage dataset).

Deep learning-based plant disease recognition requires large, diverse datasets. This project addresses the lack of real diseased leaf images by using an enhanced CycleGAN with Sobel filtering and Contour Loss to generate synthetic diseased leaf images from healthy ones.

    Key Features
    - Two enhanced CycleGAN variants:
      - Model 1 (Dual Sobel): Sobel filter on both input and output
      - Model 2 (Threshold + Sobel → Sobel): Threshold preprocessing + Sobel on input, Sobel on output
    - Contour Loss for leaf shape preservation
    - Trained on PlantVillage dataset (Tomato, Bell Pepper, Peach — bacterial spot)
    - Evaluated with FID, KID, and classification accuracy (MobileNetV2 & ViT)

    Results

    | Model | FID ↓ | KID ↓ |
    |-------|-------|-------|
    | Baseline CycleGAN | 33.32 | 0.67 |
    | Model 1 (Dual Sobel) | 41.16 | 0.67 |
    | Model 2 (Thresh+Sobel) | 37.95 | 0.68 |
    
    | Dataset Type | ViT Accuracy | MobileNetV2 Accuracy |
    |-------------|-------------|---------------------|
    | All Real | 98.08% | 72.25% |
    | Real + Synthetic (Model 2) | 95.09% | 77.50% |
    | All Synthetic (Model 2) | 95.54% | 61.25% |


Key finding: Structure-preserving preprocessing (threshold + Sobel) improves synthetic realism and boosts lightweight classifier performance in mixed real+synthetic settings.

    Files
    - 1211201869_LohYuenPeng_poster.pdf — Project poster
    - 1211201869_LohYuenPeng_Report.pdf — Full report
    - 1211201869_LohYuenPeng_Research-paper.pdf — Research paper

    Tech Stack

    - Framework: PyTorch, CycleGAN
    - Preprocessing: Sobel edge detection, adaptive thresholding
    - Evaluation: FID, KID, MobileNetV2, Vision Transformer (ViT)
    - Dataset: PlantVillage
