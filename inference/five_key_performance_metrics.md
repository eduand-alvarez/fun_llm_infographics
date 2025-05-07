🚨 The 5 Metrics That Make or Break LLM Inference Performance 🔥

The question of "how fast LLMs can generate an output" is not as straightforward as starting the clock when we hit "enter" and stopping it when the last word is generated.

In LLM performance analysis, we look at various metrics, from token-level to kernel-level performance. It’s crucial to remember that while these metrics are often associated with a specific model’s performance, they are ultimately determined by the processor's capabilities running the model and software optimization. If we are measuring or reporting performance, we typically focus on five key metrics: 

⭐ TPOT (ms/token): Directly ties to decode performance. For longer output sequences, it is critical to ensure that end-to-end latency is manageable. In 2022, the acceptable threshold for this metric was <100ms (average human reading rate per word). With today’s advances, the target TPOT is now widely considered to be <50ms.

⭐ TTFT (ms): Measures how quickly the system generates the first token after prefill, heavily impacted by the size of the input sequence. It is a good indicator of prefill performance. Depending on the use case, the threshold for TTFT can vary significantly. For real-time applications with low latency requirements and short output sequences, TTFT becomes more critical as it contributes significantly to overall latency. For use cases with very large output sequences, TTFT becomes a negligible contributor to the overall user experience or system latency.

⭐ End2EndLatency (s): Measures the inference process, including prefill and decode. Some include de-tokenization latency as well. It represents the overall system performance and is a key indicator of user experience. It comprises TTFT and the TPOT for each output token in the output sequence.

⭐ Throughput (tokens/s): Critical for scalability, throughput measures the number of tokens generated per unit of time. It is primarily affected by concurrency and request volume. More parallel requests can reduce throughput and increase latency, the cost of scaling to more users. In non-real-time use cases (offline inference), where latency is less critical, throughput can be maximized and is mainly constrained by the memory and compute capacity of the processor.

⭐ TPU (users/minute): The "final boss" metric, TPU, is most closely tied to how the system scales in production. It is often challenging to measure accurately, as it requires a staging or mock deployment with business logic in place. TPU is essentially the business-case evolution of throughput, translating throughput into real-world user-serving capacity.
