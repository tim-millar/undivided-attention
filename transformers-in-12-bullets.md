# The Transformer in 12 Bullet Points

1. The core problem the Transformer was designed to solve is that of sequence modelling and transduction (i.e., transferring one sequence into another, such as machine or language translation), which was previously addressed by RNN models that were hard to parallelize and had path length issues between distant tokens, and CNN models that had difficulty modeling long-range dependencies.

2. Self-attention is what allows each token to attend to other tokens in the sequence without processing state sequentially, allowing transformers to replace recursion in the architecture of RNNs with fully parallelisable attention blocks.

3. The queries, keys and values of a transformer are projections of the input matrix using learned weights: the query matrix tells the model what a given token wants to know; the key matrix tells the model what a given token offers; and the value matrix contains the actual information that is transferred to tokens that find a match between their queries and those keys.

4. Attention is computed by the dot-product of each query against all of the keys; when the dimensionality of the key-vectors is large, the dot-product will also tend to get large, so the dot-product is scaled by a number proportional to the dimensionality of the key-vectors.

5. Multi-head attention enables the model to run several attention blocks in parallel on the queries, keys and values matrices, allowing it to learn different relationship patterns from the input by projecting it into different representation subspaces, which would not be possible for a single attention block.

6. The transformer model contains no recurrence or convolution which it can use to build up a picture of the sequential order of the input; hence it is necessary to inject positional information to the inputs in the encoder and decoder stacks.

7. Residual connections add the original input to the output of each layer in the encoder and decoder stacks; this allows the layer to retain original information about the input, stabilise gradients, learn more efficiently and stack deeper layers without accumulating errors.

8. Normalization ensures that activations maintain a consistent scale across layers; in the early versions of the model it was placed after the residual connection to ensure that the final output of the layer was normalized (however, in later models the normalization is placed before the residual connection to ensure training stability and gradient flow).

9. The encoder builds contextual embeddings using un-masked self-attention on the input sequence; the decoder generates output autoregressively using masked self-attention on the output sequence (to prevent "cheating") and cross-attention on the encoder output.

10. During self-attention, the model must compute scores for each pair of tokens in the input sequence; thus, for a sequence of N tokens of dimension d, the time-complexity of self-attention is O(N^2 * d), whereas the space required to store the attention matrix is O(N^2).

11. The transformer replaced the sequential structure of RNN models with one in which there is no temporal dependency during training, and attention can be captured by computing all of the scores between all pairs at the same time, using matrix multiplication, which is _highly_ parallelizeable.

12. During training, the encoder dominates as the bottleneck (it's strongly parallelizeable, but the sequences can be very large); during inference, the decoder dominates as the bottleneck (since the output is generated sequentially using an autoregressive process).
