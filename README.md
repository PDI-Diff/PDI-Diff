PDI-Diff: Physically Decoupled Interactive Diffusion for Low-Light Image Enhancement
This repository contains the official PyTorch implementation of the paper: Breaking Channel Coupling: Physically Decoupled Interactive Diffusion for Low-Light Enhancement.

Observation and Motivation
Low-light image enhancement (LLIE) is challenging due to the complex entanglement of illumination degradation, heavy photon noise, and irregular color shifts. While deterministic architectures achieve success in recovering global visibility, they often produce over-smoothed textures in extreme dark regions.

Generative models, specifically Denoising Diffusion Probabilistic Models (DDPMs), provide a solution by synthesizing high-frequency details. However, current diffusion methods typically operate in the coupled RGB space, which leads to unpredictable color deviations. Although the HVI color space offers an effective operational manifold for decoupling, existing HVI-based regression models lack the stochastic capacity to restore photorealistic textures. PDI-Diff bridges this gap by executing parallel reverse diffusion processes within the HVI manifold to ensure both physical consistency and perceptual fidelity.

Technical Features
PDI-Diff focuses on a dual-stream diffusion strategy to handle illumination and chromaticity independently:

Parallel Convolutional Coarse Module (PCCM):

Uses Structure-Aware Dense Blocks (SADB) to capture global geometric anchors via dilated convolutions.

Employs Chromaticity Preservation Blocks (CPB) to establish reliable color anchors through instance normalization.

Physically Decoupled Interactive Diffusion (PDID):

Executes two parallel reverse diffusion branches to synthesize high-frequency textures for intensity and color independently.

Prevents cross-channel interference inherent in standard RGB-based diffusion processes.

Interaction Factor (IF):

A dynamic gating mechanism that propagates structural boundary cues from the intensity branch to the chromaticity branch.

Ensures spatial alignment and prevents color bleeding throughout the stochastic generation process.
