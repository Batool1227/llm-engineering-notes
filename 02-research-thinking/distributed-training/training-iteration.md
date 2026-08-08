# What Happens During One Training Iteration?

## 1. Forward Pass

- Purpose:
- Main operations:
- Output:

## 2. Loss Computation

- Purpose:
- Main operations:
- Output:

## 3. Backward Pass

- Purpose:
- Main operations:
- Output:

## 4. Gradient Synchronization (Distributed Training)

- Purpose:
- Why is it needed?
- Main operations:

## 5. Optimizer Step

- Purpose:
- Main operations:
- Output:

## Key Insight

The backward pass computes gradients, while the optimizer uses those gradients to update the model weights. In distributed training, gradients must be synchronized before the optimizer updates the weights so that every GPU maintains the same model.
