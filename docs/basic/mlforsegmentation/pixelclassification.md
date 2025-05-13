# Machine-learning for image segmentation

### The Principle behind Pixel Classification
Pixel classification is a very powerful tool for image segmentation, where pixels are assigned to different categories or classes 
based on their spatial, textural, or color properties. A pixel classifier is an algorithm that automates this process 
by analyzing the image pixels and determining their class membership. The core concept behind pixel classification 
involves the identification of patterns, similarities, and differences among pixels within an image. 
In contrast to thresholding, the algorithm does not only look at intensity, but creates additional "features" that represents structure and texture differences.

In the workflow, you will create manual annotations of your signal and background, 
select appropriate features the algorithm should take into account, 
and then train the algorithm - often a Random Forest classifier - to distinguish signal and background.
You will iteratively add annotations and then train again until the algorithm achieves a good segmentation.
Once your pixel classifier is trained, you can apply it to the rest of your data. 
![Principle of Pixel Classification](pixelclassification_1.jpg)

### Tools for Pixel Classification

- [Ilastik](https://www.ilastik.org)
- [Trainable Weka Segmentation in Fiji](https://imagej.net/plugins/tws/)
- Machine Learning Segmenter in Arivis

### Ilastik
User-friendly tool for machine learning–based segmentation, classification, and tracking without programming. 
Offers an interactive GUI to train models on pixel and object features for rapid analysis. 
[GitHub Repository](https://github.com/ilastik/ilastik)

When using Ilastik for your image analysis, please cite:

>***ilastik: interactive machine learning for (bio)image analysis*** <br>
Stuart Berg, Dominik Kutra, Thorben Kroeger, Christoph N. Straehle, Bernhard X. Kausler, Carsten Haubold, 
Martin Schiegg, Janez Ales, Thorsten Beier, Markus Rudy, Kemal Eren, Jaime I Cervantes, Buote Xu, Fynn Beuttenmueller, Adrian Wolny, Chong Zhang, Ullrich Koethe, Fred A. Hamprecht & Anna Kreshuk
in: Nature Methods, (2019)

### Selection of Features
Ilastik provides different feature types, that can be calculated in 2D or 3D. <br>

- **Color/Intensity:** <br>
		 Select these features if color or brightness can be used to distinguish objects

- **Edge:** <br>
		Select these features if brightness or color gradients can be used to distinguish objects.

- **Texture:** <br>
		 This feature may be important if the objects in the image have a unique texture.

All of these features can be selected at different scales. The scales correspond to the sigma 
value of the Gaussian filter used to smooth the image before applying the filter. Filters with 
larger sigma values can capture information from larger neighborhoods, but may also average out
 fine details. If you think a specific sigma value would be particularly well-suited to your 
 data, you can also add it to the last column, as shown in red above. The following image shows
 an example of the edge filter computed with three different sigma values. Note how the filter 
 detects the smallest edges at very low sigma values and only captures the rough cell outlines 
 at high sigma values.

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

### Training your Pixel classifier

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

### Ilastik - Pixel Classification Tutorial

For a recap of the demonstration of the Pixel Classification Workflow in ilastik, 
please visit the [Ilastik page](https://www.ilastik.org/documentation/pixelclassification/pixelclassification).

You can find the materials for the full pixel classification tutorial in your course folder.
