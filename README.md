# Enhanced depth map compression via cross-modal prior
**Supplemental Materials** for "END-TO-END DEPTH MAP COMPRESSION FRAMEWORK VIA RGB-TO-DEPTH STRUCTURE PRIORS LEARNING"


## Details of network architecture
Our proposed framework is implemented based on *mbt2018* and *cheng2020-attn* provided by [CompressAI](https://github.com/InterDigitalInc/CompressAI). We do not modify the architecture of transform and entropy model except changing the number of input channels to fit the input and output depth map tensor and concated feature maps. The detail architecture of our proposed framework are illustracted below:

**Note:**
*Convolutional layers are specified with the “Conv” prefix followed by number of output channels, the kernel size and sampling stride.*

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

## Experimental setting and results
The compression performance of our proposed framework depends on the extracted cross-modal structure prior, which may be affectd by the distortion caused by RGB compression at low bit-rate. To better illustrate the roboustness of our proposed SPF module, we trained our enhanced depth map compression framework with two bit-rate settings of RGB compression, defined as *High*  and *Low*. The corresponding PSNR and bpp of different RGB settings for both *mbt2018* and *cheng2020-attn* backbones are shown at the following table:

*mbt2018*:

<img src="https://github.com/mingfaichen/r2dcompression/blob/main/result/Joint_Color.jpg" width="150px" />

*cheng2020-attn*:

<img src="https://github.com/mingfaichen/r2dcompression/blob/main/result/Cheng_Color.jpg" width="150px" />

The experimental results are shown below:

**Note1：** *Depth maps compressed by BPG and VVC cannot generate proper nomarl map because of the degradation caused by the quantization from 16 bit to 8 bit.*

**Note2：** *All the comparison methods are conducted with the direct compression pattern, which means that the compression of RGB image and depth map are independent and ignore the reduction of cross-modal redundancy within RGB-D. To compare the performance more fairly, the RGB-D segmentation evaluation are conducted with **High** and **Low** setting of *mbt2018*, respectively.*

*High*
<img src="https://github.com/mingfaichen/r2dcompression/blob/main/result/curve_high.jpg" />
<img src="https://github.com/mingfaichen/r2dcompression/blob/main/result/visualization_high.jpg" />

*Low*
<img src="https://github.com/mingfaichen/r2dcompression/blob/main/result/curve_low.jpg" />
<img src="https://github.com/mingfaichen/r2dcompression/blob/main/result/visualization_low.jpg" />

## Test on SUN-RGBD dataset
To verify the generalization of our method, we have made a test on the SUN-RGBD dataset, which contains the RGB-D data collected from four kinds of sensors, using models with setting *mbt2018-High* trained on the NYUv2 dataset. The inference results are shown below:
<img src="https://github.com/mingfaichen/r2dcompression/blob/main/result/SUNRGBD_inference.jpg" />
