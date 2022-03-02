# Enhanced depth map compression via cross-modal prior
**Supplemental Materials** for "END-TO-END DEPTH MAP COMPRESSION FRAMEWORK VIA RGB-TO-DEPTH STRUCTURE PRIORS LEARNING"


## Details of network architecture
Our proposed framework is implemented based on *mbt2018* and *cheng2020-attn* provided by [CompressAI](https://github.com/InterDigitalInc/CompressAI). We do not modify the model parameters of backbone and entropy model except changing the number of input channel to fit the input and output depth map tensor and concated feature maps.

**Note:**
*Convolutional layers are specified with the “Conv” prefix followed by number of output channels, the kernel size and downsampling stride.*

*mbt2018-based:*

<!-- <img src="https://github.com/mingfaichen/r2dcompression/blob/main/architecture/mtb2018.jpg" /> -->
![mbt2018](https://github.com/mingfaichen/r2dcompression/blob/main/architecture/mtb2018.jpg)

*cheng2020-attn-based:*

*(The GDN layer is not shown at figure. For details please check [cheng2020-attn](https://github.com/InterDigitalInc/CompressAI/blob/master/compressai/models/waseda.py).)*

<img src="https://github.com/mingfaichen/r2dcompression/blob/main/architecture/cheng2020-attn.jpg" />
<!-- ![cheng2020-attn](https://github.com/mingfaichen/r2dcompression/blob/main/architecture/cheng2020-attn.jpg) -->

*Proposed SPF module:*

*(For details of ESA block please check [ESA](https://github.com/njulj/RFANet/blob/master/ESA.py))*

<img src="https://github.com/mingfaichen/r2dcompression/blob/main/architecture/SPF.jpg" width="150px" />
<!-- ![SPF](https://github.com/mingfaichen/r2dcompression/blob/main/architecture/SPF.jpg){:height="50%" width="50%"} -->

## Experimental results
To better illustrate the capability of cross-modal redundancy extraction of our proposed SPF module. We conducted experiments with two quality levels of RGB images, defined as *High*  and *Low*. The corresponding PSNR and bpp of different levels for both backbones are shown at the following table:

*mbt2018*:

<img src="https://github.com/mingfaichen/r2dcompression/blob/main/result/Joint_Color.jpg" width="150px" />

*cheng2020-attn*:

<img src="https://github.com/mingfaichen/r2dcompression/blob/main/result/Cheng_Color.jpg" width="150px" />

The experimental results are shown below:

**Note：** *Depth maps compressed by BPG and VVC cannot generate proper nomarl map because of the degradation caused by the quantization from 16 bit to 8 bit.*

*High*
<img src="https://github.com/mingfaichen/r2dcompression/blob/main/result/curve_high.jpg" />
<img src="https://github.com/mingfaichen/r2dcompression/blob/main/result/visualization_high.jpg" />

*Low*
<img src="https://github.com/mingfaichen/r2dcompression/blob/main/result/curve_low.jpg" />
