# Common Task 1.2

Description:

Download the dataset (split across 17 files for two different physics models: QED and QCD) and preprocess and tokenize the target data and document your rationale for choice of tokenization. Data file is formatted with rows like

“interaction : Feynman diagram : amplitude : squared amplitude”.

Here the amplitudes are the input sequences and squared amplitudes are the target sequences. Note that indices like _123456 grow over the course of the dataset and should be normalized for each amplitude and squared amplitude. Use an 80-10-10 split of train-val-test across all files.

## Rationale

Tokenization is a critical design choice for this task because amplitudes and squared amplitudes are structured symbolic expressions containing operators, indices, momentum labels and special functions. To preserve the structure of these expressions I implemented a physics-informed tokenizer, that can be described as follows:

1. Maps unbounded, growing tensor indices to a fixed vocabulary pool (INDEX_n, PINDEX_n, MOMENTUM_n) which reduces vocabulary size and dependence on arbitrary index values.
2. Categorizes physical entities such as kinematic variables (MANDELSTAM_n), intrinsic masses and constants (I_UNIT & E_CHARGE) into distinct typed tokens enabling the model to learn their specific algebraic roles.
3. Flattens nested, multi-argument structures (like Dirac gamma_{...} matrices and spinor wavefunctions) into arity aware tokens (e.g. GAMMA_n) to preserve mathematical hierarchy without relying on bracket matching.
4. Preserves frequent physical coefficients and fractions (e.g. 1/2, 1/16, 1/144) as atomic tokens to maintain numerical coherence and reduce sequence length.

## Implementation

I have used text files to extract the expressions to create dataframe. Which was further split into train-val-test split. I have normalised the expressions and built the tokenizer.

Refer to the notebook for details.
