## Questions

#### Initialiazation

In the CNNs lesson, they claim 

    The default PyTorch behavior isn't necessarily optimal and you can often improve performance by using something more custom, but we'll follow it for today because it's simple and works decently well.

Which is okay, but I haven't found a good explanation of what is optimal initialization (or why we sometimes just don't do it). Schemes I'm aware of:

- Choose weights and biases from a uniform or normal distribution. This is bad. Causes extreme values on the forward pass and vanishing/exploding gradients on the backward pass.
- Xavier initialization which normalizes by an average of the input and output dims and doesn't adjust for the non-linearity
- Kaiming/He initialization which normalize by the size of the input dim or the output dim and adjusts with a gain factor specific to the non-linearity

Pytorch seems to have definitions and apis for these that are inconsistent, which is dumb. They also have other schemes which may be useful in some specialized settings.

*Q: What is the default?* Seems like default samples uniformly from $[-1/\sqrt{N_{in}}, 1/\sqrt{N_{in}}]$ so it's really not that smart.