# Hivemind Networks

Neural network weights for the Hivemind chess engine.

## Overview

This repository contains trained neural network models used for position evaluation and move prediction in the Hivemind chess engine.

## Latest Model

| Metric | Value |
|--------|-------|
| **Version** | 3.0 |
| **Loss** | 0.97878 |
| **Policy Accuracy** | 68.3% |
| **Epoch** | 224 |

## Repository Structure

```
hivemind-networks/
├── weights/                    # Production-ready model weights
│   ├── *.onnx                 # ONNX format for inference
│   └── *.tar                  # PyTorch checkpoint
├── checkpoints/               # Training checkpoints
└── README.md
```

## Model Formats

- **ONNX** (`.onnx`): Optimized for inference, cross-platform compatibility
- **PyTorch Checkpoint** (`.tar`): Full training state for fine-tuning or resuming training

## Usage

### ONNX Inference

```python
import onnxruntime as ort

session = ort.InferenceSession("weights/model-0.97878-0.683-0224-v3.0.onnx")
# Run inference with your input tensor
```

### Loading PyTorch Checkpoint

```python
import torch

checkpoint = torch.load("weights/model-0.97878-0.683-0224.tar")
model.load_state_dict(checkpoint['model_state_dict'])
```

## File Naming Convention

Model files follow the pattern: `model-{loss}-{accuracy}-{epoch}-v{version}.{ext}`

- **loss**: Training loss value
- **accuracy**: Validation policy accuracy
- **epoch**: Training epoch number
- **version**: Model architecture version
