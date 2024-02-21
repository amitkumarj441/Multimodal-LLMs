**Mathematical Description of Conditional Denoising Diffusion Model**

The conditional denoising diffusion model (CDDM) is a generative model that learns to map from a source image domain to a target image domain. The model is trained by first corrupting a source image with noise, and then learning to denoise the image back to the original source image. The denoising process is performed in a series of steps, where each step removes a small amount of noise from the image.

The CDDM is defined by two probability distributions:

* The forward diffusion process, which describes how noise is added to an image.
* The reverse denoising process, which describes how noise is removed from an image.

**Forward Diffusion Process**

The forward diffusion process is defined by the following probability distribution:

```
q(y_{1:T} | y_0) = \prod_{t=1}^T q(y_t | y_{t-1})
```

where:

* $y_{1:T}$ is the sequence of noisy images.
* $y_0$ is the original source image.
* $q(y_t | y_{t-1})$ is the probability distribution of the noise added at step $t$.

The noise added at each step is typically Gaussian noise with a variance that is proportional to the step number.

**Reverse Denoising Process**

The reverse denoising process is defined by the following probability distribution:

```
p_\theta(y_{0:T} | x) = p(y_T) \prod_{t=1}^T p_\theta(y_{t-1} | y_t, x)
```

where:

* $x$ is the target image.
* $p_\theta(y_{t-1} | y_t, x)$ is the probability distribution of the noise removed at step $t$.

The noise removed at each step is typically Gaussian noise with a variance that is proportional to the step number.

**Training**

The CDDM is trained by maximizing the following objective function:

```
L(\theta) = \mathbb{E}_{x \sim p(x)} \left[ \log p_\theta(y_{0:T} | x) \right]
```

where:

* $p(x)$ is the distribution of source images.

The objective function is maximized using stochastic gradient descent.

**Inference**

The CDDM can be used to generate images from the target image domain by sampling from the following distribution:

```
p_\theta(x) = \int p_\theta(y_{0:T} | x) dy_{0:T}
```

where:

* $y_{0:T}$ is the sequence of noisy images.

The integral is typically approximated using Monte Carlo methods.

**Applications**

The CDDM has been used for a variety of applications, including:

* Image super-resolution.
* Image inpainting.
* Image restoration.

Note: The CDDM is a powerful generative model that can be used for a variety of applications. The model is easy to train and can be used to generate high-quality images.

**References**

* C. Saharia, J. Ho, W. Chan, T. Salimans, D. J. Fleet, and M. Norouzi, “Image Super-Resolution via Iterative Refinement,” IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. 45, no. 4, pp. 4713–4726, 2023, doi: 10.1109/TPAMI.2022.3204461.: [https://ieeexplore.ieee.org/document/9542322](https://ieeexplore.ieee.org/document/9542322)
