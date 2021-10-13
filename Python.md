# Python

## Setting up the python environment

1. Pipfile
2. PYPI mirrors

## PyTorch 

### Resources

### FAQ

* High training variance at the end of epoch.
  * Symptoms: loss spike, divergence, trained to NaN.
  * Potential Causes:
    * Did you forget to call `model.train()` after using `model.eval()` for evaluation?
    * The training dataloader instantiated with `torch.utils.data.DataLoader`
      should use the argument `drop_last=True` to ensure the last batch is not too small.

## Experiment Logging

* Tensorboard
  * Tutorial: https://pytorch.org/tutorials/intermediate/tensorboard_tutorial.html
* Weights and Biases
  * https://wandb.ai
