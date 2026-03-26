# SYMBA_Titans_Tasks

## Overview

This repo is my submissionn of evaluation tasks for **Titans for Squared Amplitude Calculation** SYMBA, ML4Sci.

## Folders

1. Folder [Common Task 1.2](./Common_Task_1.2/) contains notebook for tokenization and rationale of choice.
2. Folder [Specific Test 2.4](./Specific_Test_2.4/) contains notebooks for Titan variants and baselines.
3. Folder [Optional Specific Task 2.2](./Optional_Specific_Task_2.2/) contains notebooks for the Physics-Informed Transformer architecture.

## Problem Statement

Cross sections quantify interaction probabilities in particle physics and are computed from squared amplitudes. This project models amplitude to squared-amplitude mapping as a Seq2Seq task using Titans + MIRAS.

## Common Task 1.2 

Tokenisation and Dataset Preprocessing

Dataset: [Link](https://alabama.app.box.com/s/xhgr2onrn503jyse2fs5vxtapg0oifcs)  

For Details: [Readme](./Common_Task_1.2/readme.md)

## Specific Task 2.4

Titans architecture combined with MIRAS for squared amplitude calculation

For Details and model weights: [Readme](./Common_Task_2.4/readme.md)

## Results

### QED

| Model | Number of Encoders | Number of Decoders | Token Accuracy | Sequence Accuracy |
| ----- | ------------------ | ------------------ | -------------- | ----------------- |
| Transformer Baseline | 3 | 3 | 99.97\% | 97.22\% |
| MAL Encoder Decoder | 3 | 3 | 99.84\% | 91.67\% |
| MAG Encoder Decoder | 3 | 3 | 99.97\% | 97.22\% |
| MAC Encoder Decoder | 2 | 2 | 36.55\% | 19.44\% |

### QCD

| Model | Number of Encoders | Number of Decoders | Token Accuracy | Sequence Accuracy |
| ----- | ------------------ | ------------------ | -------------- | ----------------- |
| Transformer Baseline | 3 | 3 | 83.86\% | 66.67\% |
| MAL Encoder Decoder | 3 | 3 | 94.15\% | 79.17\% |
| MAG Encoder Decoder | 3 | 3 | 55.10\% | 70.83\% |
| MAG Encoder Decoder (Gating Disabled) | 3 | 3 | 85.38\% | 91.67\% |
| MAC Encoder Decoder | 3 | 3 | 48.46\\% | 00.00\% |

### MAG Analysis

We analyze the gating behavior of the MAG module by capturing gate activations from each decoder layer using forward hooks during inference. The sigmoid-normalized gate values are averaged across samples and feature dimensions to obtain mean gate trajectories over target positions.  

This provides insight into the model’s reliance on memory vs. local attention (SWA) across layers.

![MAG Gate Analysis](./Specific_Test_2.4/MAG/mag_gate_plot.png)

For Details: [Readme](./Specific_Test_2.4/MAG/readme.md)
