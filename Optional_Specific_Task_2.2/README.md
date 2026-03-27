# Specific Task 2.2

I developed a physics-informed dual head transformer for squared amplitude calculation.

Find all model weights at [link](https://drive.google.com/drive/folders/1ee1gqKr-H4R3zz_dK6ZFfA-w2e5fXSfr?usp=share_link)

## Ablation Study

I performed an ablation study to analyze performance of different physics-informed components using the Transformer architecture.

I compared two different KAN Heads on a Standard Encoder-Decoder Transformer with RoPE for positional encodings and reported performance for SineKAN and Chebyshev Polynomial based KAN (using first kind polynoimals), the SineKAN head gave +1.65% token_accuracy gain and +5.56% sequence_accuracy gain on the QED Dataset and +4.70% token_accuracy gain and +8.70% sequence_accuracy gain on the QCD Dataset over Chebyshev Polynomial KAN.

The token_accuracies of SineKAN were further improved by utilising SIREN activation in both Encoder and Decoder.

The Sparsely Gated MoE head using SineKAN experts gave 99.18% token_accuracy and 66.67% sequence_accuracy on the QED Dataset and 90.30% token_accuracy and 65.22% sequence_accuracy on the QCD Dataset. With an auxiliary loss for load balancing.

Further, I added dual heads on the SineKAN Transformer, this separates structural token prediction from numerical value estimation. For this model I updated the tokenizer to not merge any numeric value occuring in the expressions except for the growing indices that were to be normalised. I used Huber Loss as numeric Regression loss should not dominate the symbolic Cross Entropy loss.

At inference time I rounded off the values output by the numeric head, as all the numbers occuring in the dataset were observed to be integers. This approach gave a **96.39%** token_accuracy and **88.89%** sequence_accuracy on the QED Dataset and **97.43%** token_accuracy and **65.22%** sequence_accuracy on the QCD Dataset.

<div align="center">
  <img src="./Distribution.png" alt="Distribution" width="300"/>
</div>

## Architecture

The following architecture was implemented for Dual Heads:

<div align="center">
  <img src="./PIT.png" alt="PIT" width="500"/>
</div>
