# MAC Variant

Memory-As-Context variant achieved a token_accuracy of 36.55% and sequence_accuracy of 19.44% on QED Dataset and 48.46% token_accuracy and 00.0% sequence accuracy on the tougher QCD Dataset.

This variant showed limited lower accuracy compared to the baseline, indicating the current memory integration requires further architecture refinement.

## MAC Implementation Details

### Chunk-Level Gating for Memory Updates

The underlying Neural Memory module in this MAC implementation utilizes Chunk-Level Mean Pooling. The context vector $\mathbf{c}$ used to generate the optimizer gates (learning rate $\theta$, momentum $\eta$ and weight decay $\alpha$) is pooled across the entire chunk:

$$\mathbf{c} = \frac{1}{L} \sum_{i=1}^{L} \mathbf{x}_i$$

## Architecture

I used a standard Encoder and a MAC augmented Decoder for the architecture.

<div align="center">
  <img src="./MAC.png" alt="MAC" width="500"/>
</div>
