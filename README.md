# Deep-Conv-GAN-For-Chest-X-Ray-Image
1. Introduction

Medical imaging datasets, particularly chest X-rays, are challenging for deep learning because of:

Highly limited labelled datasets

Restricted patient diversity

Class imbalance

Ethical constraints on acquiring new clinical data

Difficulty obtaining rare cases

GANs provide a strong mechanism for generating synthetic radiological data that preserves anatomical patterns while preventing patient identity leakage.

This research investigates three stages:

1. Baseline Generative Model — DCGAN

Used as the initial attempt to generate synthetic CXRs, identifying challenges and limitations.

2. Advanced GAN — StyleGAN2-ADA

Trained using adaptive discriminator augmentation to stabilize GAN training on small medical datasets.

3. Classification Model — ResNet50

Used to test whether synthetic GAN images improve classification performance.

This sequential approach enabled deep analysis of the strengths, weaknesses, and suitability of GANs for medical imaging synthesis.

2. Dataset
Dataset Characteristics

Type: Chest X-Ray (Normal class only)

Total Images: 1,341

Resolution: Resized to 256 × 256

Color channels: Grayscale (converted to RGB for GAN pipelines)

Preprocessing:

Histogram normalization

Pixel scaling to [-1, 1]

Resizing using bilinear interpolation

Train/test split where needed

Small dataset size made this an ideal test case for StyleGAN2-ADA.

3. DCGAN Implementation

DCGAN was the first model trained to establish a baseline.

3.1 DCGAN Architecture

Key architectural details

Generator:

Transposed convolutions

Batch normalization

ReLU activation

Output: 64×64 image

Discriminator:

Convolutional layers

LeakyReLU activation

Sigmoid output

Training Setup

Epochs: 200

Batch size: 64

Optimizer: Adam (lr=0.0002)

Loss: Binary Cross-Entropy

3.2 DCGAN Results
Observations

Generated images had:

Severe noise

Missing anatomical structure

Blurred boundaries

Mode collapse after 80–120 epochs

Artifacts along edges

Unrealistic ribcage patterns

( Images: Sample DCGAN Generated CXRs at Different Epoch)

Why DCGAN Failed:

DCGAN struggles with high structural complexity like medical images.

No adaptive data augmentation.

Limited dataset size → discriminator overpowered generator.

Training became unstable beyond 80–100 epochs.

Conclusion for DCGAN

DCGAN was not suitable for generating medically realistic CXRs.
It established the need for more advanced architectures.
