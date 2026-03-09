# PDI-Diff: Physically Decoupled Interactive Diffusion for Low-Light Image Enhancement

## 📖 Overview

Low-light image enhancement (LLIE) remains a formidable challenge in computer vision due to the complex entanglement of severe illumination degradation, photon noise, and non-linear chromatic distortion. While recent generative diffusion models excel at synthesizing high-frequency textures, deploying them directly in the tightly coupled RGB color space often leads to uncontrolled color deviations and the hallucination of non-existent structural artifacts.

To fundamentally overcome these bottlenecks, we introduce **PDI-Diff**, a novel, physically-inspired generative framework that synergistically bridges explicit physical priors with latent diffusion techniques. 

Instead of relying on the standard RGB format, our method leverages the **HVI color space** to explicitly decouple the degraded input into distinct **Intensity** and **Chromaticity** representations. This allows the network to model structural illumination and color fidelity independently yet synchronously.

## ✨ Key Features & Architecture

Our framework is driven by three core architectural innovations:

*   **🧱 Parallel Convolutional Coarse Module (PCCM):** 
    Acts as the deterministic foundation of our pipeline. It extracts robust physical anchors from the degraded image, providing a highly stable structural prior that prevents the subsequent diffusion process from generating arbitrary or unconstrained artifacts.
*   **🌌 Physically Decoupled Interactive Diffusion (PDID):** 
    A specialized dual-stream generative diffusion module tailored for the decoupled HVI space. It performs fine-grained stochastic refinement, restoring realistic textures for intensity and vibrant colors for chromaticity without cross-channel interference.
*   **🔗 Interaction Factor (IF):** 
    A dynamic gating mechanism designed to bridge the semantic gap between the two diffusion streams. By feeding spatial boundary cues from the intensity stream into the chromaticity branch, it explicitly averts spatial misalignment and color bleeding.
