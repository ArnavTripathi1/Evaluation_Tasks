# MAL Variant

Memory-As-Layer variant achieved 99.84% token_accuracy and 91.67% sequence_accuracy on the QED Dataset and 94.15% token_accuracy and 79.17% sequence_accuracy on the QCD Dataset.

## Memory Diagnostics

To understand the test time learning more I logged three internal signals (for a single sequence of QED Dataset) per Decoder layer: Gradient Norm (||∇w​L||), associative memory loss and memory update magnitude (||Δw||).

<div align="center">
  <img src="./grad_norm.png" alt="MAL" width="600"/>
</div>

<br>

The above gradient norm plot shows gradual decline in gradient magnitude for some layers across later chunks which indicates memory becomes slightly less surprised as the sequence progress which is a desirable behavior for an adaptive memory system.

<div align="center">
  <img src="./memory_loss.png" alt="MAL" width="600"/>
</div>

<br>

$$\mathcal{L}_{assoc} = \frac{1}{N} \sum_{i=1}^{N} \| \text{MLP}_{W_t}(k_i) - v_i \|^2$$

The associative memory loss plot shows that the memory is actively trying to fit the key-to-value mapping inside each chunk. The loss values remain close to 1.0 so the absolute reduction is moderate.

<div align="center">
  <img src="./update_norm.png" alt="MAL" width="600"/>
</div>

<br>

This plot reflects how much internal memory weights are changing. Layer 2 has the largest update magnitude overall while Layer 1 has the smallest. Layer 3 starts with relatively small updates but becomes more active toward later chunks, which aligns with its improving loss trend.

## Architecture

For both datasets I used 3 Encoder and 3 Decoder Layers.

<div align="center">
  <img src="./MAL.png" alt="MAL" width="500"/>
</div>
