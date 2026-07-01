# The Latency-Overhead of Online Dictionary Projection

Routing intermediate states through massive Sparse Autoencoders adds substantial projection time. This challenge requires hardware-fused execution blocks to run projection steps in SRAM memory.

## Mechanism

Triton and CUDA kernels fuse encoder projection, thresholding, and addition directly into a single GPU block to avoid DRAM traffic.

```mermaid
graph TD
    Hidden[Hidden State in SRAM] -->|Hardware Fused Kernel| SAE_Encoder[SAE Encoder Projection]
    SAE_Encoder --> TopK[Top-K Thresholding]
    TopK --> Add[Steering Addition]
    Add --> SAE_Decoder[SAE Decoder Projection]
    SAE_Decoder --> Output[Steered Hidden State in SRAM]
```

## Mitigation
- Direct SRAM fusion using Triton/CUDA.
- Reduced precision float operations.
