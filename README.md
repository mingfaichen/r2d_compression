# Enhanced depth map compression via cross-modal prior
**Supplemental Materials** for "END-TO-END DEPTH MAP COMPRESSION FRAMEWORK VIA RGB-TO-DEPTH STRUCTURE PRIORS LEARNING"


## Details of network architecture
Our proposed framework is implemented based on *mbt2018* and *cheng2020-attn* provided by CompressAI. We do not modify the model parameters of backbone and entropy model except changing the number of input channel to suit depth map and concated feature maps.

**Note:**
*Convolutional layers are specified with the “Conv” prefix followed by number of output channels, the kernel size and downsampling stride.*

*mbt2018-based:*

<!-- <img src="https://github.com/mingfaichen/r2dcompression/blob/main/architecture/mtb2018.jpg" /> -->
![mbt2018](https://github.com/mingfaichen/r2dcompression/blob/main/architecture/mtb2018.jpg)

*cheng2020-attn-based:*

<img src="https://github.com/mingfaichen/r2dcompression/blob/main/architecture/cheng2020-attn.jpg" />
<!-- ![cheng2020-attn](https://github.com/mingfaichen/r2dcompression/blob/main/architecture/cheng2020-attn.jpg) -->

*Proposed SPF module:*

<img src="https://github.com/mingfaichen/r2dcompression/blob/main/architecture/SPF.jpg" width="150px" />
<!-- ![SPF](https://github.com/mingfaichen/r2dcompression/blob/main/architecture/SPF.jpg){:height="50%" width="50%"} -->
