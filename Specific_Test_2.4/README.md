# Specific Test 2.4

## Titans variants for Sqaured Amplitude Calculation

I have used Encoder-Decoder style Attention-Titans hybrid models, having similar architecture to seq2seq transformers. Placing Titans modules in Decoder layers.

## Implementation Details

I implemented the architectures using PyTorch and referring to implementation details in the Titans paper.

For a strong baseline I trained a Standard Transformer. After hyperparameter tuning I achieved 99.97% token_accuracy and 97.22% sequence_accuracy on QED Dataset and 83.86% token_accuracy and 66.67% sequence_accuracy on QCD Dataset.

All model weights can be found at [link](https://drive.google.com/drive/folders/1tYG6kcrkOlJbIFp5gz4NhE1fQcu83bLV?usp=share_link)

Refer to the corresponding variant-specific folders for detailed architecture configurations.
