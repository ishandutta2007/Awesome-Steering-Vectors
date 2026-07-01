# Multi-Layer Latent Injection Hooks

Dictates the depth and boundaries of activation steering. Rather than injecting steering values into a single layer, this technique places hooks across target model horizons (typically middle layers).

## Mechanism

Interventions are performed dynamically across layers where abstract concepts are synthesized.

```mermaid
graph TD
    Input[Input Tokens] --> Layer1_11[Early Layers 1-11<br/>Syntactic Features]
    Layer1_11 --> Hook12{Hook Layer 12<br/>Inject Offset}
    Hook12 --> Hook24{Hook Layer 24<br/>Inject Offset}
    Hook24 --> Layer25_32[Late Layers 25-32<br/>Output Selection]
    Layer25_32 --> Output[Output Tokens]
```

## Advantages
- Better alignment fidelity without disrupting early parser stages.
- Ensures stable concept representation updates.
