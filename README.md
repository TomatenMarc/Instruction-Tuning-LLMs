# 🤖 Large Language Models

A practical guide to understanding LLM components, tuning strategies, naming conventions, and best libraries.

---

## 📚 Vocabulary: Core Concepts

### 🧠 1. Language Models vs. Large Language Models (LLMs)

- **Language Model (LM):**  
  A system that learns language patterns and calculates probabilities of word sequences. Useful for generation, classification, and translation.

- **Large Language Model (LLM):**  
  A language model with billions of parameters, trained on massive text datasets. Powers chatbots, translators, and creative tools.  
  👉 Examples: **GPT-4**, **LLaMA**, **PaLM**, **T5**, **BERT**.

---

### 🔁 2. Model Architectures

- **🟦 Encoder**  
  Extracts context from input (e.g., BERT). Ideal for classification, extraction, and comprehension.

- **🟥 Decoder**  
  Generates text one token at a time (e.g., GPT, LLaMA). Suited for creative/generative tasks.

- **🟪 Encoder-Decoder**  
  Combines both: encodes input → decodes output (e.g., T5, BART). Best for translation, summarization.

---

### 🛠️ 3. Fine-Tuning Strategies

- **🎯 Classic Heads**  
  Add a task-specific "head" (layer) to a pretrained model. Supports sequence classification, QA, etc.

- **🧩 Adapters (PEFT)**  
  Inject small task-specific modules into the model (e.g., LoRA, Bottleneck). Efficient and reusable.

- **📝 Prompt-Tuning**  
  Keep weights frozen—only tune the input prompts. Lightweight, fast, and flexible.

---

### 🧠 4. In-Context Learning Methods

- **📄 In-Context Learning**  
  Solves tasks using only examples/instructions in the prompt. No parameter updates.

- **⚡ Shot Learning**
  - **Zero-Shot**: No examples  
  - **One-Shot**: One example  
  - **Few-Shot**: A few examples

- **🔍 RAG (Retrieval-Augmented Generation)**  
  Combines LLMs with external search to enhance factual output.

---

## ⚖️ Effort Comparison

> Based on practical usage experience

| Method              | 💻 Compute | 💾 Memory | 📊 Data | 🔧 Flexibility | 🚀 Performance | 🟢 Use When... |
|---------------------|------------|-----------|--------|----------------|----------------|----------------|
| Full Fine-Tuning    | 🔴         | 🔴        | 🔴     | 🔴             | 🔴             | Maximum control is needed. |
| LoRA                | 🟡         | 🟢        | 🟡     | 🟡             | 🟡             | Efficient + modular.       |
| QLoRA               | 🟢         | 🟢        | 🟡     | 🟡             | 🟡             | Consumer GPUs with low VRAM. |
| Adapter Tuning      | 🟡         | 🟡        | 🟡     | 🟢             | 🟡             | Modular, reusable tasks.  |
| Prompt Tuning       | 🟢         | 🟢        | 🟢     | 🔴             | 🟢             | No model updates needed.  |
| RAG                 | 🟢         | 🟢        | 🟢     | 🟡             | 🟡             | Real-time knowledge access. |

---

## 🧰 LLM Tools & Libraries

| 🔧 Tool / Framework                                                                | 🌟 Purpose                                        | 🧠 Best For                                       | 💾 Memory | ⚡ Speed | 📈 Scale | 🧪 Ease |
|------------------------------------------------------------------------------------|--------------------------------------------------|--------------------------------------------------|----------|---------|----------|---------|
| [🤗 Transformers](https://huggingface.co/docs/transformers/index)                 | Load/train/tokenize LLMs                         | BERT, GPT, T5, LLaMA                             | 🟡       | 🟡      | 🟡       | 🟢      |
| [🧬 SentenceTransformers](https://www.sbert.net/)                                 | Text/Sentence embeddings                         | Similarity, clustering, retrieval                | 🟢       | 🟢      | 🟢       | 🟢      |
| [⚡ SimpleTransformers](https://github.com/ThilinaRajapakse/simpletransformers)   | Easy fine-tuning                                 | BERT, RoBERTa, GPT-2                             | 🟢       | 🟢      | ⚪       | 🟢      |
| [🧩 AdapterHub](https://adapterhub.ml/)                                           | Adapter-based tuning                             | LoRA, bottleneck adapters                        | 🟢       | 🟢      | 🟡       | 🟢      |
| [⚙️ PEFT (HF)](https://huggingface.co/docs/peft/index)                           | Parameter-efficient tuning                       | LoRA, BitFit, Adapter                            | 🟢       | 🟢      | 🟡       | 🟢      |
| [🌐 OpenAI API](https://platform.openai.com/docs/)                                | Hosted GPT access                                | Chat, generation, tools                          | ⚪       | 🟢      | 🟢       | 🟢      |
| [🔗 LangChain](https://python.langchain.com/docs/)                                | Chain LLM workflows                              | RAG, tools, agents                               | 🟢       | 🟡      | 🟢       | 🟡      |
| [🔍 ChromaDB](https://docs.trychroma.com/)                                        | Vector DB + semantic search                      | Retrieval-based LLMs                             | 🟢       | 🟢      | 🟡       | 🟢      |
| [🚀 DeepSpeed](https://www.deepspeed.ai/)                                         | Efficient large-model training                   | Scaling to large hardware                        | 🟢       | 🟢      | 🟢       | ⚪      |
| [📦 BitsAndBytes](https://huggingface.co/docs/transformers/main/en/main_classes/quantization) | Quantized model inference             | Memory-constrained LLM usage                     | 🟢       | 🟢      | 🟡       | ⚪      |
| [🦥 Unsloth](https://github.com/unslothai/unsloth)                                | Fast LoRA/QLoRA training                         | Consumer GPUs                                    | 🟢       | 🟢      | 🟢       | 🟢      |
| [💨 vLLM](https://github.com/vllm-project/vllm)                                   | Optimized inference                              | Speed & memory efficiency                        | 🟢       | 🟢      | 🟢       | 🟡      |

---

## 🧩 Bonus: Understanding LLM Naming Conventions

### 🏷️ Common Tokens in Model Names

| 🔤 Term     | 🔎 Meaning                             |
|------------|-----------------------------------------|
| `Base`     | Pretrained only                        |
| `Instruct` | Fine-tuned for instructions            |
| `Chat`     | Optimized for conversation             |
| `Code`     | Code generation model                  |
| `RLHF`     | Aligned via human feedback             |
| `7B`, `13B`| Model size (in billions of params)     |
| `hf`       | Hugging Face format                    |

### 📌 Examples
- `Meta-Llama-3-8B` → Pretrained base model, 8B parameters  
- `Meta-Llama-3-8B-Instruct` → Instruction-tuned  
- `Llama-2-13B-Chat-hf` → Chat model in HF format  
- `Mixtral-8x7B` → Mixture of Experts: 8x 7B models

---

## 📝 Key Papers on LLMs

### 🔹 **Foundation Models (Base Models)**
- [LLaMA: Open and Efficient Foundation Language Models](https://arxiv.org/abs/2302.13971)  
  *Hugo Touvron, Thibaut Lavril, Gautier Izacard, et al.*  
  *Describes the training of LLaMA models and their efficiency compared to larger-scale LLMs.*

- [Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361)  
  *Jared Kaplan, Sam McCandlish, Tom Henighan, et al.*  
  *Explores how dataset size, compute, and model parameters impact LLM performance.*

### 🔹 **Instruction-Tuned Models (Fine-Tuning & Alignment)**
- [Training Language Models to Follow Instructions with Human Feedback](https://arxiv.org/abs/2203.02155)  
  *Long Ouyang, Jeff Wu, Xu Jiang, et al.*  
  *Explains how fine-tuning with RLHF improves instruction-following capabilities in LLMs.*

- [Fine-tuning Language Models from Human Preferences](https://arxiv.org/abs/1909.08593)  
  *Diederik P. Kingma, Jeff Wu, Alec Radford, et al.*  
  *Presents early research on aligning models with human preferences using supervised fine-tuning.*

### 🔹 **RLHF & Chat Optimization**
- [Deep Reinforcement Learning from Human Preferences](https://arxiv.org/abs/1706.03741)  
  *Paul F. Christiano, Jan Leike, Tom B. Brown, et al.*  
  *Introduces reinforcement learning from human feedback (RLHF) as a technique to fine-tune LLMs.*

- [Learning to Summarize with Human Feedback](https://arxiv.org/abs/2009.01325)  
  *Nisan Stiennon, Long Ouyang, Jeffrey Wu, et al.*  
  *Applies RLHF to text summarization, demonstrating improved alignment with human preferences.*

- [Improving Alignment of Dialogue Agents via Targeted Human Judgments](https://arxiv.org/abs/2209.14375)  
  *Amelia Glaese, Nat McAleese, Maja Trębacz, et al.*  
  *Discusses methods to align chatbot responses using human judgments.*

## 🧩🧩 Extra Bonus: Cheat-Sheet for LLMs
<div align="center">
  <img src="https://github.com/TomatenMarc/public-images/raw/main/Cheat-Sheet-LLMs.svg" alt="Cheat-Sheet-LLMs" width="100%">
</div>
