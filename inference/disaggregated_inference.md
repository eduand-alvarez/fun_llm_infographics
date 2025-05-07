What is disaggregated inference ⛓️‍💥 and why should you care? 

Disaggregated inference (DI) follows principles similar to the heterogeneous compute concept that the industry has been exploring for decades. The main difference today is that we haven’t yet landed on best practices for DI and today, DI is very GPU-centric. A few frameworks are beginning to enable the capability - most notably SGLang, vLLM, and Dynamo.

But what’s the actual benefit? 🤔 

Inference can be broken down into two key phases: prefill and decode. The prefill phase is compute-bound and can be thought of as a short burst with very high FLOPs demand. Decode, on the other hand, is memory bandwidth-bound, as it frequently reads from and writes to the KV cache.

Current monolithic inference setups perform both phases on the same accelerators. With DI, we can split (disaggregate) ⛓️‍💥 these workloads and tailor the deployment - dedicating specific GPUs to prefill and others to decode - optimizing each for their specific demands.

One pivotal trend that will undoubtedly drive demand for DI is deep reasoning. During reasoning, we generate "reasoning tokens," which significantly increase the number of tokens processed during decode. For deployments of large models like DeepSeek-R1 671B or the upcoming LLaMA 4 Behemoth 2T, it may make more sense to allocate a greater share of GPUs to decode rather than prefill. The ideal ratios are still an area of research, but the principle remains: DI allows us to invest in and configure compute resources for the right task... Ultimately saving energy, time, and money 🏆 

In the future we might see DI deployed multi-vendor, across GPUs and ASICs, across different accelerator generations, etc. - exciting times to come. 🚀 
