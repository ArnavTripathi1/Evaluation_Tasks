# MAC Variant

Memory-As-Context variant achieved a token_accuracy of 36.55% and sequence_accuracy of 19.44% on QED Dataset and 48.46% token_accuracy and 00.0% sequence accuracy on the tougher QCD Dataset.

This variant showed limited lower accuracy compared to the baseline, indicating the current memory integration requires further architecture refinement.

## MAC Implementation Details

### 1. Chunk-Level Gating for Memory Updates

he underlying Neural Memory module in this MAC implementation utilizes Chunk-Level Mean Pooling. The context vector $\mathbf{c}$ used to generate the optimizer gates (learning rate $\theta$, momentum $\eta$ and weight decay $\alpha$) is pooled across the entire chunk:

$$\mathbf{c} = \frac{1}{L} \sum_{i=1}^{L} \mathbf{x}_i$$

### 2. Static Block-Context Prefixing

The implementation enforces Static Block-Context Prefixing. The memory state is updated based on chunk $t-1$ and the resulting retrieval output $\mathbf{M}_{context}$ is held strictly constant as a prefix for the entirety of chunk $t$. 

When computing the self-attention for the current chunk, the keys ($\mathbf{K}$) and values ($\mathbf{V}$) are concatenated with this static historical memory block:

$$\mathbf{K}_{chunk} = [ \mathbf{M}_{context}^K ; \mathbf{K}_{local} ]$$
$$\mathbf{V}_{chunk} = [ \mathbf{M}_{context}^V ; \mathbf{V}_{local} ]$$

By freezing the memory context for the duration of the $L$-length chunk the short-term attention mechanism is provided a stable historical reference point.

## Architecture

I used a standard Encoder and a MAC augmented Decoder for the architecture.

<div align="center">
  <img src="./MAC.png" alt="MAC" width="500"/>
</div>
