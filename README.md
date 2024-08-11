## Summary

### Introduction

We perform a video interpolation task - provided beginning and end frames or clips of a video, we provide context-appropriate material for the middle of a video. We aim to do this by training a combination of a VQ-VAE and a Transformer model with ample context (31 frames) and attempting to predict missing frames in a lower context (2 or 6 frame) setting. Using a modified version of the Vimeo90k dataset, our model is able to cohesively interpolate video for provided inputs, approaching though not currently meeting industry levels, given time and compute constraints.

### Dataset

We used webscraping and image processing techniques to create a version of this dataset with 31 frames of context - our model is trained to predict all even indexed frames from a 31-frame sequence. We tested this model's transfer-ability by predicting missing frames on standardized Vimeo90k septuplet datasets. Our ablations focused on finding the ideal transfer method.

### Methods

We begin with sequences of video frames and quantize them using a VQ-VAE. We apply a mask to remove the frames being predicted and pass the quantized frames through a video transformer and generate quantized predictions of the most likely masked frames. Finally, we reconstruct the masked frames from our quantizations.
                                  
## Example
### Original
![Original Frames](https://github.com/TBennur/GenAIFinalProject/blob/main/images/final_original_ex.png "Original Frames")

### Reconstruction
![Reconstruction](https://github.com/TBennur/GenAIFinalProject/blob/main/images/final_model_ex.pngg "Reconstruction")
