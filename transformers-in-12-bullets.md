# The Transformer in 12 Bullet Points

1. The core problem the Transformer was designed to solve:

The core problem the Transformer was designed to solve is that of sequence modelling and transduction (i.e., transferring one sequence into another, such as machine or language translation), which was previously addressed by RNN and CNN models.

2. The role of self-attention and what it replaces:

Self-attention forms part of the transformer architecture and it is what allows each token token to attend to other tokens in the sequence without sequentional processing and state, allowing transformers to relpace the recursive, sequential architecture of RNNs and CNNs with fully parallelisable attention blocks.

3. The meaning and function of queries, keys, and values:

The queries, keys and values of a transformer are projections of the input matrixusing learned weights: the query matrix tells the model what a given token wants to know; the key matrix tells the model what a give token offers; and the value matrix tells the model what the context is.

4. Why attention is scaled and where the scaling factor comes from:

Attention is computed by the dot-product of each query against all of the keys; as the number of keys gets large, the dot-product will also tend to get large, so the dot-product is scaled by a number proportional to the length of the keys.

5. The purpose of multi-head attention beyond simple parallelism:

Multi-head attention enables the model to run several attention blocks in parallel on the queries, keys and values matrices, allowing it to learn different relationship patterns from the input by projecting it into different representation subspaces, which would not be possible for a single attention block.

6. The function of positional information and why it must be injected:

The transformer model contains no recurrence or convolution which it can use to build up a picture of the sequential order of the input; hence it is necessary to inject positional information to the inputs in the encoder and decoder stacks.

7. The role of residual connections in the architecture:

The residual connection adds the original input to the output of each layer in the encoder and decoders stacks; this allows the layer to retain original information about the input, stabilise gradients, learn more efficiently and stack deeper layers without accumulating errors.

8. The role of layer normalization and its placement:

Normalization ensures that activations maintain a consistent scale across layers; it was placed after the residual connection to ensure that the final output of the layer was normalized (however, in later models the normalization is placed before the residual connection to prevent signal degradation).

9. The distinction between encoder and decoder attention:

The encoder builds contextual embeddings using un-masked self-attention on the input sequence; the decoder generates output autoregressively using masked self-attention on the output sequence (to prevent "cheating") and cross-attention on the encoder output.

10. The computational complexity characteristics of self-attention:

During self-attention, the model must compute scores for each pair of tokens in the input sequence; thus, for a sequence of N tokens, the complexity of self-attention is O(N^2).

11. The implications of the architecture for parallelism during training:

The transformer replaced the sequential structure of RNN and CNN models with one in which only attention mattered, and attention can be captured by computing all of the scores between all pairs at the same time, using matrix multiplication, which is _highly_ parallelizeable.

12. One performance or scaling implication relevant to inference or deployment:

During training, the encoder dominates as the bottleneck (it's strongly parallelizeable, but the sequences can be very large); during inference, the decoder dominates as the bottleneck (since the output is generated sequentially using an autoregressive process).
