# Zoom Super Resolution

  The aim of this project is to enhance the resolution of zoomed area in a image. Inspired by the article entitled "Learning Deep CNN Denoiser Prior for Image Restoration" by Kai Zhang, I have used a CNN (convolutionnal neural network) with a similar structure.  
The dataset is composed of 900 images from the DIV2K dataset, split into 800 images for the train set and 100 for the test set.

<p align="center">
  <img src = "images/div2K_exemple.jpg" width = "500">
</p>

## Comparison method of the digital zoom improvements 

Upscale by a factor 2 an under-determined 256x256 scene and improve the output resolution of the same scene to a 512x512 image through a 5-layer CNN.

Description step-by-step process of resolution augmentation :  
(a) in a super resolved image, a 512x512 snapshot will be consiedered as the ground truth  
(b) in a under resolved image, a 256x256 snapshot of the same area is the image that will be improved  
(c) result of a SRCNN improvement  
(d) result of a VDSR improvement   
(e) result of the CNN improvement in the article  


<p align="center">
  <img src = "images/presentation_projet.PNG" width = "750" >
</p>


##  Unet structure of the CNN 

<p align="center">
<img src = "images/Unet.PNG" width = "750">
</p>

The used CNN is composed of 5 layers, 4 for convolution and downsizing and the final one to upscale the image.

## Reconstruction throughout the epochs

<p align="center">
<img src = "images/epoque.PNG" width = "750">
</p>

The training of the CNN leads to the best results at around 10 epochs. Follow up of the training has been studied but leads to similar results, with a risk of overfitting. Therefore 10 epochs is the choice I made to compare resolution improvement as output of the CNN. 

## Performances on train set and test set 

<p align="center">
<img src = "images/erreur_courbe.PNG" width = "750">
</p>

These curves describe the absolute mean error for the value of a given pixel, through the epochs.  

## Good Results 

<p align="center">
<img src = "images/exemple_1.PNG" width = "750">
</p>

The ouput of the CNN leads to a significant improvement in the details when it comes to texture; The skin of this strawberry for example is smoother but not blurred.   

## Difficulties 

<p align="center">
<img src = "images/difficultes.PNG" width = "750">
</p>

However the CNN seems to struggle with high spatial frequency. The Eiffel Tower iron patterns are not discriminated enoguh, and the writing on the german Parlement are also blurred. the CNN did keep these details, but it has a tendancy to not give enough weight, leading to a blurring of the area rather an improvement of the resolution. 
