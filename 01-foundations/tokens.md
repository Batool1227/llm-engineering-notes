# What are Tokens?

A **token** is the smallest unit of text that a Large Language Model (LLM) processes. A token is not always a complete word—it can be a whole word, part of a word, a punctuation mark, or even a single character, depending on the tokenizer used by the model.

For example:

| Text | Possible Tokens |
|------|------------------|
| `Hello world!` | `Hello`, `world`, `!` |
| `unbelievable` | `un`, `believ`, `able` |
| `GPT-4` | `GPT`, `-`, `4` |

> **Note:** Different models use different tokenizers, so the same text may be split into different tokens.

---

# Why do LLMs use Tokens?

LLMs are neural networks, and neural networks operate on numerical data rather than raw text. Before text can be processed by the model, it must be converted into numbers. This is done using a tokenizer, which splits the text into smaller units called **tokens** and assigns each token a unique numerical ID. These token IDs are then transformed into embedding vectors, allowing the model to process the text during training and inference.

```text
                Raw Text
                    │
                    ▼
              ┌───────────┐
              │ Tokenizer │
              └───────────┘
                    │
                    ▼
         Token IDs (e.g., 15496, 995)
                    │
                    ▼
            Embedding Layer
                    │
                    ▼
          Embedding Vectors
                    │
                    ▼
                  LLM
```

---

# Why do Tokens Matter?

Tokens determine how text is represented before it reaches the model. Every LLM has a maximum context length, which defines the maximum number of tokens it can process in a single request. If the input exceeds this limit, the model cannot process all of the tokens, and the request may be rejected or the input may be truncated. Understanding tokens also helps engineers estimate context usage, optimize prompts, and manage inference costs when building LLM applications.

```text
                 Context Window (Example: 8K Tokens)

┌────────────────────────────────────────────────────────────┐
│                                                            │
│  System Prompt                                             │
│  User Prompt                                               │
│  Chat History                                              │
│  Retrieved Documents                                       │
│  Current Question                                          │
│  Generated Response                                        │
│                                                            │
└────────────────────────────────────────────────────────────┘
                           ▲
                           │
          Maximum number of tokens the model
            can process in a single request
```

---

# Key Takeaways

- LLMs cannot process raw text directly; they process numerical representations.
- A tokenizer splits text into tokens and assigns each token a unique numerical ID.
- Token IDs are converted into embedding vectors before entering the model.
- Every LLM has a maximum context length measured in tokens.
- Tokens affect context usage, inference efficiency, and API cost.

## References

1. Vaswani, A., et al. (2017). *Attention Is All You Need*. NeurIPS.
   https://arxiv.org/abs/1706.03762

2. Sennrich, R., Haddow, B., & Birch, A. (2016). *Neural Machine Translation of Rare Words with Subword Units*.
   https://arxiv.org/abs/1508.07909

3. OpenAI. *What are tokens and how to count them?*
   https://help.openai.com/en/articles/4936856-what-are-tokens-and-how-to-count-them

4. Hugging Face. *Tokenizer Summary*.
   https://huggingface.co/docs/transformers/tokenizer_summary

5. Hugging Face Course. *Chapter 2: Tokenizers*.
   https://huggingface.co/course/chapter2
