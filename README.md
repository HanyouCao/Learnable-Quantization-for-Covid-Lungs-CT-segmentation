# Learnable-Quantization-for-Covid-Lungs-CT-segmentation

We implemented a learnable physical quantization layer to simulate the quantizers in CT scanners.

In the physical layer there is an array called choices of the same size of the input images, which are either 0 or 1. When it's 1, the corresponding pixel is quantized based on the following formula.

$$X_{qntz} = floor(X/2^k) \times 2^k,$$
