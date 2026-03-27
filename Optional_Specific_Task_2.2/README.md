# Specific Task 2.2

I developed a physics-informed dual head transformer for squared amplitude calculation.

Find all model weights at [link](https://drive.google.com/drive/folders/1ee1gqKr-H4R3zz_dK6ZFfA-w2e5fXSfr?usp=share_link)

Ablation Study Details: [Ablation](./Ablation.md)

## Architecture

The following architecture was implemented for Dual Heads, where both Encoder and Decoder have 3 layers each and a model dimension of 256, with 4 attention heads for QED and 8 attention heads for QCD Dataset:

<div align="center">
  <img src="./PIT.png" alt="PIT" width="500"/>
</div>
