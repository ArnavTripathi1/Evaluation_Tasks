# MAC Variant

Memory-As-Context variant achieved a token_accuracy of 36.55% and sequence_accuracy of 19.44% on QED Dataset and 48.46% token_accuracy and 00.0% sequence accuracy on the tougher QCD Dataset.

This variant showed limited lower accuracy compared to the baseline, indicating the current memory integration requires further architecture refinement.

I used a standard Encoder and a MAC augmented Decoder for the architecture.

## Architecture

I used a standard Encoder and a MAC augmented Decoder for the architecture.

<div align="center">
  <img src="./MAC.png" alt="MAC" width="500"/>
</div>
