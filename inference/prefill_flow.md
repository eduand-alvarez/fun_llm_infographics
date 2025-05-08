🚀 Ever wondered what’s really happening under the hood before the first token is generated?

Inference can be broken down into two key components: prefill and decode. The first component, prefill, handles the initial processing of the input sequence, starting with breaking down the input into tokens and converting them into vector embeddings.

Next, positional encoding is applied to retain the relative position of each embedding. Then the real work begins when we compute attention and pass the embeddings through the feed-forward network (FFN) layers.

The primary output of the prefill phase is cache initialization, where hidden states and key/value caches are generated and stored for the input tokens. This enables faster processing during the decode phase.

Prefill is highly compute-intensive, often saturating GPU capacity through heavily parallel processing. Ultimately, these processes contribute the most to Time-To-First-Token (TTFT) - essentially, Prefill + First Token Latency.
