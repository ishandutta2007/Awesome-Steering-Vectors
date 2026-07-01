# The Representation Exploded Saturation Boundary

If the steering scale multiplier ($\alpha$) is set too high, the hidden representations deform, leading to repetition, loss of syntax, or model collapse.

## Mechanism

Dynamic Activation Clipping monitors the Euclidean norm of activations at runtime, dynamically scaling down the steering vectors if they exceed safe thresholds.

```mermaid
graph TD
    Hidden[Hidden State] --> CalcNorm[Calculate Euclidean Norm]
    CalcNorm --> Check{Exceeds Threshold?}
    Check -->|Yes| ScaleDown[Scale Down Steering Vector]
    Check -->|No| ApplyNormal[Apply Normal Steering Vector]
    ScaleDown --> Inject[Inject Vector]
    ApplyNormal --> Inject
    Inject --> Output[Output State]
```

## Mitigation
- Dynamic norm scaling.
- Layer-wise proportional boundaries.
