# Automatic Segmentation of Primary Brain Lymphoma on Clinical Routine Post-contrast T1-weighted MRI


This repository contains material associated to this [paper](#Citation).

It contains:
- link to trained models for segmentation of lymphoma from post-constrast T1-weighted MRI ([link](#Trained-nnU-net-models))

If you use this material, we would appreciate if you could cite the following reference.

## Citation
* Guanghui Fu, Lucia Nichelli, et al. Automatic Segmentation of Primary Brain Lymphoma on Clinical Routine Post-contrast T1-weighted MRI. Preprint, https://hal.science/hal-. 
  
## Trained nnU-net models
### Lymphoma segmentation in post-contrast T1-weighted MRI 
* [`preprocess/lymphoma_preprocess.py`](<https://github.com/GuanghuiFU/medical_cv_foundation_eval/blob/main/preprocess/lymphoma_preprocess.py>):
  * Resample to (1,1,1)
  * Rescale intensity
  * CropOrPad, or Resize to (240, 240, 160)
  * Note that, all these operations are performed through [TorchIO](<https://torchio.readthedocs.io/index.html>) operations
* **Trained model link**: https://owncloud.icm-institute.org/index.php/s/4nERKuJb4xASV81

## Code to train nnU-net

Training nnU-Net only requires the following commands. `DATASET_ID` and `FOLD` are defined in the same way as [nnU-net official codes](<https://github.com/MIC-DKFZ/nnUNet>). See the [official code](<https://github.com/MIC-DKFZ/nnUNet>) for details.

## Inference for nnU-Net

Inferencing nnU-Net only requires the following commands. `DATASET_ID`, `INPUT_FOLDER` and `OUTPUT_FOLDER` are defined in the same way as [nnU-net official codes](<https://github.com/MIC-DKFZ/nnUNet>). See the [official code](<https://github.com/MIC-DKFZ/nnUNet>) for details.

* **3D inference**: 
```console
nnUNetv2_predict -d DATASET_ID -i INPUT_FOLDER -o OUTPUT_FOLDER -f  0 1 2 3 4 -tr nnUNetTrainer -c 3d_fullres -p nnUNetPlans
```

```
## Computation of metrics and statistical analysis

* [`evaluation/eval_bootstrap_ci.py`](<https://github.com/GuanghuiFU/nnunet_lymphoma_segment/blob/main/evaluation/eval_boostrap_ci.py>): This code is for evaluation and calculate the 95% bootstrap confidence interval.
* [`evaluation/t_test.py`](<https://github.com/GuanghuiFU/nnunet_lymphoma_segment/blob/main/evaluation/t_test.py>): This code is to perform paired T-test.


## Related codes

1. **nnU-Net** [1]: https://github.com/MIC-DKFZ/nnUNet
2. **TorchIO** [2]: https://torchio.readthedocs.io/index.html

## References

1. Fabian Isensee, Paul F Jaeger, Simon AA Kohl, Jens Petersen, and Klaus H Maier-Hein. nnU-Net: a self-configuring method for deep learning-based biomedical image segmentation. Nature methods, 18(2):203–211, 2021.
2. Pérez-García, Fernando, Rachel Sparks, and Sébastien Ourselin. "TorchIO: a Python library for efficient loading, preprocessing, augmentation and patch-based sampling of medical images in deep learning." Computer Methods and Programs in Biomedicine 208 (2021): 106236.
