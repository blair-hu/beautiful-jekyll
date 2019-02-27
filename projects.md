---
layout: page
title: Projects
subtitle: Ongoing and completed work
published: true
---
Check out my [Google Scholar](https://scholar.google.com/citations?user=t1hINkMAAAAJ&hl=en) profile.

### **Neural rendering of prosthesis sensor data for improved generalizability of intent recognition (Ongoing)**
#### *Motivation*:
Movement-related signals detected prior to movement completion can be used to train a pattern classification algorithm to predict the upcoming locomotor activity in order to control a powered leg prosthesis (i.e. intent recognition). Intent recognition has already enabled amputees to transition intuitively and seamlessly between different pre-programmed activity modes (e.g. level ground, stairs, ramps); however, collecting labeled training data from an impaired population is very tedious. Yet, the collected training data may not even generalize well to new patterns at prediction time for both personal-predictive and population-pooled models due to factors such as differences in device configuration (alignment, socket fit), user characteristics (shoe height, height, weight, muscle strength), or environment. Therefore, new techniques to improve generalizability to these different conditions are necessary to demonstrate that intent recognition is clinically feasible and does not require an unrealistic amount of training data). In two separate but related projects, we attempt to generate realistic prosthesis sensor data that reflects variability (a) across days and users and (b) across proshetic devices.

#### *Approach*:
We selected a data-driven approach using a deep generative model (i.e. adversarial autoencoder) to learn the structure of the variability in the training data (a) aggreggated from four users across four sessions and (b) aggreggated from one user performing the same experimental protocol on two analogous prosthetic devices. First, we perform baseline data augmentation using jitter and random noise in the time-domain in order to amplify our training data from tens and hundreds to thousands of examples. Next, we train our models to simultaneously predict the activity labels and generate realistic data. Lastly, we assess the practical benefit of this approach by evaluating the prediction accuracy for models trained on varying proportions of collected and generated data and tested on collected data.

### **Open access human movement data for improving lower-limb wearable robotics**
<img style="float: center;" src="http://blair-hu.github.io/img/OpenSourceDataset1.jpg" width="500">

#### *Motivation*: 
Benchmark datasets containing high-resolution, device-agnostic neuromechanical signals from unimpaired individuals are critical to helping the wearable robotics community objectively evaluate device performance for a variety of walking-related activities. In addition, rich labeled training data from wearable sensors is valuable for developing activity prediction algorithms. Our contribution, the ENcyclopedia of Able-Bodied Lower-Limb Locomotor Signals (ENABL3S), represents a "best case scenario" (i.e. the device is fully transparent and does not impede movement) for activity prediction and is intended to fill a gap in the field by making this type of data publicly available. 
#### *Approach*:
We used wearable sensors to collect bilateral myoelectric and kinematic signals (52 channels, 1 kHz) from the lower extremities of ten healthy human subjects as they spontaneously transitioned between locomotor activities including level ground walking and ascending/descending stairs and ramps. The experimenter labeled the ground truth with a key fob. We used a temporal raster plot to highlight different patterns in the neuromechanical signals corresponding to different locomotor activities. The unstructured data were cleaned, organized, validated against results aggregated from previously published biomechanics studies, and hosted on Figshare.

[Code](https://github.com/blair-hu/OS-Data) | [Data Repository](https://doi.org/10.6084/m9.figshare.5362627) | [Paper](http://blair-hu.github.io/files/BHu_OpenSourceDataset_Frontiers2018.pdf)

### **Bilateral neuromechanical sensor fusion for intent recognition**
<img style="float: center;" src="http://blair-hu.github.io/img/BilateralIntentRecognition1.png" width="500">

#### *Motivation*:
Walking requires interlimb coordination because the leading and trailing legs have distinct biomechanical functions, especially for amputee subjects who already exhibit exaggerated gait asymmetries. However, state of the art intent recognition algorithms have not been systematically applied to bilateral control signals. We tested the hypothesis that including information from both legs would improve accuracy over a controller using unilateral information alone and assessed the practical tradeoffs of performing sensor fusion across legs and modalities.
#### *Approach*:
We used the ENABL3S dataset to systematically compare the effect of sensor fusion across legs (unilateral, contralateral, or bilateral) and modalities (myoelectric, kinematic, inertial, or all) on offline prediction accuracy. We segmented windows before critical gait events, extracted heuristic features, and used PCA for dimensionality reduction. We used k-fold cross-validation to compare different sensor configurations and investigated the effect of data dimensionality on the accuracy of three classifiers (linear discriminant, SVM, and neural network). We performed sequential forward sensor selection to determine the number and type of contralateral sensors needed to signficantly improve accuracy compared to a strictly unilateral setup. Lastly, we collected data from one amputee subject wearing an IMU sensor on his non-prosthesis side as a proof-of-concept for the generalizability and benefit of using bilateral control information in an impaired population. 

[Code](https://github.com/blair-hu/Bilateral-IR) | [Paper](http://blair-hu.github.io/files/BHu_BilateralIntentRecognition_Frontiers2018.pdf)

### **Bilateral gait segmentation using a single sensor**
<img style="float: center;" src="http://blair-hu.github.io/img/BilateralGaitSegmentation2.png" width="500">

#### *Motivation*:
Most wearable lower-limb assistive devices use finite-state machine controllers to segment gait into distinct phases with different biomchanical functions (i.e. control laws). Therefore, the ability to estimate the gait phase (e.g. stance, swing) of one or both legs in an accurate and timely manner greatly affects device safety, function, and efficiency. Specifically, robust detction of double support phase (both feet on the ground) can both help prevent the device from becoming compliant before weight transfer and synchronize power delivery. Existing techniques for bilateral gait segmentation can be cumbersome because they require sensorizing each limb. Therefore, we set out to develop a novel method for bilateral gait segmentation by applying sensor fusion to sensor data from a single thigh-mounted IMU and depth sensor.
#### *Approach*:
We developed separate processing pipelines for the IMU and depth sensor data in order to make independent offline predictions of phase (stance or swing) for each leg. For the IMU data, we extracted heuristic features from overlapping sliding windows, performed dimensionality reduction (PCA), and used linear discriminant and SVM binary classifiers to estimate stance and swing phase probabiltiies for each leg. For the depth data, we extracted two novel features (ground and contralateral shank angle) and developed a template matching algorithm to estimate the probability of each phase. Predictions were fused using a weighted average. Our promising initial findings suggest that a creative unilateral sensor fusion strategy can perform as well as a more traditional bilateral sensor configuration.

[Code](https://github.com/blair-hu/Bilateral-GS) | [Paper](http://blair-hu.github.io/files/BHu_BilateralGaitSegmentation_BioRob2018.pdf) | [Presentation](https://drive.google.com/file/d/1RjrIAizBAi3fGsOFgUEA-sWbL05sq_4f/view?usp=sharing)
