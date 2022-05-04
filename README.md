# Learnable-Quantization-for-Covid-Lungs-CT-segmentation

We implemented a learnable physical quantization layer to simulate the quantizers in CT scanners.

In the physical layer there is an array called choices of the same size of the input images, which are either 0 or 1. When it's 1, the corresponding pixel is quantized based on the following formula.

X_q = floor(X/2^k) * 2^k

The "choices" are discrete parameters since they are either 0 or 1. To train the neural network, we must replace them with continuous ones. To this end, we sample the "choices" from a Bernoulli distribution. Then, the trainable parameters become the probability array(self.W) of the Bernoulli distribution. With a higher probability, it tends to quantize the corresponding pixel more likely.

We can see from the results that the probability array resembles a lung. Along the edge, the network tends to quantize on one side and doesn't quantize on the other side. In this way, the contarst will be improved, which leads to better performance.

The result can help guide the design of a adaptable quantizer in CT scanners. We can get images with higher contrast in important areas while reduce the storage room for images.

The project is done with Libo Zhang, Sihan Lyu and Sizhe Kuang.
