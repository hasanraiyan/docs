# Source: https://coursify.hasanraiyan.me/research/generative-ai

Generative AI

# 

Generative AI

Verified Sources

Jun 13, 2026

## AI Summary

Generative AI refers to models that learn patterns from large datasets and then generate novel outputs resembling that data. Modern foundation models power systems for chat, summarization, coding, image synthesis, audio generation, and multimodal reasoning.[2]() The current era is dominated by transformers for language and diffusion models for image generation, though GANs and VAEs remain historically important.

A useful way to frame the field is by the conditional distribution a model learns: p(x),p(x∣c),orp(y∣x)p(x), \\quad p(x \\mid c), \\quad \\text{or} \\quad p(y \\mid x)p(x),p(x∣c),orp(y∣x) where xxx may be text, images, or audio, and ccc is some conditioning signal such as a prompt, class label, or another modality. In practice, generative systems approximate these distributions with large neural networks trained on internet-scale or enterprise-scale corpora.[2]()

Generative AI has expanded rapidly because pretraining on large unlabeled datasets creates reusable capabilities, while fine-tuning, prompting, retrieval, and tool use adapt the model to specialized tasks.[2]() At the same time, the technology introduces substantial risks: confabulation, harmful bias, privacy leakage, copyright disputes, and deepfakes.

## Footnotes

1. [Generative AI and the Foundation Model Era: A Comprehensive Review](https://www.mdpi.com/2504-2289/10/3/94) - Survey of architectures, training, evaluation, and applications across transformers, diffusion, and multimodal models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-1-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-1-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-1-4)
 
2. [What Are Foundation Models? - NVIDIA Blog](https://blogs.nvidia.com/blog/what-are-foundation-models) - Overview of foundation models and their role in modern generative AI. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-2-2)
 
3. [The two models fueling generative AI products: Transformers and diffusion models](https://www.gptechblog.com/generative-ai-models-transformers-diffusion-models) - Explains pretraining, foundation models, and the roles of transformers and diffusion models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
4. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 

#### Generative AI Explained In 5 Minutes

#### Core idea

Generative AI is not just prediction in the narrow sense; it models data distributions well enough to synthesize plausible new outputs across modalities.

## Footnotes

1. [Generative AI and the Foundation Model Era: A Comprehensive Review](https://www.mdpi.com/2504-2289/10/3/94) - Survey of architectures, training, evaluation, and applications across transformers, diffusion, and multimodal models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 

more...

### Why generative AI matters

Generative AI matters because one pre-trained model can support many downstream tasks with minimal task-specific engineering. This shifts software from deterministic rule writing toward probabilistic interaction through prompts, examples, retrieval, and safety controls. In industry, these systems now support search assistants, software development, marketing content, document analysis, customer support, simulation, and scientific workflows.[2]()

Economically, generative AI investment has accelerated sharply. Stanford HAI reports that global private investment in generative AI reached 25.2billionin2023,nearlyeighttimesthe2022level.\[5\]Thesamereportnotesthat149foundationmodelswerereleasedin2023,and25.2 billion in 2023, nearly eight times the 2022 level.\[^5\] The same report notes that 149 foundation models were released in 2023, and 25.2billionin2023,nearlyeighttimesthe2022level.\[5\]Thesamereportnotesthat149foundationmodelswerereleasedin2023,and65.7% ofthemwereopen−source,upfromof them were open-source, up fromofthemwereopen−source,upfrom44.4%in2022.\[5\]Yetfrontiercapabilityisexpensive:Stanfordestimatedcomputetrainingcostsofaboutin 2022.\[^5\] Yet frontier capability is expensive: Stanford estimated compute training costs of aboutin2022.\[5\]Yetfrontiercapabilityisexpensive:Stanfordestimatedcomputetrainingcostsofabout78millionforGPT−4andmillion for GPT-4 andmillionforGPT−4and191$ million for Gemini Ultra.

### Main capability areas

| Capability | Typical model family | Example outputs | Key challenge |
| --- | --- | --- | --- |
| Text generation | Transformers / LLMs | Summaries, chat, code | Factuality[2]() |
| Image generation | Diffusion models | Art, design mockups, product imagery | Copyright, misuse[2]() |
| Audio generation | Autoregressive / diffusion | Voice cloning, music | Identity misuse |
| Multimodal generation | Vision-language / unified models | Image captioning, visual QA, text-to-image | Cross-modal safety[2]() |
| Synthetic data | Specialized generators | Training augmentation, simulation | Bias propagation |

A crucial technical distinction is between open-source and closed models. Stanford's AI Index notes that closed models still often outperform open ones on common benchmarks, but the open ecosystem expanded substantially in 2023.[2]()

## Footnotes

1. [Generative AI and the Foundation Model Era: A Comprehensive Review](https://www.mdpi.com/2504-2289/10/3/94) - Survey of architectures, training, evaluation, and applications across transformers, diffusion, and multimodal models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-1-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-1-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-1-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-1-5)
 
2. [The 2024 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2024-ai-index-report) - Key 2024 statistics on generative AI investment, model releases, costs, and evaluation gaps. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-5-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-5-3)
 
3. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-4-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-4-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-4-5)
 
4. [Stanford's 2024 AI Index Tracks Generative AI and More - IEEE Spectrum](https://spectrum.ieee.org/ai-index-2024) - Summary of open versus closed model trends and model release patterns discussed in the AI Index. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-6)
 

### 

High-Level Evolution of Generative AI

#### Probabilistic and neural generation foundations

Early era

Earlier generative approaches established statistical modeling and neural sequence generation before large-scale foundation models became dominant."

## Footnotes

1. [Generative AI and the Foundation Model Era: A Comprehensive Review](https://www.mdpi.com/2504-2289/10/3/94) - Survey of architectures, training, evaluation, and applications across transformers, diffusion, and multimodal models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 

#### GANs, VAEs, and transformer breakthrough

2014–2019

GANs and VAEs advanced image generation, while transformers became central to scalable language modeling."

## Footnotes

1. [Generative AI and the Foundation Model Era: A Comprehensive Review](https://www.mdpi.com/2504-2289/10/3/94) - Survey of architectures, training, evaluation, and applications across transformers, diffusion, and multimodal models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 

#### Foundation model scaling

2020–2022

Large pretrained models expanded few-shot learning, instruction following, and multimodal generation.[2]()"

## Footnotes

1. [Generative AI and the Foundation Model Era: A Comprehensive Review](https://www.mdpi.com/2504-2289/10/3/94) - Survey of architectures, training, evaluation, and applications across transformers, diffusion, and multimodal models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [What Are Foundation Models? - NVIDIA Blog](https://blogs.nvidia.com/blog/what-are-foundation-models) - Overview of foundation models and their role in modern generative AI. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 

#### Consumer and enterprise adoption

2022–2024

Chat assistants and diffusion-based image systems accelerated public adoption, investment, and governance debates.[2]()"

## Footnotes

1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
2. [The 2024 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2024-ai-index-report) - Key 2024 statistics on generative AI investment, model releases, costs, and evaluation gaps. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

#### Multimodal, tool-using, and governed systems

Current direction

The field is moving toward retrieval, agents, smaller efficient models, and stronger risk management practices.[2]()"

## Footnotes

1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
2. [The 2025 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2025-ai-index-report) - Reports falling inference costs, improving open-weight models, and broader accessibility trends. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 

### Technical foundations

The backbone of language-oriented generative AI is the transformer. Instead of processing tokens only sequentially, self-attention enables the model to weigh relationships among tokens across a context window. Given token representations XXX, attention is commonly expressed as: Attention(Q,K,V)\=softmax(QK⊤dk)V\\text{Attention}(Q,K,V)=\\text{softmax}\\left(\\frac{QK^\\top}{\\sqrt{d\_k}}\\right)VAttention(Q,K,V)\=softmax(dk​​QK⊤​)V This mechanism makes it easier to model long-range dependencies than earlier recurrent designs, and it scales effectively with large datasets and compute.

For image synthesis, diffusion models learn to reverse a gradual corruption process. Training adds noise step by step to data; generation starts from noise and denoises iteratively to produce an image. Conceptually: xt\=1−βtxt−1+βtϵ,ϵ∼N(0,I)x\_t = \\sqrt{1-\\beta\_t}x\_{t-1} + \\sqrt{\\beta\_t}\\epsilon, \\qquad \\epsilon \\sim \\mathcal{N}(0, I)xt​\=1−βt​​xt−1​+βt​​ϵ,ϵ∼N(0,I) and the model learns the reverse process to estimate a clean sample from noisy states.

Other important families include:

- GANs for sharp image synthesis, though often unstable in training.
- VAEs for structured latent spaces and efficient sampling.
- Multimodal models that align text, image, audio, and video representations for cross-modal generation and understanding.

## Footnotes

1. [Generative AI and the Foundation Model Era: A Comprehensive Review](https://www.mdpi.com/2504-2289/10/3/94) - Survey of architectures, training, evaluation, and applications across transformers, diffusion, and multimodal models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-1-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-1-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-1-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-1-5) [↩6](https://coursify.hasanraiyan.me/#user-content-fnref-1-6) [↩7](https://coursify.hasanraiyan.me/#user-content-fnref-1-7)
 

### How a Generative AI System Is Built and Deployed

1. 1
 
 Step 1
 
 Collect and prepare data
 
 Assemble text, image, audio, or multimodal corpora; filter low-quality, unsafe, duplicated, or non-compliant data; document provenance because data quality strongly affects downstream bias, memorization, and usefulness.[2]()
 
 ## Footnotes
 
 1. [Generative AI and the Foundation Model Era: A Comprehensive Review](https://www.mdpi.com/2504-2289/10/3/94) - Survey of architectures, training, evaluation, and applications across transformers, diffusion, and multimodal models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
2. 2
 
 Step 2
 
 Pretrain a foundation model
 
 Train a large model on broad datasets so it learns reusable statistical structure and representations rather than a single narrow task.[2]()
 
 ## Footnotes
 
 1. [Generative AI and the Foundation Model Era: A Comprehensive Review](https://www.mdpi.com/2504-2289/10/3/94) - Survey of architectures, training, evaluation, and applications across transformers, diffusion, and multimodal models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [What Are Foundation Models? - NVIDIA Blog](https://blogs.nvidia.com/blog/what-are-foundation-models) - Overview of foundation models and their role in modern generative AI. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2)
 
 
3. 3
 
 Step 3
 
 Adapt to downstream use
 
 Use prompting, supervised fine-tuning, retrieval-augmented generation, domain adaptation, or instruction tuning to make the model useful for enterprise or product scenarios.[2]()
 
 ## Footnotes
 
 1. [Generative AI and the Foundation Model Era: A Comprehensive Review](https://www.mdpi.com/2504-2289/10/3/94) - Survey of architectures, training, evaluation, and applications across transformers, diffusion, and multimodal models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 2. [The 2025 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2025-ai-index-report) - Reports falling inference costs, improving open-weight models, and broader accessibility trends. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 
 
4. 4
 
 Step 4
 
 Evaluate performance and risk
 
 Measure task quality, robustness, calibration, safety, and failure modes because leading model providers still lack standardized responsibility reporting across benchmarks.
 
 ## Footnotes
 
 1. [The 2024 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2024-ai-index-report) - Key 2024 statistics on generative AI investment, model releases, costs, and evaluation gaps. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 
5. 5
 
 Step 5
 
 Add governance and controls
 
 Apply access control, logging, human review, output filtering, and usage policies to reduce harmful or non-compliant outputs.
 
 ## Footnotes
 
 1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
6. 6
 
 Step 6
 
 Monitor in production
 
 Track drift, abuse, prompt injection, user feedback, latency, and cost; update prompts, retrieval sources, and safeguards continuously as the system encounters real workloads.[2]()
 
 ## Footnotes
 
 1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 2. [The 2025 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2025-ai-index-report) - Reports falling inference costs, improving open-weight models, and broader accessibility trends. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 
 

#### Practical design principle

For high-stakes use cases, combine generation with retrieval, citations, human review, and domain constraints instead of relying on free-form model output alone.[2]()

## Footnotes

1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
2. [The 2025 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2025-ai-index-report) - Reports falling inference costs, improving open-weight models, and broader accessibility trends. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 

more...

### Common workflows and architectures

A production-grade generative AI application rarely consists of a bare model call. Instead, robust systems often add retrieval, policy checks, tools, memory, and post-processing. A common enterprise pattern is RAG, where relevant documents are fetched first and then used to condition generation. This improves specificity and can reduce unsupported claims, though it does not eliminate them.[2]()

Another emerging pattern is agentic orchestration, where a model plans tasks, calls tools, and iterates. This is powerful but increases operational complexity, security exposure, and debugging difficulty. NIST emphasizes risk management throughout design, deployment, and monitoring rather than treating safety as a final add-on.

### Evaluation dimensions

Generative models must be evaluated beyond raw benchmark scores. Important dimensions include:

- Utility: Does the output solve the intended task?
- Faithfulness: Is the answer supported by sources or context?[2]()
- Robustness: Does performance degrade under adversarial or ambiguous prompts?
- Safety: Does the system produce harmful, hateful, or abusive content?
- Privacy: Does it leak personal or memorized training data?
- Cost and latency: Can it run reliably at scale?

Because benchmark reporting is fragmented, Stanford HAI highlights that responsible AI evaluations for LLMs remain insufficiently standardized across leading developers.

## Footnotes

1. [The 2025 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2025-ai-index-report) - Reports falling inference costs, improving open-weight models, and broader accessibility trends. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-7-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-7-3)
 
2. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-4-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-4-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-4-5) [↩6](https://coursify.hasanraiyan.me/#user-content-fnref-4-6)
 
3. [The 2024 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2024-ai-index-report) - Key 2024 statistics on generative AI investment, model releases, costs, and evaluation gaps. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-5-2)
 

### Key Concepts and Clarifications

What makes generative AI different from traditional predictive AI?

Are large language models the same as generative AI?

Do larger models always perform better?

Does retrieval remove hallucinations completely?

Why is data provenance important?

### 

Selected Generative AI Market and Model Trends

Illustrative values drawn from Stanford HAI AI Index 2024.

### Risks, limitations, and governance

Generative AI systems can be highly fluent while remaining unreliable. NIST's Generative AI Profile identifies confabulation, dangerous or hateful content, privacy risks, intellectual property risks, and abusive synthetic media among the major concerns. This means quality must be understood as multi-dimensional: a polished answer is not necessarily a correct or safe answer.

#### Major risk classes

1. **Factual unreliability and confabulation** 
 Models may produce unsupported statements confidently, leading users to trust false outputs.
 
2. **Bias and stereotyping** 
 If training data encodes social imbalances, outputs may reproduce or amplify them.
 
3. **Privacy leakage** 
 Training on sensitive data can lead to unauthorized disclosure, memorization, or imitation of identity, voice, or likeness.
 
4. **Intellectual property disputes** 
 NIST notes unresolved legal debates around copyrighted training data and generated outputs that may reproduce protected material.
 
5. **Deepfake and abuse potential** 
 Generative systems can facilitate misleading synthetic media, impersonation, harassment, or harmful content creation.
 
6. **Operational and governance weaknesses** 
 Limited transparency, weak evaluation, and insufficient monitoring can make failures difficult to detect or remediate.[2]()
 

A governance-oriented perspective treats these issues as system risks rather than model-only flaws. Controls may include dataset review, access management, red-teaming, output filters, provenance records, usage restrictions, and human escalation pathways.

## Footnotes

1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-4-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-4-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-4-5) [↩6](https://coursify.hasanraiyan.me/#user-content-fnref-4-6) [↩7](https://coursify.hasanraiyan.me/#user-content-fnref-4-7) [↩8](https://coursify.hasanraiyan.me/#user-content-fnref-4-8)
 
2. [The 2024 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2024-ai-index-report) - Key 2024 statistics on generative AI investment, model releases, costs, and evaluation gaps. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

#### Do not equate fluency with truth

The most dangerous generative outputs are often not obviously wrong; they can be persuasive, coherent, and still false. High-stakes decisions require verification and accountable review.

## Footnotes

1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 

more...

Text Generation

Image GenerationEnterprise Deployment

Typical tasks include summarization, drafting, translation, coding support, and conversational assistance. The dominant architecture is the transformer, optimized for large-scale sequence modeling with self-attention.

## Footnotes

1. [Generative AI and the Foundation Model Era: A Comprehensive Review](https://www.mdpi.com/2504-2289/10/3/94) - Survey of architectures, training, evaluation, and applications across transformers, diffusion, and multimodal models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 

### Best practices for responsible use

Organizations adopting generative AI should combine technical, legal, and organizational controls. NIST's framework approach emphasizes mapping, measuring, managing, and governing risk across the system lifecycle rather than only testing outputs at the end.

Recommended practices include:

- Define acceptable-use boundaries before deployment.
- Use data minimization and provenance documentation where possible.
- Ground outputs with retrieval or verified knowledge bases for factual tasks.[2]()
- Establish human oversight for sensitive decisions in health, law, finance, hiring, and public communication.
- Benchmark both quality and safety using repeatable test sets.
- Monitor model behavior continuously because threats and failure modes evolve over time.

For learners, one of the most important conceptual shifts is understanding that generative AI is a socio-technical system. The model is only one layer; data, interfaces, incentives, policies, users, and monitoring all shape real-world outcomes.[2]()

## Footnotes

1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-4-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-4-4) [↩5](https://coursify.hasanraiyan.me/#user-content-fnref-4-5) [↩6](https://coursify.hasanraiyan.me/#user-content-fnref-4-6) [↩7](https://coursify.hasanraiyan.me/#user-content-fnref-4-7)
 
2. [The 2025 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2025-ai-index-report) - Reports falling inference costs, improving open-weight models, and broader accessibility trends. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 
3. [The 2024 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2024-ai-index-report) - Key 2024 statistics on generative AI investment, model releases, costs, and evaluation gaps. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-5-2)
 

### A Responsible Workflow for Using Generative AI in Practice

1. 1
 
 Step 1
 
 Define the task and risk level
 
 Separate low-risk creativity tasks from high-stakes tasks involving legal, medical, financial, educational, or identity-sensitive decisions.
 
 ## Footnotes
 
 1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
2. 2
 
 Step 2
 
 Choose the right model and architecture
 
 Select among closed, open, small, large, text-only, or multimodal systems based on required quality, privacy, latency, and governance needs.[2]()
 
 ## Footnotes
 
 1. [The 2024 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2024-ai-index-report) - Key 2024 statistics on generative AI investment, model releases, costs, and evaluation gaps. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 2. [Stanford's 2024 AI Index Tracks Generative AI and More - IEEE Spectrum](https://spectrum.ieee.org/ai-index-2024) - Summary of open versus closed model trends and model release patterns discussed in the AI Index. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-6)
 
 
3. 3
 
 Step 3
 
 Ground the system with trusted context
 
 Use curated enterprise documents, retrieval pipelines, or approved datasets to improve factual support and reduce unsupported improvisation.[2]()
 
 ## Footnotes
 
 1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 2. [The 2025 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2025-ai-index-report) - Reports falling inference costs, improving open-weight models, and broader accessibility trends. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 
 
4. 4
 
 Step 4
 
 Apply policy and safety layers
 
 Add filtering, rate limits, content moderation, and escalation paths for harmful, abusive, or regulated outputs.
 
 ## Footnotes
 
 1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 
5. 5
 
 Step 5
 
 Evaluate with realistic scenarios
 
 Test not only average performance but edge cases, adversarial prompts, demographic harms, and failure recovery procedures.[2]()
 
 ## Footnotes
 
 1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 2. [The 2024 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2024-ai-index-report) - Key 2024 statistics on generative AI investment, model releases, costs, and evaluation gaps. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
 
6. 6
 
 Step 6
 
 Deploy with monitoring and feedback
 
 Track incidents, user complaints, quality regressions, and cost signals; then update prompts, retrieval sources, and controls as usage evolves.
 
 ## Footnotes
 
 1. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 
 

### Future directions

The field is moving toward more efficient models, stronger multimodal integration, better tool use, and more formal governance. Stanford's 2025 AI Index highlights a dramatic decline in inference cost for systems at GPT-3.5-level capability and a narrowing performance gap between open-weight and closed models on some benchmarks. These trends suggest broader access to advanced capabilities, but they also imply that safety and governance must scale alongside accessibility.

In research and practice, several frontiers are especially important:

- Better evaluation standards for reliability and responsibility.
- Smaller, specialized models for cheaper deployment.
- Improved provenance, watermarking, and traceability for synthetic media.
- More robust safeguards against prompt injection, abuse, and privacy leakage.
- Domain-specific systems that combine generation with verified tools and expert workflows.[2]()

Ultimately, generative AI is best understood not as magic but as large-scale probabilistic modeling plus engineering, data curation, and governance. Its value depends on aligning capability with trustworthy use.[2]()

## Footnotes

1. [The 2025 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2025-ai-index-report) - Reports falling inference costs, improving open-weight models, and broader accessibility trends. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-7-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-7-3)
 
2. [The 2024 AI Index Report | Stanford HAI](https://hai.stanford.edu/ai-index/2024-ai-index-report) - Key 2024 statistics on generative AI investment, model releases, costs, and evaluation gaps. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 
3. [Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf) - NIST guidance on generative AI risks including confabulation, privacy, IP, and abusive synthetic content. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-4-2) [↩3](https://coursify.hasanraiyan.me/#user-content-fnref-4-3) [↩4](https://coursify.hasanraiyan.me/#user-content-fnref-4-4)
 
4. [Generative AI and the Foundation Model Era: A Comprehensive Review](https://www.mdpi.com/2504-2289/10/3/94) - Survey of architectures, training, evaluation, and applications across transformers, diffusion, and multimodal models. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 

### Knowledge Check

Question 1 of 5

Q1Single choice

Which model family is most strongly associated with modern large language models?

Transformers

K-means clustering

Decision trees

Linear regression

BackNext

[![Coursify logo](https://coursify.hasanraiyan.me/_next/image?url=%2Fimages%2Fapps%2Fcoursify.png&w=48&q=75)Browse all research articles](https://coursify.hasanraiyan.me/research)