# What Happens During One Training Iteration?

> **Note:** This page describes a single training iteration using **Data Parallelism (Distributed Data Parallel, DDP)**. In this training strategy, each GPU stores a complete copy of the model but processes a different mini-batch of data. During the backward pass, every GPU computes its own gradients. Before the model weights are updated, the gradients are synchronized across all GPUs using communication operations such as **All-Reduce**. This ensures that every GPU applies the same parameter update and keeps all model replicas identical.

## 1. Forward Pass

- **Purpose:** Generate the model's prediction from the input.
- **Main operations:** Matrix multiplication, attention, normalization, activation functions, and softmax.
- **Output:** Predicted token probabilities (or logits).

## 2. Loss Computation

- **Purpose:** Compare the model's prediction with the target and measure the prediction error.
- **Main operations:** Loss function (e.g., Cross-Entropy Loss).
- **Output:** Loss value.

## 3. Backward Pass

- **Purpose:** Compute the gradient of the loss with respect to every trainable parameter.
- **Main operations:** Derivatives, the chain rule, matrix multiplication, and addition.
- **Output:** Gradients.

## 4. Gradient Synchronization (Distributed Training)

- **Purpose:** Synchronize the gradients computed on each GPU.
- **Why is it needed?** To ensure that every GPU updates the model using the same gradients, keeping all model replicas identical.
- **Main operations:** All-Reduce, Reduce-Scatter, and All-Gather (depending on the distributed training strategy).
- **Output:** Synchronized gradients.

## 5. Optimizer Step

- **Purpose:** Update the model weights using the synchronized gradients.
- **Main operations:** Multiplication, addition/subtraction, and (for optimizers such as Adam) division and square root.
- **Output:** Updated model weights.

## Key Insight

The **backward pass** computes the gradients, while the **optimizer** uses those gradients to update the model weights. In Data Parallelism, gradients must be synchronized across all GPUs before the optimizer performs the weight update. This ensures that every GPU applies the same update and keeps an identical copy of the model throughout training.

## Key Concepts

| Concept | Description |
|----------|-------------|
| **Forward Pass** | Computes the model's predictions from the input using operations such as matrix multiplication, attention, and activation functions. |
| **Loss** | Measures the difference between the model's prediction and the expected target using a loss function such as Cross-Entropy. |
| **Gradient** | Indicates how each trainable parameter should change to reduce the loss. Gradients are computed during the backward pass using derivatives and the chain rule. |
| **Gradient Synchronization** | In Data Parallelism, gradients computed on different GPUs are synchronized (typically using All-Reduce) so that every GPU has the same gradients before updating the model. |
| **Optimizer** | Uses the synchronized gradients to update the model parameters. Common optimizers include SGD, Adam, and AdamW. |
