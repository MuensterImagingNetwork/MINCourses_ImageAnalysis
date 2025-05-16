# Hands-On: Ilastik

During our hands-on session, we will walk through the complete pixel classification workflow using Ilastik. 
Together, we’ll apply this method to tackle a challenging segmentation task where traditional thresholding fails. 
First, we’ll explore the range of **features** Ilastik offers and cover a few **practical tips for drawing effective annotations**. 
Then, we’ll proceed through the full workflow: creating training annotations, 
selecting meaningful image features, and iteratively refining the model. By the end, you’ll know how to build a pixel classifier 
that can accurately segment your images and scale across large datasets with minimal manual effort.


### Selection of Features
Ilastik offers three main feature types, each available in 2D or 3D and at multiple scales: <br>

- **Color/Intensity:** <br>
		 Use when your objects differ in brightness or hue from the background.

- **Edge:** <br>
		Detects sharp changes in intensity or color—ideal for highlighting borders and contours.

- **Texture:** <br>
		 Captures local patterns (e.g., granularity or striations) when your objects have a distinctive texture.

Each feature can be computed at various scales, defined by a Gaussian smoothing sigma.

- **Low sigma - small neighborhood:** preserves fine details, detecting tiny edges or texture.

- **High sigma - large neighborhood:** emphasizes broader structures and smooths out noise.

The following image shows an example of the edge filter computed with three different sigma values. Note how the filter 
 detects the smallest edges at very low sigma values and only captures the rough cell outlines at high sigma values.

![ImageData](feature_selection.png) <br>
*The image shows the edge feature with different sigma values.*
**© Copyright by the ilastik developers** |
[Source](https://www.ilastik.org/license)

!!! tip "Selection of **good** features"
	As a general guideline, we recommend starting by selecting a broad range of feature types 
	and scales. For smaller 2D datasets where computational resources are not a limitation, 
	you can even choose to select all options. After confirming your selections in the feature 
	selection dialog, you can review the chosen features in the bottom-left panel. 
	Usually, you can quickly see by eye if the feature "makes sense" for your data.
	If you are unsure - Ilastik can suggest features for you. Please follow the offical documentation [here](https://www.ilastik.org/documentation/pixelclassification/pixelclassification#suggest).

###  Training your Pixel Classifier 

This training process involves a repetitive cycle of human input and machine learning. 
The user starts by creating initial annotations, which are then used to generate predictive 
models. The user evaluates these predictions, identifies areas for improvement, 
and adds additional annotations to correct any mistakes, thereby refining the model's 
performance through multiple iterations.

![ImageData](training.png) <br> 
*The image is showing the iterative training process in ilastik. By evaluating the prediction, the user can add targeted annotations to improve the model.* 

!!! tip "How to draw **good** annotations"
	
	- The more features, the more annotations
	- Focus on edges and borders
	- Try to draw background and foreground annotations close to each other
	- Training time depends on number of training samples (e.g. annotated pixels)
	- Adding lot of very similar “looking” pixels will not improve the classifier
	- Include variations on your dataset into the training set (e.g. WT vs mutants, treatments)

### Step-by-Step Tutorial

Background and Goal
You have acquired 3D fluorescence images of XY stained for (green) and (blue). 
Your goal is to segment individual nuclei.

You have tried traditional segmentation approaches using "Otsu" threshold
1. Traditional Segmentation Approach
Global Thresholding

You apply Otsu’s method on the nuclear channel to separate “foreground” nuclei from “background.”

Result: Over‑merged objects in crowded regions; small nuclei are lost in noisy areas.

2D slice after thresholding (left) vs. ground truth outline (right). Note merged nuclei and missing small objects.

Take‑home: Simple thresholding cannot cope with intensity heterogeneity, uneven illumination, or variable nuclear texture. We need a more robust, pixel‑wise model.

Task: Proper segmentation using a pixel classification algorithm

Image data 


| Step                             | Description                                                                
| -------------------------------- | -------------------------------------------------------------- 
| **1. Project Setup**             | Open your image in ilastik’s “Pixel Classification” workflow.              
| **2. Feature Selection**         | You select the features that will be measured and fed into the <br> machine learning algorithm. The features will be measured <br>on the original image, as well as smoothed images. The level of <br> smoothing is determined by σ, the larger this scale, the more <br> information of the neighborhood around a pixel is taken into account.
| **3. Define Classes**            | Create two classes: **Nucleus** and **Background**.                        
| **4. Annotate Training Regions** | Brush representative regions for each class across different tissue <br>  areas. Annotate at least 5 regions each for nucleus and background. 
| **5. Train Classifier**          | Click **“Live Update”** to see probability map.                            
| **6. Refine Annotations**        | Add or remove brush strokes where misclassifications occur.                
| **7. Export Segmentation**       | Threshold the nucleus probability channel and apply watershed.
| **8. Batch Application**         |  Apply your model to your dataset. Load more images and apply your <br> pixel classifier batch-wise.               

!!! tip "Congratulations"
	You have trained your own pixel classifier that outperforms thresholding!


           



For a detailed recap of the demonstration of the Pixel Classification Workflow in ilastik, 
please visit the [Ilastik page](https://www.ilastik.org/documentation/pixelclassification/pixelclassification).



!!! warning "Citation"
	When using Ilastik for your image analysis, please cite:
	>***ilastik: interactive machine learning for (bio)image analysis*** <br>
	Stuart Berg, Dominik Kutra, Thorben Kroeger, Christoph N. Straehle, Bernhard X. Kausler, Carsten Haubold, 
	Martin Schiegg, Janez Ales, Thorsten Beier, Markus Rudy, Kemal Eren, Jaime I Cervantes, Buote Xu, Fynn Beuttenmueller, Adrian Wolny, Chong Zhang, Ullrich Koethe, Fred A. Hamprecht & Anna Kreshuk
	in: Nature Methods, (2019) 
	<br> DOI: [10.1038/s41592-019-0582-9](10.1038/s41592-019-0582-9)
