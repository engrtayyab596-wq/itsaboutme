[Tayyab *Hassan*](#top)

[About](#about) [Projects](#projects) [Experience](#experience) [Education](#education) [Skills](#stack) [Contact](#contact)

Deep learning / computer vision / generative AI / embedded AI

# Muhammad Tayyab *Hassan*

Master's student in Biometrics and Intelligent Vision at Université Paris-Est Créteil, building and evaluating deep learning, computer vision and generative AI systems end to end — from model training to production-style deployment. Two years of industry hardware design experience, now aimed at Edge AI.

Open to a 6-month internship from February 2027, in ML, DL, computer vision or embedded AI.

[Email me](mailto:engrtayyab596@gmail.com) [LinkedIn](https://www.linkedin.com/in/muhammad-tayyab-hassan-4b565b230) [GitHub](https://github.com/engrtayyab596-wq)

![Portrait of Muhammad Tayyab Hassan](/_blob/e59aef00a67172a82825ddaef56fa44c)

Île-de-France, FranceOpen to M2 opportunities

**15**end-to-end AI & CV systems, model to deployment

**2 yrs**industry hardware design, Teresol Pvt. Ltd.

**2**languages — English (fluent), French (A2)

## About

I spent two years as a hardware design engineer at Teresol Pvt. Ltd., designing multi-layer, high-speed PCBs around processors like the NVIDIA Jetson Tegra TK1, writing embedded C/C++ for real-time control boards, and verifying power and signal integrity before boards went to production. Before that, I designed the motor drive and battery management system for Pakistan's first mini electric tractor as my final-year project.

I'm now in the second year of a Master's in Biometrics and Intelligent Vision at UPEC, where I build deep learning, computer vision and generative AI systems — not just notebooks, but models wrapped in FastAPI, containerised with Docker, tested with pytest and shipped through CI/CD. I work across medical imaging, real-time detection and tracking, generative modelling, classical statistical ML, and reinforcement learning, and my own Edge-AI board design is where that work meets the hardware background I started with.

I'm looking for a 6-month M2 internship from February 2027, anywhere in artificial intelligence, machine learning, deep learning, computer vision, or embedded AI — the field I'd choose first, because it needs both halves of what I know.

Based in

Île-de-France, France

Languages

English (fluent), French (A2)

Interests

Embedded AI, computer vision, generative AI, biometrics, power electronics

Selected work / 2025-2026

## Projects

Fifteen systems spanning medical imaging, real-time vision, generative AI and embedded hardware. Five below in full; the rest are one click away.

- 01 / Medical image segmentation

  PyTorchU-NetFastAPIDocker

  ### Brain tumour segmentation

  A U-Net trained from scratch to turn an MRI slice into a pixel-level tumour mask, not just a yes/no label.

  **0.86**Dice score

  **0.76**IoU

  **31M**parameters

  **26**pytest tests

  Approach

  Built a U-Net (encoder/decoder with skip connections) from scratch in PyTorch, trained on 3,929 slice/mask pairs from the LGG MRI dataset. Only 33% of slices contain tumour, so cross-entropy would let the model learn to predict "healthy" everywhere and still score 96.7% accuracy — I trained with Dice loss instead, which optimises the overlap between predicted and true masks directly and ignores the background. An Albumentations pipeline (flips, rotation, elastic transform) simulated natural tissue variation between patients.

  Result

  Best validation Dice of 0.8586 at epoch 45, with almost no gap between train and validation despite 31M parameters on under 4,000 images — the augmentation held. I then tested it on an external dataset using a different MRI sequence it had never seen in training, and it still localised the tumour correctly, which is the real test of whether a medical model generalises rather than memorises.

  Deployed — FastAPI · Docker · pytest[View repository →](https://github.com/engrtayyab596-wq/brain-tumour-segmentation)
- 02 / M2 research, generative AI

  DDPMEEGNetReactFastAPI

  ### Synthetic EEG generation — NeuroSynth

  My Master's research project, targeting BioSMART 2026: generating synthetic EEG to augment small, expensive-to-collect brain-signal datasets.

  **0.98+**PSD-Pearson fidelity

  **87.2%**best CNN accuracy

  **6**brain-state classes

  **4**evaluation protocols

  Approach

  Compared three generation methods — LLM-guided Fourier synthesis, a baseline DDPM, and MSC+DFSI, a larger diffusion model I proposed and trained for 1,000 epochs — then evaluated the synthetic signals two ways: how well a CNN and an EEGNet classifier could tell brain states apart on them, and how closely their power-spectral density matched real EEG.

  Result

  MSC+DFSI reached PSD-Pearson correlations above 0.98 against real EEG across all six classes and a best CNN accuracy of 87.2%, close to the 88.4% real-data-only baseline. I built the full evaluation stack myself — a FastAPI backend and React/Vite frontend with Generate, Visualize, Statistics and Results tabs — and defended the work in a 12-slide jury presentation.

  Scientific article in progress[Ask about this research →](#contact)
- 03 / Real-time computer vision

  YOLOv8ByteTrackOpenCVDocker

  ### Real-time traffic monitoring

  Turns raw traffic-camera video into vehicle counts, speeds and congestion hotspots, served over a REST API.

  **+38%**mAP50 after fine-tuning

  **140k**fine-tuning frames

  **25-30**FPS on GPU

  Approach

  YOLOv8s detects vehicles across 5 classes; ByteTrack keeps a consistent ID on each one across frames, though it drops the class label once tracking starts, so I added a custom IoU-based class-memory fix. Virtual line-crossing counts vehicles per lane, pixel-to-real-world calibration estimates speed in km/h, and a decaying heatmap shows where traffic builds up.

  Result

  COCO weights are trained on eye-level photos, not elevated traffic-camera angles, so I fine-tuned on 140k frames from UA-DETRAC and watched mAP50 go from 0.52 to 0.717 in 3 epochs — a measured case for why domain adaptation matters before a vision model goes into production, not just a claim about it.

  FastAPI · Docker · GitHub Actions CI/CD[Ask for access →](#contact)
- 04 / Embedded AI hardware

  AltiumVivadoHyperLynx

  ### Edge-AI single board computer

  A from-scratch board built to run AI workloads at the edge, where the model has to share silicon with real hardware constraints.

  **16-core**NXP LX2160A SoC

  **DDR4-3200**ECC memory

  **PCIe Gen4**+ 25G SFP28

  Approach

  I'm independently architecting SBC v1.1 around an NXP LX2160A (16-core ARM Cortex-A72) paired with a Xilinx Kintex UltraScale+ FPGA, for real-time, on-device inference. The design scope covers DDR4-3200 ECC memory, PCIe Gen4 / 25G SFP28 connectivity and a multi-rail power architecture, using Altium Designer for schematic and layout, Vivado for the FPGA side, and HyperLynx to verify signal and power integrity before committing to a spin.

  Why it matters

  This is where my two years of high-speed PCB design meet the deep learning work on this page: it's the board that would eventually run something like the vision models above, not simulate them on a laptop GPU. It's the project I'd point an embedded-AI interviewer to first.

  In progress — layout & verification phase[Ask about this build →](#contact)
- 05 / Classical ML, imbalanced data

  XGBoostRandom ForestBorderlineSMOTE

  ### Credit card fraud detection

  An ensemble of SVM, Random Forest and XGBoost stacked together to catch fraud in 284,807 transactions where only 0.17% are fraudulent.

  **0.973**ROC-AUC

  **0.865**PR-AUC

  **79.8%**of signal from one feature

  Approach

  With 284,315 legitimate transactions against 492 fraud cases, ROC-AUC is misleading: even 1,000 false alarms barely move the false-positive rate, so a weak model can still look strong. I reported PR-AUC instead, which ignores true negatives and scores only how well fraud itself is caught — it correctly exposed SVM's ROC-AUC of 0.96 as a poor PR-AUC of 0.60. Stacking a Logistic Regression meta-learner on top of the three base models beat simple soft voting, automatically weighting XGBoost highest.

  Finding

  XGBoost's feature importance showed one anonymised feature, V14, alone explains 79.8% of fraud-detection ability — likely a transaction authentication or merchant-risk score — a genuinely actionable lead for a simpler production model.

  scikit-learn · imbalanced-learn[Ask for details →](#contact)

#### RAG system

+

Semantic search over documents grounded by a generative model, to cut hallucination.

- Combined embedding-based semantic search (FAISS) with a generative language model (flan-t5) to answer natural-language queries over documents, via a Gradio interface.
- Grounded generated answers in retrieved context specifically to reduce hallucination and keep outputs reliable.
- Hands-on experience with the full generative AI stack end to end: embeddings, retrieval, and LLM-based generation.

sentence-transformersFAISSflan-t5Gradio

#### Structure from Motion

+

A monocular 3D reconstruction pipeline built from scratch, no library doing the geometry for me.

- Built a complete geometric vision pipeline from scratch: SIFT feature matching, FLANN matching, RANSAC outlier rejection, pose recovery and triangulation.
- Processed 740 frames end to end, reconstructing 14,088 3D points with 2.37 px mean reprojection error against ground truth.
- Demonstrates rigorous geometric reasoning and quantitative validation on real image sequences, not just a working demo.

OpenCVNumPySIFTRANSAC

#### Chest X-ray pneumonia classifier

+

ResNet50 transfer learning, where the simpler strategy beat the more expensive one.

- Trained an ImageNet-pretrained ResNet50 on 5,216 chest X-rays, comparing feature extraction against full fine-tuning under class-weighted loss.
- Feature extraction reached 85% test accuracy and 0.98 recall — fine-tuning the full 14.9M-parameter network overfit the small dataset instead.
- Deployed as a tested, containerised FastAPI service with automated CI/CD via GitHub Actions.

PyTorchResNet50FastAPIpytest

#### Customer churn prediction

+

LDA plus boundary-targeted oversampling, benchmarked against three other models.

- Built an imbalance-aware pipeline on 7,043 real customer records, using LDA (which uses the class labels to find the most separating direction, unlike unsupervised PCA) and BorderlineSMOTE to oversample only the ambiguous cases near the decision boundary.
- Tuned the decision threshold on held-out data via the precision-recall curve, reaching 0.644 F1 and 72.4% recall.
- Chose Logistic Regression over Random Forest despite RF's 97% recall, because RF's precision collapsed to 36% — it flagged almost everyone as a churner.

scikit-learnimbalanced-learnMLflow

#### Disease risk prediction with PCA

+

Cutting 30 correlated features to 10 without losing predictive power.

- Reduced the Wisconsin Breast Cancer dataset from 30 to 10 principal components (67% reduction) while retaining about 95% of the variance, after a correlation heatmap showed severe multicollinearity in the raw features.
- Reached 98% test accuracy with Logistic Regression on the orthogonal components, with only 1 false negative out of 43 malignant cases.
- Kept StandardScaler inside the pipeline, fit only on training folds, to avoid leaking test-set information into the scaling.

scikit-learnFastAPIMLflowpytest

#### Semi-supervised sentiment analysis

+

Testing when self-training actually helps — and documenting the case where it doesn't.

- Compared TF-IDF and dense sentence-embedding (all-MiniLM-L6-v2) representations for self-training on 200,000 Amazon reviews with only 2.5% labelled.
- Embeddings reached 85.14% accuracy, closing 94% of the gap to a fully supervised upper bound; TF-IDF self-training instead caused negative transfer — early mislabelled pseudo-labels compounded across retraining rounds.
- The finding: representation quality can substitute for label quantity, but a weak representation makes semi-supervised learning actively harmful.

scikit-learnsentence-transformersFastAPI

#### Multi-sensor anomaly detection

+

14 state space models flagging jet-engine degradation before it becomes failure.

- Built 14 independent per-sensor state space models (Kalman filter-based) on NASA CMAPSS turbofan sensor data, rather than one multivariate model, for interpretability and computational practicality.
- Combined the 14 signals into a weighted anomaly score and reached a 97.97% mean detection rate, explicitly reporting the trade-off against a 21.3% false-alarm rate from a 95th-percentile threshold on healthy data.
- Served asynchronously through FastAPI Background Tasks (so sensors never block on detection) with a PostgreSQL backend, orchestrated with Docker Compose.

State Space ModelsFastAPIPostgreSQLDocker Compose

#### Energy consumption regression

+

Statistical diagnosis before modelling, not after.

- Ran OLS regression and Variance Inflation Factor analysis on 768 buildings to find and remove multicollinear features before fitting the model — two features with VIF above 20 were dropped because they were near-duplicates of others already in the set.
- A p-value test dropped a third feature with no real relationship to the target, leaving 5 statistically validated predictors.
- Reached 0.909 test R² and 2.31 kWh mean absolute error, plus full residual diagnostics confirming the regression's assumptions held.

statsmodelsscikit-learnOLSVIF

#### RL stock trading agent

+

A Deep Q-Network that had to be stopped from learning the wrong lesson.

- Built a custom Gymnasium trading environment on 13 years of AAPL price and indicator data, and trained a Deep Q-Network agent with experience replay and a target network to stabilise learning.
- At 200K training timesteps the agent found a degenerate strategy — hold forever, never trade — a form of RL-specific overfitting invisible in the training metrics.
- Cutting training to 50K timesteps fixed it: the agent then outperformed a buy-and-hold baseline by 20.6% on unseen 2021-2023 test data.

Stable Baselines3GymnasiumDQN

#### Convolutional VAE face generator

+

The same latent-space idea behind Stable Diffusion, built from first principles.

- Implemented a convolutional Variational Autoencoder from scratch in PyTorch, with a 512-dimensional latent space, trained on 50,000 CelebA face images at 128×128 resolution.
- Used the reparameterisation trick (sampling noise separately from the learned mean/variance) so gradients could flow through an otherwise non-differentiable sampling step, and reduced reconstruction loss by 82% over 50 epochs.
- Diagnosed the "prior hole" problem limiting random-sample generation quality in high-dimensional latent spaces — the same encoder-decoder idea runs inside Stable Diffusion's compressed latent space.

PyTorchVAECelebA

## Experience

1. Aug 2023 to Aug 2025

   ### Hardware Design Engineer

   Teresol Pvt. Ltd., Islamabad
   - Designed a custom 16-layer board around the NVIDIA Jetson Tegra TK1 in Altium Designer, integrating PCIe, SERDES, Ethernet, USB3.0, DDR4 and HDMI, and led hardware planning from concept through prototyping to final testing.
   - Ran DC and AC power-delivery-network analysis in Siemens HyperLynx to verify power and signal integrity, and routed high-speed PCB interfaces (DDR, PCIe, USB3.0, SPI, Ethernet).
   - Diagnosed and resolved power-on-reset and Ethernet hardware faults on production boards, and flashed the eMMC of a custom Jetson-based GPU card.
   - Designed a hot-swappable, active load-sharing power supply with cascaded control for redundancy, plus high-slew-rate video amplifier and DAC circuits.
   - Programmed STM32, TI Cortex-M and RM57 microcontrollers in C/C++ for real-time embedded applications, including a FIFO data link between an RM57 microcontroller and an FPGA over dual-port RAM.
   - Designed and implemented an STM32-based hardware monitoring system, managing multiple sensor inputs and outputs, while working cross-functionally to translate requirements into technical solutions.
2. Jul 2022 to Aug 2022

   ### Electrical Engineer Intern

   National Transmission and Despatch Company (NTDC), Pakistan
   - Worked in the operations department at 500kV and 200kV grid stations, gaining hands-on experience in power-grid monitoring and control.
   - Learned relay-based protection control and national grid monitoring through SCADA systems.
   - Simulated power flow on the IEEE 14-bus system using the Newton-Raphson method in PowerWorld Simulator and ETAP, and performed load-flow analysis of a residential electrical system.

## Education

### MSc International Biometrics and Intelligent Vision

Université Paris-Est Créteil (UPEC), Sept 2025 to 2027 (expected)

Deep learning, computer vision, biometrics and multimedia, building toward a 6-month M2 internship from February 2027.

### BSc Electrical Engineering

International Islamic University, Islamabad, 2019 to 2023 — GPA 3.69

Final-year project: Mini Electric Tractor. Researched electric vehicles and designed the BLDC motor drive in Altium Designer, real-time motor control on a TI F280039C LaunchPad, and the battery management system.

01

Won the final-year design project competitionInternational Islamic University — Mini Electric Tractor

02

1st place, Arduino Programming and Interfacing CompetitionFETEX-23, IIUI

03

Winner, Real-Time Embedded Programming CompetitionFETEX-23, IIUI

04

Winner, MATLAB Guru CompetitionIIUI

05

Winner, Mini Project ExhibitionIIUI

06

6-month startup incubationARID University, Rawalpindi — Mini Electric Tractor venture

07

Reached the final round, Startup World PakistanMini Electric Tractor startup

08

Participant, Zindagi Prize startup competitionBusiness Incubation Center (BIC), IIUI

09

Volunteer, fundraisingShaukat Khanum Memorial Cancer Hospital and Research Center

Technical expertise

## Skills & Stack

From high-speed PCB design to deep learning models that end up running on hardware like it.

- 01

  ### Machine Learning & Deep Learning

  Model architectures and training strategies across supervised, generative and reinforcement learning.
  - PyTorch
  - TensorFlow
  - scikit-learn
  - XGBoost
  - CNN
  - ResNet
  - Transfer learning
  - Diffusion models
  - Variational autoencoders
  - State space models
- 02

  ### Computer Vision

  Detection, tracking and classical geometric vision.
  - OpenCV
  - YOLOv8
  - ByteTrack
  - SIFT / FLANN / RANSAC
  - Structure from Motion
  - Object detection & tracking
- 03

  ### Generative AI & NLP

  Retrieval, generation and language-model tooling.
  - RAG
  - Large language models
  - FAISS
  - sentence-transformers
  - Prompt engineering
- 04

  ### Data & Statistics

  The statistical groundwork behind a trustworthy model.
  - pandas
  - NumPy
  - statsmodels
  - PCA
  - OLS regression
  - Exploratory data analysis
- 05

  ### Engineering & MLOps

  Shipping a model as something another system can actually call.
  - Git
  - GitHub Actions CI/CD
  - FastAPI
  - Docker
  - Docker Compose
  - pytest
  - MLflow
  - PostgreSQL
- 06

  ### Embedded & Hardware

  High-speed digital design and the firmware that runs on it.
  - Altium Designer
  - High-speed PCB design
  - Vivado
  - Siemens HyperLynx (PI/SI)
  - STM32
  - TI Cortex-M / RM57
  - NVIDIA Jetson
- 07

  ### Languages

  Programming languages used across the AI and hardware work.
  - Python
  - C++
  - Embedded C
  - MATLAB
  - SQL

Get in touch

## Let's talk about an internship.

Available for a 6-month M2 internship from February 2027, in France or abroad, in AI, ML, deep learning, computer vision or embedded AI. Each field below has a copy button.

[LinkedIn](https://www.linkedin.com/in/muhammad-tayyab-hassan-4b565b230) [GitHub](https://github.com/engrtayyab596-wq)

Email

engrtayyab596@gmail.com

Phone

+33 7 45 63 77 85

Based in

Île-de-France, France

Muhammad Tayyab Hassan, Île-de-France.